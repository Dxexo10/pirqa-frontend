# Pirqa Frontend

*by Dxexo10*

Skill para agentes de IA que guía la construcción de módulos frontend completos
(lista, filtros, detalle, formulario, dashboard, gráficos y exportación) con
criterio de diseño, accesibilidad WCAG 2.2 AA y testing por capas.

## Qué incluye

| Carpeta | Contenido |
| --- | --- |
| `skills/pirqa-frontend/SKILL.md` | Protocolo de trabajo, blueprint y Definition of Done |
| `skills/pirqa-frontend/references/` | Tokens, componentes, patrones de pantalla, datos, accesibilidad, testing, gráficos, convenciones, copy y un ejemplo de módulo mínimo |
| `skills/pirqa-frontend/presets/` | Presets visuales opcionales |

## Cuándo usarla

- Construir, refinar o auditar un módulo completo con datos, estados y tests.
- No es para cambios triviales de un solo componente.

## Instalación

**Claude Code (plugin):**

```bash
/plugin marketplace add Dxexo10/pirqa-frontend
/plugin install pirqa-frontend@pirqa
```

**Manual:** copia `skills/pirqa-frontend/` a la carpeta de skills de tu agente
(por ejemplo `~/.claude/skills/`).

## Stack

Optimizada para React + TypeScript. Los conceptos de accesibilidad, tokens, copy
y patrones de pantalla aplican a cualquier framework; ver "Alcance y stack" en
`SKILL.md`.

## Modos

- **Completo** (default): productos reales.
- **Ligero**: pantalla única, sin persistencia.

## Licencia

MIT