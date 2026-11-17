---
name: pirqa-frontend
description: Actívala cuando construyas, refines o audites un módulo completo —lista, detalle, formulario, dashboard, gráficos o exportación— con datos, estados y tests. No la actives para cambios triviales de un solo componente, estilos sueltos o scripts.
metadata:
  version: 1.2.0
---

# Frontend Modules — playbook reutilizable

Actúa como **director de diseño y staff engineer** del producto en el que estás
trabajando. Cada módulo debe ser claro, coherente, accesible, rápido y completo.
No entregues pantallas a medias ni deuda visual silenciosa.

1. **El brief, el producto y su marca mandan** sobre tu gusto y sobre los
   defaults de categoría.
   La paleta existente o solicitada por el usuario manda; no añadas acentos
   de otra familia por gusto.
2. **Verifica mirando el render** en los tamaños reales; un test no sustituye el juicio.
3. **Termina**: si un estado, breakpoint, tema o caso límite está en alcance, se entrega.

Esta skill es **genérica y reutilizable**. No asume colores, tipografías, rutas
ni nombres de marca. El contrato concreto del proyecto se lee de su
documentación y tokens, y puede reforzarse con una skill de proyecto (por
ejemplo, un adaptador de marca) que tenga precedencia sobre esta.

## Alcance y stack

Optimizada para **React + TypeScript** con TanStack Query, React Hook Form +
Zod, Tailwind/cva y Playwright. Los nombres de herramientas y comandos son
ejemplos; adáptalos al proyecto.

- **Universal:** accesibilidad, tokens, copy, patrones de pantalla (conceptos),
  craft floor, estados y responsive.
- **Dependiente del stack:** capa de datos, convenciones del framework y
  herramientas de testing.

Para **Vue, Svelte o HTML/CSS/JS**: conserva los conceptos —contratos y
repositorios, estado de servidor, validación de formularios, filtros en URL,
estados y tokens— y sustituye las herramientas: Pinia/TanStack Vue Query,
vee-validate/Zod, stores de Svelte/SvelteKit, `fetch` + estado local o
formularios HTML. No cambies las reglas de accesibilidad, copy ni craft.

## 1. Cómo usar esta skill

| Referencia | Léela cuando… |
| --- | --- |
| [`references/tokens.md`](references/tokens.md) | definas color, tipografía, temas, contraste o radios |
| [`references/direccion-visual.md`](references/direccion-visual.md) | definas o completes la identidad visual cuando falte o esté incompleta |
| [`references/componentes.md`](references/componentes.md) | definas shell, navegación, componentes, estados o primitivas |
| [`references/patrones-de-pantalla.md`](references/patrones-de-pantalla.md) | construyas lista, filtros, detalle, formulario, dashboard o exportación |
| [`references/datos-y-mutaciones.md`](references/datos-y-mutaciones.md) | definas contratos, hooks, queryKeys, mutaciones, errores o permisos |
| [`references/accesibilidad.md`](references/accesibilidad.md) | revises foco, teclado, ARIA, contraste, touch o motion |
| [`references/testing.md`](references/testing.md) | escribas tests, axe, capturas o presupuestos de rendimiento |
| [`references/graficos.md`](references/graficos.md) | agregues o modifiques un gráfico |
| [`references/convenciones.md`](references/convenciones.md) | escribas TypeScript/React, formatos de dominio o labels |
| [`references/copy.md`](references/copy.md) | escribas textos de interfaz, errores o estados |
| [`references/ejemplo-modulo-minimo.md`](references/ejemplo-modulo-minimo.md) | necesites un módulo mínimo completo como punto de partida |

**Presets visuales opcionales** en `presets/`: `warm-editorial`, `suave-pastel-sobrio` y `frio-de-trabajo`. Elige solo el que encaje con el dominio y el brief; ninguno es default. Si el proyecto ya tiene identidad, mandan sus tokens.

**Dependencias externas (todas opcionales):**

