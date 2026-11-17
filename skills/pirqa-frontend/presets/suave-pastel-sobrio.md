# Preset: Suave pastel sobrio

Preset **opcional**, claro por defecto. Úsalo solo si encaja con el dominio y la audiencia; los tokens existentes del proyecto siempre mandan.

## Cuándo usarlo

- Productos de aprendizaje, bienestar o consumo que admitan una atmósfera amable y serena.
- Interfaces que se beneficien de superficies suaves, con texto y acciones de alto contraste.

## Cuándo no usarlo

- Gestión operativa densa, finanzas de alta precisión o marcas con otro carácter establecido.
- Nunca uses el pastel como texto pequeño ni apliques el preset por ser la opción más fácil.

## Paleta semántica

| Token | Claro |
| --- | --- |
| `--background` | `#F7F4EE` |
| `--surface` | `#FFFFFF` |
| `--text-primary` | `#292C32` |
| `--text-secondary` | `#67696F` |
| `--border` | `#E5E1D8` |
| `--primary` | `#276B62` |
| `--primary-foreground` | `#FFFFFF` |
| `--accent-subtle` | `#E9F1E8` |
| `--success` | `#356A4A` |
| `--warning` | `#7A4B12` |
| `--danger` | `#A13732` |
| `--info` | `#365F83` |

No implementes oscuro salvo que lo pida el brief o el usuario; derívalo de estos roles y mídelo por separado.

## Tipografía

Usa una pareja con personalidad serena para títulos y alta legibilidad para interfaz. Confirma disponibilidad en el proyecto; no inventes que una fuente está instalada. Si solo hay una familia disponible, define una jerarquía tipográfica deliberada.

## Forma

Radios moderados y consistentes; controles claramente delimitados con borde fino. Reserva fondos pastel para áreas agrupadas y conserva superficies blancas para formularios y lectura.

## Contraste medido

Ratios calculados con script de luminancia WCAG 2:

| Texto | Fondo | Ratio | Criterio |
| --- | --- | ---: | --- |
| `--text-primary` `#292C32` | `--background` `#F7F4EE` | 12.75:1 | AA normal |
| `--text-secondary` `#67696F` | `--background` `#F7F4EE` | 5.00:1 | AA normal |
| `--text-primary` `#292C32` | `--surface` `#FFFFFF` | 13.99:1 | AA normal |
| `--primary` `#276B62` | `--surface` `#FFFFFF` | 6.24:1 | AA normal y enlace |
| `--primary-foreground` `#FFFFFF` | `--primary` `#276B62` | 6.24:1 | AA normal en botón |

Mide de nuevo los estados, colores de estado y cualquier adaptación de tokens. No asumas que los ratios se conservan tras cambiar tonos.
