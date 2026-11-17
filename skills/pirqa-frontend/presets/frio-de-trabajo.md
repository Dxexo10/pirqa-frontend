# Preset: Frío de trabajo

Preset **opcional**, claro por defecto. Úsalo solo si encaja con el dominio y la audiencia; los tokens existentes del proyecto siempre mandan.

## Cuándo usarlo

- Herramientas de trabajo, analítica y operaciones con datos densos y sesiones largas.
- Productos que necesitan una base fría, compacta y firme sin sacrificar legibilidad.

## Cuándo no usarlo

- Productos de bienestar o aprendizaje que requieran una atmósfera más cálida.
- Marcas ya establecidas con paleta diferente o dominios que pidan otra señal emocional.

## Paleta semántica

| Token | Claro |
| --- | --- |
| `--background` | `#F1F5F7` |
| `--surface` | `#FFFFFF` |
| `--text-primary` | `#172A3A` |
| `--text-secondary` | `#526575` |
| `--border` | `#D8E1E7` |
| `--primary` | `#245F83` |
| `--primary-foreground` | `#FFFFFF` |
| `--accent-subtle` | `#E1EDF3` |
| `--success` | `#286247` |
| `--warning` | `#774812` |
| `--danger` | `#A23434` |
| `--info` | `#245F83` |

No implementes oscuro salvo que lo pida el brief o el usuario; derívalo de estos roles y mídelo por separado.

## Tipografía

Usa títulos de voz precisa y una familia de interfaz muy legible a tamaños compactos. Confirma disponibilidad en el proyecto; no inventes que una fuente está instalada. Mantén cifras tabulares en métricas.

## Forma

Radios pequeños o moderados y bordes visibles pero discretos. Da prioridad a alineación, agrupación y densidad controlada sobre tarjetas repetidas o sombras decorativas.

## Contraste medido

Ratios calculados con script de luminancia WCAG 2:

| Texto | Fondo | Ratio | Criterio |
| --- | --- | ---: | --- |
| `--text-primary` `#172A3A` | `--background` `#F1F5F7` | 13.40:1 | AA normal |
| `--text-secondary` `#526575` | `--background` `#F1F5F7` | 5.51:1 | AA normal |
| `--text-primary` `#172A3A` | `--surface` `#FFFFFF` | 14.70:1 | AA normal |
| `--primary` `#245F83` | `--surface` `#FFFFFF` | 6.91:1 | AA normal y enlace |
| `--primary-foreground` `#FFFFFF` | `--primary` `#245F83` | 6.91:1 | AA normal en botón |

Mide de nuevo los estados, colores de estado y cualquier adaptación de tokens. No asumas que los ratios se conservan tras cambiar tonos.