| Dependencia | Si existe | Fallback |
| --- | --- | --- |
| `impeccable` | Úsala para `critique`, `audit`, `polish`, `adapt`, `animate`, `typeset`, `clarify` y `harden`. | Aplica el craft floor y una autocrítica con el triaje P0–P3. |
| `frontend-design` | Úsala para explorar un mundo visual. | Deriva la dirección del brief y los tokens; no inventes una marca nueva. |
| `trazo-brand` | Aporta tokens, rutas y labels de [Trazo](https://github.com/Dxexo10/trazo). | Lee `PRODUCT.md`/`DESIGN.md`/tokens y detecta el gold standard del repo. |
| Skill de proyecto | Aporta el contrato de marca y arquitectura. | Usa la documentación y el código existentes como contrato. |

Pásales el contexto del proyecto. Si contradicen una regla explícita del
proyecto, gana el proyecto.

## 2. Contexto del proyecto (obligatorio antes de diseñar)

Antes de escribir código, descubre y respeta:

- `PRODUCT.md`, `README.md` o equivalente: qué es el producto, quién lo usa,
  cuál es la tarea y el modo dominante (Persuade, Operate, Read, Experience).
- `DESIGN.md`, `docs/DESIGN_SYSTEM.md` o equivalente: sistema visual, tokens,
  componentes y decisiones.
- Tokens reales (`tokens.css`, theme, Tailwind config, variables CSS): colores,
  tipografía, espaciado, radios, sombras y temas.
- El **módulo de referencia (gold standard)** del repo: el más completo en lista,
  detalle, formularios, datos, tests y accesibilidad. Copia su estructura; no
  inventes una paralela.
- Contratos de datos y convenciones de estado (URL, store, query client).
- Comandos reales de lint, typecheck, tests y build (`package.json` o equivalente).

Si falta contexto, inspecciona el código y el historial; no inventes cifras ni versiones. Si no hay marca, tokens ni sistema visual, trata el trabajo como Build y presenta primero la dirección de [`references/direccion-visual.md`](references/direccion-visual.md). Refine solo aplica si el proyecto ya tiene identidad visual.

## 3. Protocolo de trabajo

| Tipo | Señales | Comportamiento |
| --- | --- | --- |
| **Build** | módulo nuevo, feature, CRUD, pantalla | Explora, planea, implementa completo, verifica |
| **Refine** | "pulir", "arreglar", "se ve raro" sobre una identidad existente | Preserva identidad; corrige en el nivel más estrecho |
| **Evaluate** | "revisa", "audita", "critica" | Diagnostica y prioriza; no edites |
| **Adapt** | responsive, tema, densidad, i18n | Cambio estructural, no tipografía fluida |

Antes de editar: lee los archivos que tocarás, revisa el patrón vecino y busca
un componente/token/hook reutilizable. Para trabajo visual, mira la pantalla
actual. Si no puedes ejecutarla, dilo.

Mientras construyes: un cambio, una verificación; agrupa las comprobaciones en
una sola mirada al render; aplica el checklist sin narrarlo. Si el concepto está
mal, dilo y propone rediseño en vez de disfrazarlo de polish.

Antes de construir UI, define una identidad visual ligada al producto y a la tarea.
Usa los patrones existentes si tienen carácter; no los reemplaces por una plantilla.
Si no hay sistema visual, presenta primero la dirección de
[`references/direccion-visual.md`](references/direccion-visual.md). Comprueba que la
composición y la navegación expresen la identidad más allá del logo y el color.

Antes de cerrar: lint, typecheck, tests y build; recorre la ruta con teclado y tamaños representativos; entrega un diff limpio; declara lo que no verificaste.
Si no puedes abrir el navegador, entrega una checklist manual de cinco pasos: Tab y foco; viewport de 320 px; tema soportado; estados vacío/sin resultados/error; comparación con la base.

### Refine y Evaluate

**Refine** preserva identidad, contenido y comportamiento. Clasifica cada
desviación antes de corregirla: **token faltante**, **implementación puntual**
(usar el componente compartido), **desajuste conceptual** (flujo, jerarquía o
información) o **defecto local**. Corrige la causa en el nivel más estrecho.

**Triaje P0–P3:** P0 tareas rotas, pérdida de datos, estado engañoso o ruta
inaccesible; P1 falta de estados o violación WCAG AA; P2 flujo, jerarquía,
responsive o deriva del sistema; P3 inconsistencia visual o de motion.

**Formato de hallazgo:** `[P?] Nombre · ubicación (archivo/línea) · impacto ·
estándar violado · recomendación`. En Evaluate no edites: diagnostica, prioriza
y evita falsos positivos sin verificar. No perfecciones una esquina mientras el
resto queda por debajo del mismo estándar.

## Modo ligero

Elige el modo por alcance: usa el modo ligero si el encargo cubre una sola pantalla sin backend ni persistencia. El modo completo es el default en los demás casos.

- **Omite:** contratos y repositorios, hooks de datos (usa fixtures o estado local), capa de dominio separada y E2E (opcional).
- **Conserva:** tokens, estados de carga/vacío/error, accesibilidad básica, responsive, copy y los bans.
- Mantén el alcance en un archivo o feature pequeño; sin over-engineering.

**Definition of Done reducida:**

- [ ] Tarea primaria completada.
- [ ] Estados de carga, vacío, error y sin resultados.
- [ ] Responsive 320/375/768 y teclado/foco.
- [ ] Revisión de bans universales completada.
- [ ] Contraste AA medido con script para texto/fondo; tokens usados.
- [ ] Checklist manual de teclado: Tab, orden, foco visible y salida de overlays.
- [ ] Copy claro y consistente.
- [ ] Lint/typecheck/build pasan (si aplica).
## 4. Module Blueprint

Checklist ordenado para crear un módulo. Adapta nombres y rutas a las
convenciones del repo; copia la estructura de su módulo gold standard.

1. **Mini-brief.** Completa y confirma esta plantilla:

   ```text
   - Usuario:
   - Tarea primaria:
   - Modo dominante: Persuade | Operate | Read | Experience
   - Datos y fuente:
   - Permisos:
   - Estados críticos:
   - Restricciones de marca:
   - Dispositivos:
   ```

   Si faltan usuario, tarea o datos, pregunta; no los inventes.
2. **Contrato y datos.** Interfaz de repositorio en la capa de contratos del
   proyecto, adaptador mock/HTTP y **un único punto de composición**. Las vistas
   no tocan red ni almacenamiento directo.
3. **Dominio.** Reglas y agregaciones en funciones puras, con tests unitarios.
   Sin React ni acceso a red.
4. **Hooks de datos.** Consultas y mutaciones con queryKeys jerárquicas
   (`['<módulo>', 'list'|'detail'|'stats', params]`) y la librería de datos del
   proyecto (TanStack Query, SWR, stores equivalentes).
5. **Etiquetas.** Todo texto visible de dominio en el archivo de labels del
   proyecto. Nada hardcodeado en componentes.
6. **Rutas y navegación.** Página con carga diferida, ruta real y entrada de
   navegación. Sin entradas deshabilitadas ni pantallas ficticias.
7. **Estados.** Carga (skeleton), vacío, error con reintento, sin permiso y
   éxito. Sin spinner en medio del contenido.
8. **Tests.** Dominio (unit), componente/página (RTL o equivalente), flujo
   crítico (E2E/Playwright), axe en la ruta principal y capturas en los anchos
   y temas soportados.
9. **Documentación.** Actualiza el design system si creaste un patrón y el
   registro de decisiones si tomaste una decisión técnica.

## 5. Arquitectura y datos

Adopta las capas del repo. Si no existen, esta es la separación sana:

```text
features/**   pantallas, componentes de dominio, hooks
components/** ui (primitivas), shared, charts
domain/**     modelos, reglas puras y agregaciones
data/**       contratos + adaptadores mock/HTTP
lib/**        configuración, labels, formato, utilidades UI
app/**        router, providers, layout, entrypoints
```

- Un único punto de composición de datos; ninguna vista importa adaptadores
  concretos.
- Una sola fuente por cifra: KPIs, tablas, gráficos y exportaciones derivan del
  mismo estado/función pura.
- Dinero en la unidad mínima entera (céntimos) y formato local del proyecto.
- Fechas con utilidades del proyecto y una fecha de referencia explícita.
- Filtros compartibles en la URL; preferencias cosméticas en storage con
  fallback en memoria.

Detalle en [`references/datos-y-mutaciones.md`](references/datos-y-mutaciones.md).

## 6. Patrones de pantalla

Reglas y componentes por patrón en
[`references/patrones-de-pantalla.md`](references/patrones-de-pantalla.md).

Los valores concretos (debounce, `staleTime`, tamaño de página, umbral de
virtualización, INP) son **defaults de referencia ajustables** al proyecto; no
los trates como reglas si el repo define otros.

Resumen no negociable:

- **Lista/tabla:** encabezado fijo, orden, paginación con el techo del
  repositorio, scroll horizontal controlado, densidad y columnas ocultables.
  Distingue "sin datos" de "sin resultados de filtro".
- **Filtros:** viven en la URL; chips removibles; "Limpiar todo"; búsqueda con
  debounce (300 ms salvo convención del proyecto).
- **Detalle:** cabecera con acciones, tabs; drawer solo para tareas laterales
  breves, página cuando hay URL propia o contenido profundo.
- **Formulario:** React Hook Form + Zod o equivalente; validación al salir del
  campo y al enviar; resumen de errores accesible; mensajes en el idioma del
  producto desde labels; protección de cambios sin guardar; submit con estado de
  carga; errores del servidor mapeados a campos.
- **Dashboard:** un KPI destacado y máximo 4 por fila; una sola fuente por cifra.
- **Exportación:** misma derivación que la pantalla, formato local, nombre
  `<módulo>-<fecha de referencia>`, estado de carga y error.

## 7. Sistema visual

El tema predeterminado es **claro**. Implementa tema oscuro solo si lo pide el
brief o el usuario; si se pide, derívalo de los mismos tokens semánticos y
verifica su contraste por separado. Si el proyecto no tiene identidad visual,
usa primero `references/direccion-visual.md`.

- **Tokens semánticos, no valores sueltos.** Color, radio, sombra y tipografía
  salen del sistema del proyecto. Prohibido hex/px nuevos donde existe token.
- Tipografía: respeta la pareja y la escala del proyecto; cifras con
  `tabular-nums`. Sin `clamp` en UI de producto.
- Radios y sombras: usa la escala del proyecto; elevación una sola vez (borde
  **o** sombra, nunca ambos como “ghost card”).
- Estados: color + icono + texto. El color de marca no representa estados.
- Tema claro/oscuro comparten tokens; no dupliques paletas dentro de la vista.
- Contraste AA: mide cada pareja texto/fondo en default, hover, foco, activo, seleccionado y disabled; conserva 4.5:1 en texto normal y 3:1 en texto grande.
- Movimiento: 150–250 ms, comunica estado, un solo momento autoral.
- Superficies del navegador: selección, caret, scrollbars, focus ring,
  `underline-offset`, autofill y `color-scheme` desde la paleta.

## 8. Accesibilidad y responsive

Checklist completo en [`references/accesibilidad.md`](references/accesibilidad.md).

- WCAG 2.2 AA; foco visible; teclado; `aria-current`; skip-link.
- Touch target: 24×24 CSS px mínimo AA; 44×44 px en acciones primarias y flujos
  móviles.
- `prefers-reduced-motion`: equivalente sin movimiento, no solo `0.01ms`.
- Responsive estructural: 320, 375, 768, 1280, 1600 px; sin scroll horizontal
  fuera de tablas/gráficos. Reflow AA 1.4.10 a 320 px.
- WCAG 2.2 adicional: 2.4.11 (foco no oculto por topbar/header sticky;
  `scroll-padding-top`), 2.5.7 (alternativa a arrastre).

## 9. Componentes, gráficos y exportación

Capas, inventario y props en [`references/componentes.md`](references/componentes.md).

- Primitivas accesibles primero; componentes de producto después; dominio
  local por último.
- `cn`/`cva` o el helper del proyecto; nunca concatenes clases.
- Cada interactivo implementa default, hover, focus, active, disabled, loading
  y error.
- Overlays escapan contenedores con `overflow` (portal/`fixed`/`dialog`).
- Iconos de una sola familia, grosor y tamaño; `aria-hidden` si son decorativos.

Gráficos en [`references/graficos.md`](references/graficos.md): máximo 4 series
+ "Otros", tokens de chart del proyecto, distinción no solo por color, ejes con
unidad, tooltip accesible, resumen `sr-only`, tabla alternativa, estado vacío,
carga diferida y mismo origen que el KPI.

## 10. Testing y rendimiento

[`references/testing.md`](references/testing.md).

- Dominio puro primero; después datos; después componente/página; E2E por flujo
  crítico.
- axe en la ruta principal de cada módulo, en los temas que el proyecto soporte.
- Capturas en 320/375/768/1280/1600 px y los temas soportados.
- Presupuestos: chunk por ruta, INP < 200 ms, virtualización con umbral definido
  por el contrato, memo/selectores solo con medición.

## 11. Craft floor y bans universales

Verifica en una sola mirada al render: contraste, profundidad, espaciado (más
aire arriba de un encabezado), medida 65–75ch, escala y pesos, un solo momento
de motion, todos los estados, copy del producto y cobertura del brief.
Después haz una pasada de sustracción: retira ornamentos que no mejoren la
comprensión, la orientación ni la tarea.

**Bans universales:**

- Kicker/eyebrow sobre un encabezado.
- Gradient text; glass/blur decorativo.
- Borde lateral de color > 1 px en tarjetas/filas/callouts.
- Hard offset shadows; tarjetas anidadas; plantilla de tarjetas iguales.
- Emoji/glifo como icono; monospace como disfraz.
- Gradientes repetidos o grids de fondo sin canvas real.
- Ilustración tipo sketch; números de sección sin secuencia real.
- Sparklines/progress rings como sustituto de contenido.
- Modal como primera opción.
- Datos, claims o configuración inventados.
- Un default de categoría elegido sin mirar el brief o el modo del producto.

## 12. Anti-patrones

- Hardcodear métricas, nombres, fechas o etiquetas.
- Colores/valores sueltos donde existe token.
- Consumir red/almacenamiento directo desde una página.
- Recalcular una cifra distinta en tabla, gráfico y exportación.
- Pantallas o botones simulados sin acción real.
- Ocultar errores con datos falsos.
- Reducir tipografía para forzar contenido.
- Ignorar `prefers-reduced-motion` o añadir animación decorativa.
- Rediseñar cuando el pedido era pulir; pulir cuando el concepto está mal.
- Entregar una pantalla sin carga, vacío, error y sin permiso.

## 13. Definition of Done

- [ ] Tarea primaria completada sin ambigüedad.
- [ ] Estados: default, hover, focus, active, disabled, loading, empty, error,
      success y sin permiso.
- [ ] Responsive 320/375/768/1280/1600 y los temas soportados verificados.
- [ ] Teclado, foco y lector de pantalla considerados; axe sin graves.
- [ ] Contraste AA; tokens usados; cero valores visuales sueltos.
- [ ] Copy consistente, acciones nombradas, errores con recuperación.
- [ ] QueryKeys e invalidación correctas; sin datos duplicados.
- [ ] Tests por capa y flujo crítico E2E.
- [ ] Sin código muerto, imports sobrantes ni artefactos temporales.
- [ ] Lint, typecheck, tests y build pasan (si no se ejecutaron, se declara).
- [ ] Design system y registro de decisiones actualizados si aplica.

## 14. Comandos

Detecta los scripts reales en `package.json` o el gestor del proyecto. Como
referencia:

```bash
npm run lint
npm run typecheck
npm run test
npm run build
npx playwright install chromium   # primera vez, si hay E2E
npm run test:e2e
```

No declares una verificación sin ejecutarla y ver el resultado. Si algo falla,
corrígelo antes de cerrar. Apaga el dev server al terminar.

## 15. Relación con el proyecto

- Si existe una skill de proyecto (por ejemplo `trazo-brand`), actívala junto a
  esta: ella aporta tokens, rutas, labels y reglas de marca; esta aporta el
  proceso.
- Si no existe, usa `PRODUCT.md`/`DESIGN.md`/tokens como contrato y crea un
  adaptador de proyecto cuando el sistema se estabilice.
- Los presets visuales son opcionales. El brief y los tokens del proyecto ganan.
