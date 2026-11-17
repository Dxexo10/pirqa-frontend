# Patrones de pantalla (genérico)

Adapta nombres y componentes a los del proyecto. Usa su módulo gold standard
como referencia implementada.

## 1. Lista / tabla

- **Encabezado fijo** al hacer scroll dentro de la tabla, con fondo de superficie
  y borde inferior.
- **Orden:** control explícito, campo y dirección visibles; ordenar vuelve a la
  página 1.
- **Paginación:** `pageSize` nunca supera el techo del repositorio
  (`MAX_PAGE_SIZE` del proyecto). Virtualiza solo si una vista recibe más filas
  materializadas que el umbral acordado (por ejemplo > 100), lo que exige
  cambiar el contrato. No mezcles ambas estrategias sin justificarlo.
- **Selección múltiple:** checkbox por fila y de cabecera con estado
  indeterminado (`aria-checked="mixed"`). Barra de acciones con el conteo; se
  limpia al cambiar filtros o página.
- **Densidad:** una sola por pantalla (cómoda por defecto; compacta para
  consulta).
- **Columnas ocultables:** solo si hay muchas columnas o el usuario lo pide;
  incluye “Restablecer columnas”.
- **Scroll horizontal controlado:** contenedor propio con `overflow-x-auto`;
  nunca en el `body`. Congela la primera columna solo si identifica la fila.
- **Vacío vs. sin resultados:** sin datos = crear el primero; con filtros = no
  encontramos + limpiar filtros.
- **Móvil:** lista de tarjetas, no scroll horizontal de la tabla.
- Pie con contador, rango visible y tamaño de página.

## 2. Filtros

- Viven en la **URL** (`useSearchParams` o router equivalente); nunca en estado
  local si el enlace debe compartirse. Serializa solo valores no-default.
- Al cambiar un filtro, vuelve a `page: 1` y usa `replace`.
- **Chips de filtros activos** con “Quitar filtro X” y `aria-label`. Siempre
  “Limpiar todo”, deshabilitado si no hay filtros.
- **Búsqueda con debounce** (300 ms salvo convención del proyecto): actualiza la
  URL después del silencio, no en cada tecla; limpiar es inmediato.
- **Móvil:** filtros avanzados en sheet/drawer con “Limpiar” y “Ver resultados”.
- Si un filtro depende de una regla de dominio, aplícalo en el hook/servicio,
  no en la tabla.
- No inventes filtros que el contrato no soporta; documenta el límite.

## 3. Detalle

- Cabecera con identidad, estado, acciones primarias y secundarias. La acción
  destructiva va separada y con estilo `danger`.
- **Tabs** para dimensiones del mismo registro; el tab activo vive en la URL.
- **Página vs. drawer:**
  - Página: entidad con URL propia, contenido profundo, tabs, edición o
    historial.
  - Drawer/sheet: vista rápida o tarea lateral breve desde la lista, sin
    navegación propia; ofrece “Abrir página” para profundizar.
  - Modal: solo interrupción necesaria o confirmación protegida.
- Cada dato sale del repositorio; no recalcules totales en el JSX.

## 4. Formulario

Stack: React Hook Form + Zod o equivalente.

- **Validación:** `mode: 'onBlur'` y `reValidateMode: 'onChange'`. Valida al
  salir del campo y al enviar; `reValidateMode` aplica después del primer envío.
- **Errores por campo:** `aria-invalid` y `aria-describedby` al id del mensaje.
  Sin `role="alert"` por campo.
- **Resumen de errores:** `role="alert"` único al enviar, con enlaces a cada
  campo; enfoca el resumen o el primer campo inválido.
- **Mensajes** en el idioma del producto, accionables y centralizados. No
  muestres mensajes crudos de la librería.
- **Reglas cruzadas** con `superRefine` o equivalente.
- **Cambios sin guardar:** `isDirty` + `beforeunload` y confirmación al cancelar.
- **Submit:** una sola acción primaria, con estado de carga y `disabled`.
- **Errores del servidor:** mapéalos a campos cuando haya detalle; errores
  generales con la acción nombrada. Nunca pierdas lo escrito.
- **Permisos:** si no puede editar, no renderices el formulario; explica la vía.

## 5. Formulario nativo sin librería

Usa este mínimo cuando el proyecto no incluya una librería de formularios:

- Label visible asociado a cada control; aprovecha `required`, `type`, `min`, `max`, `pattern` nativos cuando correspondan.
- Al detectar error, establece `aria-invalid="true"` y conecta el mensaje mediante `aria-describedby`; quita `aria-invalid` al corregir.
- Al enviar, valida los campos y muestra un único resumen accesible con enlaces a los campos inválidos; enfoca el resumen o el primer campo inválido.
- No asignes `role="alert"` a cada error de campo; resérvalo para el resumen de envío.
- Conserva los valores, anuncia la recuperación y no dependas solo del color.

## 6. Dashboard

- Un KPI destacado como ancla visual; el resto en tarjetas del sistema.
- Máximo 4 KPIs por fila.
- Una sola fuente por cifra; no recalcules en tarjeta, tabla y gráfico.
- Periodo explícito y fecha de corte visible.
- Estado vacío cuando no hay datos para el filtro.
- Gráficos con carga diferida y skeleton de la altura final.

## 7. Exportación y reportes

- **Misma función de derivación** que la pantalla: un `ReportDocument` puro
  alimenta resumen, vista previa, CSV, XLSX y PDF.
- Formato local para dinero, porcentaje y fechas.
- Nombre de archivo `<producto>-<módulo>-<fecha de referencia>`.
- CSV con BOM UTF-8 y escapado RFC 4180; XLSX con celdas numéricas reales.
- PDF con `window.print()` y utilidades `print:hidden`; declara que depende del
  diálogo del navegador.
- Botón con estado de exportación y error con reintento. No descargues vacío.
- Metadatos: título, etiqueta de entorno, fecha de corte, generación y filtros.
