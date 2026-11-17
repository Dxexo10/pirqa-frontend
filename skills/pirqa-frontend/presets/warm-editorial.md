# Preset: Warm Editorial

Preset visual **opcional**. No es el default de la skill. Úsalo solo si el
brief pide un producto empresarial cálido, editorial y sobrio. Si el proyecto
ya tiene tokens, este preset se mapea sobre ellos; no reemplaces su marca.

## Cuándo tiene sentido

- Producto B2B, paneles de gestión, datos densos, sesiones largas.
- Se busca confianza y claridad, no espectáculo.
- El brief pide una estética cálida, humana y editorial, sin caer en plantilla.

No lo uses para marcas que ya tienen identidad, ni para productos lúdicos,
de consumo masivo o con una paleta aprobada distinta.

## Paleta (mapear a tokens semánticos)

| Rol semántico | Claro | Oscuro |
| --- | --- | --- |
| `--background` | `#F5F2EB` | `#191C19` |
| `--surface` | `#FFFFFF` | `#30352F` |
| `--text-primary` | `#252824` | `#F0EAE0` |
| `--text-secondary` | `#686C64` | `#B2B8AE` |
| `--border` | `#E8E4DC` | `#454B43` |
| `--primary` | `#B4522F` | `#E18A69` |
| `--primary-foreground` | `#FFFFFF` | `#191C19` |
| `--accent` | `#C65D3A` | `#E18A69` |
| `--accent-subtle` | `#F5E5DD` | `#3A2822` |
| `--success` | `#4F6B47` | `#A9C59A` |
| `--warning` | `#8A5714` | `#E8B77A` |
| `--danger` | `#A63F32` | `#F0A79B` |
| `--info` | `#4F6070` | `#A8BCCB` |
| `--sidebar` | `#252824` | `#252A25` |
| `--chart-1..5` | `#C65D3A`, `#60715A`, `#B7791F`, `#858A80`, `#4F6070` | `#E18A69`, `#9FB08F`, `#D9A441`, `#8E948A`, `#8FA6B6` |

Notas de contraste:

- `#C65D3A` sobre blanco no alcanza 4.5:1 para texto normal; usa `#A84B2C` para
  enlaces/texto pequeño y `#B4522F` para botones primarios.
- `#858A80` no cumple AA como texto normal; úsalo solo en texto grande o
  decorativo. Para metadatos usa `#686C64`.

## Tipografía

- Encabezados: Manrope Variable.
- Interfaz y cifras: Inter Variable con `tabular-nums`.
- Escala fija: 11 (micro-etiquetas) · 12 · 13 · 14 · 15 · 16 · 18 · 20 · 24 ·
  30 · 32 px. Sin `clamp` en UI de producto.
- Medida de prosa 65–75ch.

## Forma y profundidad

- Radios: 8–12 px controles, 18 px tarjetas, 20 px paneles, 22 px navegación.
- Sombras suaves con offset y blur; sin hard shadows.
- Elevación una sola vez: borde o sombra.
- Sin glassmorphism ni gradientes llamativos.
- Un acento cálido puntual; no decores con él.

## Layout

- Navegación lateral flotante de altura completa (16 px de margen, radio 22 px,
  grafito), o una sidebar sólida equivalente según el proyecto.
- Contenido con máximo amplio (~1600 px), padding generoso.
- Densidad legible; tablas cómodas.
- Un ancla visual oscura para la métrica protagonista; el resto claro.

## Movimiento

- 150–250 ms; comunica estado.
- Un solo momento autoral; sin coreografía de carga.
- `prefers-reduced-motion` con equivalente sin movimiento.

## Cómo aplicarlo

1. Mapea los roles de la tabla a los tokens del proyecto.
2. Ajusta tipografía y radios a su escala si ya existe.
3. No copies nombres de clases ni rutas de otro proyecto.
4. El tema claro es el default; implementa oscuro solo si se solicita y verifica su contraste por separado.
5. Conserva la marca y el logo del proyecto; este preset es solo atmósfera.

## Origen

Derivado del sistema visual de [Trazo](https://github.com/Dxexo10/trazo), usado como caso de estudio. No es una
marca ni un default; es una atmósfera entre otras posibles.
