# Componentes y convenciones de UI (genérico)

## Capas

| Capa | Contenido | Regla |
| --- | --- | --- |
| Primitivas | Botón, card, input, select, dialog, table, tabs, tooltip | Accesibles; se adaptan, no se envuelven sin motivo |
| Compartidos | Producto reutilizable (page header, KPI, badges, empty/error/skeleton) | Usados por varias features |
| Dominio | Componentes locales del módulo | No ascienden hasta reutilizarse de verdad |

## Inventario mínimo

- **Page header:** un `<h1>`, descripción, meta y acciones.
- **Card / section:** título, descripción y acción opcional.
- **KPI card:** etiqueta, valor tabular, delta contextual, `href` opcional.
- **Badges:** estado, prioridad, severidad; icono + texto + color.
- **Progress:** `role="progressbar"` y valor accesible.
- **Estados:** empty, error, skeleton; empty inicial distinto de sin resultados.
- **Filtros:** select accesible con label y opción “Todos”.
- **User/avatar:** nombre e imagen o inicial.

## Convenciones

- Usa el helper de clases del proyecto (`cn` o equivalente) y variantes
  (`cva` o equivalente). Nunca concatenes strings.
- Todo componente acepta `className` y lo aplica al contenedor raíz.
- Conserva los atributos de la primitiva (foco, disabled, `data-slot`).
- Iconos de una sola familia, grosor y tamaño; `aria-hidden` si son decorativos.
- Cada interactivo implementa default, hover, focus, active, disabled, loading
  y error.
- Overlays escapan su contenedor: un dropdown absoluto dentro de
  `overflow: hidden/auto` se recorta. Usa portal, `position: fixed` o `dialog`.
- La misma acción tiene el mismo nombre, icono y forma en toda la app.

## Shell y navegación

- Elige la navegación después de entender la arquitectura de información, las tareas frecuentes y los dispositivos. Usa navegación lateral, superior, rail o contextual según el producto; no asumas sidebar como plantilla.
- Si el shell ya tiene una forma propia, consérvala y úsala como patrón del producto. Si aún no hay marca, refleja la tesis visual en el símbolo y en la organización del shell; no resuelvas identidad solo cambiando el color o poniendo una inicial en un recuadro.
- Mantén visible y coherente la ubicación activa, los grupos y la relación entre navegación y contenido. Coloca perfil, apariencia y configuración donde el modelo de uso los haga fáciles de encontrar; no añadas controles de muestra.
- En móvil, transforma la navegación para la tarea táctil sin reducirla a una versión comprimida del escritorio.
- En grupos laterales expandibles, distingue el padre abierto con una superficie redondeada y sus hijos con sangría y una guía sutil. Marca cada submódulo con un punto: usa el acento ya definido por la interfaz para el activo y un tono de la misma paleta para los demás; no inventes un nuevo color para el punto. Combina el indicador con texto distinguible y `aria-current`, nunca dependas solo del color. Adapta o descarta el patrón si la identidad o el espacio del producto no lo justifican.
## Tarjetas y superficies

- Radio y borde desde tokens.
- Elige **borde sutil O sombra**, nunca ambos. Por defecto borde sin sombra; la
  sombra se reserva a elevación real u hover.
- Sin tarjetas anidadas.
- La tarjeta no es la estructura por defecto de la página: agrupa información
  relacionada, no envuelve cada bloque.

## Estados

- **Vacío inicial:** explica qué aparecerá y cómo crear el primer registro.
- **Sin resultados de filtro:** distinto del vacío; ofrece limpiar filtros.
- **Error:** qué falló y cómo reintentar; no culpes al usuario.
- **Carga:** skeleton con la forma del contenido y `aria-busy`.
- **Sin permiso:** explica el motivo y la vía de acceso.
- **Éxito:** confirma con la acción nombrada, no con un “OK” genérico.

## Al crear un componente

1. Confirma que no existe una primitiva o patrón reutilizable.
2. Props tipadas, `className` opcional, sin `any`.
3. Tokens y variantes; iconos del sistema.
4. Estados y accesibilidad completos.
5. Test de comportamiento si tiene lógica o interacción no trivial.
6. Si es patrón nuevo, actualiza el design system del proyecto.
