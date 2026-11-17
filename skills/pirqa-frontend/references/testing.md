# Testing y rendimiento (genérico)

## Qué se prueba en cada capa

| Capa | Herramienta | Qué cubre |
| --- | --- | --- |
| Dominio | Unit runner del proyecto | Reglas puras, agregaciones, diff, filtros, formato |
| Datos | Unit runner + adaptador local | Repositorios, seed determinista, adaptadores HTTP |
| Hooks / componentes | Testing Library + jsdom o equivalente | Render, interacción, estados, navegación |
| Página / flujo | Testing Library o E2E | Integración de pantalla y ruta |
| E2E | Playwright/Cypress | Flujo crítico, móvil, API, accesibilidad |
| Accesibilidad | axe o equivalente | WCAG A/AA en rutas principales |

Usa el inventario existente del repo; no crees un framework paralelo.

## Reglas

- **Dominio primero:** si una regla es pura, pruébala ahí. No la pruebes tres
  veces desde la UI.
- **Un test de página** por módulo: carga, vacío, error y filtros clave.
- **Un E2E por flujo crítico** (crear, editar, archivar, revisar, exportar).
  Resetea el dataset antes de cada escenario.
- **axe en la ruta principal de cada módulo nuevo, en tema claro y oscuro**;
  agrégalo a la lista de rutas del test de accesibilidad.
- En E2E usa el **adaptador mock determinista del proyecto** (el mismo dataset
  demo que consume la app), no mocks por test ni repositorios falsos por
  escenario. Los mocks unitarios viven en la capa de datos, no en el flujo E2E.
- Sin latencia artificial en tests.
- Nombra por comportamiento observable, no por implementación.

## Comandos

Detecta los scripts reales. Referencia:

```bash
npm run test
npm run test:coverage
npm run test:e2e
npx playwright install chromium   # primera vez
```

No bajes los umbrales de cobertura para “pasar”.

## Capturas visuales

Para cambios de UI, captura y revisa:

- Anchos: **320, 375, 768, 1280 y 1600 px** (320 valida reflow 1.4.10).
- Temas: **claro y oscuro**.
- Estados: carga, vacío, error, éxito y filtros activos.
- Copy largo y tablas densas.

Revisa las capturas en una sola pasada y corrige todo lo que revelen antes de
volver a capturar. Si no existe suite de regresión visual, son evidencia manual.

## Presupuestos de rendimiento

Ajusta los números al proyecto y verifícalos con el build real.

| Métrica | Presupuesto de referencia |
| --- | --- |
| Chunk por ruta | Definido por el proyecto (mídielo; no lo inventes) |
| INP | < 200 ms |
| Listas largas | Virtualizar sobre el umbral del contrato |
| Gráficos | Carga diferida; nunca en el primer render del shell |
| Imágenes | Dimensiones explícitas; lazy fuera del primer viewport |

## Evitar re-renders

- Selecciona del cache con selectores estables; no devuelvas objetos nuevos en
  cada render.
- `useMemo`/`memo` **solo con medición** (profiler o INP).
- Divide componentes grandes por frontera de estado, no por estética.
- No metas listas completas en estado local si ya viven en el cache.
- Un cambio de filtro debe producir una key nueva, no re-renderizar todo con
  datos viejos.
