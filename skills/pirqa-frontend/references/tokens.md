# Tokens, color y tipografía (genérico)

La fuente de verdad son los tokens del proyecto. Esta guía define cómo usarlos,
no qué colores elegir.

## Modelo de tokens

| Capa | Ejemplos | Regla |
| --- | --- | --- |
| Primitivos | `--brand-*`, `--palette-*` | Solo se declaran; no se usan directo en componentes |
| Semánticos | `--background`, `--surface`, `--text-primary`, `--text-secondary`, `--border`, `--primary`, `--success`, `--warning`, `--danger`, `--info` | Lo que consumen los componentes |
| Componente | `--sidebar`, `--card`, `--ring` | Derivados de semánticos |
| Datos | `--chart-1..n`, `--chart-muted` | Series y comparativos |

- Prohibido hex/px sueltos donde existe token.
- El color de marca no representa estados. Los estados combinan icono + texto +
  color y usan tokens semánticos.
- El tema predeterminado es claro. Implementa oscuro solo si lo pide el brief o el usuario; deriva ambos modos de los mismos tokens semánticos y verifica el contraste por separado. No dupliques paletas ni condiciones por vista.

## Contraste

- Texto normal ≥ 4.5:1; texto grande ≥ 3:1.
- Placeholder y texto de apoyo ≥ 4.5:1.
- Sobre superficies de color, tinta el texto secundario desde ese tono o el
  foreground; nunca lo fuerces a gris.
- Si un token no cumple, restringe su uso a texto grande/decorativo o corrige el
  token. Documenta la medición.
- Verifica los temas que el proyecto soporte: un par puede pasar en claro y fallar en oscuro.

## Tipografía

- Respeta la pareja tipográfica y la escala del proyecto.
- Escala de producto sin `clamp`; pasos fijos y previsibles.
- Cifras con `tabular-nums`.
- Micro-etiquetas (KPI, cabeceras de tabla, métricas) pueden usar un paso menor
  (11–12 px) siempre que sean versalitas con tracking y no cuerpo de texto.
- Medida de prosa 65–75ch; tablas densas pueden superar 120ch.
- `text-wrap: balance` en encabezados y `pretty` en párrafos.

## Espaciado, radios y sombras

- Espaciado en la escala del proyecto (múltiplos de 4 es lo común).
- Radios por rol: controles, tarjetas, paneles, navegación. No un radio único
  para todo.
- Elevación una sola vez: borde **o** sombra. Sombra suave, nunca hard offset
  salvo mundo neobrutalista explícito.
- Sin gradientes decorativos fuertes.

## Temas

- Tema claro por defecto; solo añade `dark` si lo pide el brief o el usuario.
- Preferencia `light | dark | system` en storage con lectura segura cuando aplique.
- Aplica el tema antes del primer render (script inline) para evitar flash.
- Escucha `prefers-color-scheme` y el evento `storage` si aplica.
- Los pares críticos se prueban por tema.

## Movimiento y `prefers-reduced-motion`

- 150–250 ms en hover, apertura, filtros, feedback y cambio de estado.
- El movimiento comunica estado; no decora ni coreografía la carga.
- `prefers-reduced-motion` exige un equivalente sin movimiento: color, opacidad,
  borde o estado instantáneo. El default debe ser el estado final visible.
- No uses movimiento para comunicar algo que se pierde al desactivarlo.
- Verifica con la preferencia emulada: la tarea se completa y el feedback existe.

## Superficies del navegador

Tema desde la paleta: selección, caret, scrollbars, focus ring,
`underline-offset`, autofill, `color-scheme` y números tabulares. Es la señal más
barata de una interfaz construida y no ensamblada.
