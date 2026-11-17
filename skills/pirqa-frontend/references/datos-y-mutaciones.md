# Datos, consultas, mutaciones y permisos (genérico)

## Capas

```text
features/<módulo>/hooks/  orquestación de datos
data/contracts/           interfaces de repositorio
data/mock/                adaptadores locales
data/http/                adaptadores REST
data/index.ts             ÚNICO punto de composición
domain/services/          reglas puras y agregaciones
```

- Ninguna vista importa adaptadores concretos ni toca red/almacenamiento.
- El punto de composición elige mock o HTTP por entorno.
- La lógica de negocio vive en funciones puras y se prueba sin UI.
- Dinero en la unidad mínima entera; fechas ISO; IDs estables.

## QueryKeys

Convención jerárquica por módulo:

```ts
['<module>', 'list', filters]
['<module>', 'detail', id]
['<module>', 'stats', params]
```

- Primer segmento: módulo; segundo: tipo; después, parámetros serializables.
- Un cambio de filtros produce una key nueva; no mutes la anterior.
- Invalida por raíz del módulo y también los agregados que dependan de él
  (dashboard, alertas, monitoreo).
- No uses índices de array como parte de la key.

## staleTime

Valores de referencia; adáptalos al producto:

| Dato | staleTime |
| --- | --- |
| Listas y detalles | 30 s |
| Agregados de dashboard/reportes | 60 s |
| Catálogos casi estáticos | 5 min |
| Datos deterministas de demo | puede ser mayor, pero invalida tras mutar |

Sin `staleTime: Infinity` salvo dato verdaderamente inmutable. Usa
`keepPreviousData` para paginación y filtros.

## Mutaciones

```ts
const mutation = useMutation({
  mutationFn: (input) => repository.update(id, input),
  onMutate: async (input) => {
    await queryClient.cancelQueries({ queryKey: ['<module>', 'detail', id] })
    const previous = queryClient.getQueryData(['<module>', 'detail', id])
    queryClient.setQueryData(['<module>', 'detail', id], optimistic(input))
    return { previous }
  },
  onError: (_error, _input, context) => {
    if (context?.previous) {
      queryClient.setQueryData(['<module>', 'detail', id], context.previous)
    }
    toast.error('No pudimos guardar los cambios.')
  },
  onSettled: () => {
    void queryClient.invalidateQueries({ queryKey: ['<module>'] })
  },
  onSuccess: () => toast.success('Registro actualizado.'),
})
```

- **Optimistic** solo para acciones rápidas y reversibles (toggle, estado,
  reordenar). Guarda snapshot, rollback en `onError`, invalida en `onSettled`.
- Acciones con efectos de negocio (crear versión, generar alertas, archivar) no
  son optimistas: espera la respuesta y muestra el resultado real.
- **Toast en el idioma del producto con la acción nombrada** y el identificador
  útil. Un solo toast por mutación.
- Bloquea el control mientras `isPending`; conserva el formulario si falla.

## Errores

| Tipo | Qué muestra | Recuperación |
| --- | --- | --- |
| Red / offline | Estado o banner “Sin conexión” | Reintentar; conservar datos |
| Validación (422) | Errores por campo + resumen | Corregir y reenviar |
| Conflicto (409) | “El registro cambió” con detalle | Recargar y comparar |
| Permisos (403) | Estado sin permiso con motivo | Solicitar acceso o volver |
| No encontrado (404) | Página/estado no encontrado | Volver al listado |
| Servidor (500) | Error honesto con reintento | Reintentar; no datos falsos |

Nunca muestres stack, mensajes en inglés ni `[object Object]`. Los detalles
técnicos solo en desarrollo.

## Acciones destructivas

- **Reversible:** ejecuta + toast con **“Deshacer”** (≈8 s). Nombra el objeto.
- **Irreversible o con efectos amplios:** `AlertDialog` con título en pregunta,
  impacto y botón `danger` con el verbo exacto.
- No uses `window.confirm` salvo el guard de cambios sin guardar; migra a un
  diálogo accesible.

## Permisos y roles

- Una **única función de dominio** decide: `can(user, action, resource)`.
  Ninguna vista compara strings de rol.
- Tres niveles:
  1. **Ocultar** lo que el rol nunca puede usar.
  2. **Deshabilitar con motivo** cuando falta contexto.
  3. **Estado 403** al acceder por URL directa.
- Evalúa con usuario y recurso, no con el nombre del módulo.
- Si aún no existe autenticación, no inventes permisos: define la función única
  cuando se implemente y usa un actor explícito hasta entonces.

## Rendimiento de datos

- Evita waterfalls: `Promise.all` para consultas independientes.
- Pagina en el repositorio; `pageSize` ≤ `MAX_PAGE_SIZE` del proyecto.
- Selecciona del cache con selectores estables; memoiza solo con medición.
- No dupliques datos derivados en el cache: deriva con una función pura.
