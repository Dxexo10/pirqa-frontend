# Accesibilidad (WCAG 2.2 AA, genérico)

## Checklist por superficie

- [ ] Un solo `<h1>` por pantalla; jerarquía de encabezados lógica.
- [ ] Skip-link y `<main>` enfocable.
- [ ] `aria-current="page"` en la navegación activa.
- [ ] Foco visible en todos los interactivos.
- [ ] Orden de tabulación lógico; sin trampas de teclado.
- [ ] Contraste ≥ 4.5:1 en texto normal y ≥ 3:1 en texto grande.
- [ ] Estados con icono/punto + texto, nunca solo color.
- [ ] Botones con icono tienen nombre accesible.
- [ ] Tablas con encabezados semánticos y caption cuando aporte.
- [ ] Gráficos con leyenda, resumen `sr-only` y alternativa en tabla.
- [ ] Loading con `aria-busy`/`aria-live`; errores con reintento.
- [ ] Overlays accesibles y cerrables con Escape.
- [ ] Zoom 200 % y escalado de texto sin romper el layout.
- [ ] Formularios con label, `aria-invalid` y `aria-describedby`.

## Contraste

- Texto normal ≥ 4.5:1; grande ≥ 3:1.
- Verifica los temas que el proyecto soporte y todos los estados (hover, focus, disabled, error).
- Si un token falla, restringe su uso a texto grande/decorativo o corrige el
  token; documenta la medición.
- El foco necesita contraste con su entorno además de visibilidad.

## Touch target: 24 px vs. 44 px

- **24×24 CSS px** es el mínimo AA (SC 2.5.8) para cualquier objetivo. Excepciones:
  el objetivo está en una frase/bloque de texto, existe un control equivalente
  en la misma superficie, el tamaño lo define el agente de usuario o es esencial.
  La excepción de espaciado exige que un círculo de 24 px centrado no se solape
  con otro objetivo subdimensionado.
- **44×44 px** es el estándar del producto para acciones primarias, controles de
  flujo, navegación móvil y uso con pulgar. También es el criterio AAA (SC 2.5.5).
- No agrandes visualmente el icono: amplía el área interactiva manteniendo el
  icono en su tamaño.

## Formularios

- Label visible y asociado; nunca solo placeholder.
- `aria-invalid` en el campo y `aria-describedby` al mensaje.
- El mensaje de cada campo no lleva `role="alert"` propio.
- `role="alert"` se reserva al **resumen de errores** al enviar, con enlaces a
  cada campo; enfoca el resumen o el primer campo inválido.
- Marca requeridos en texto, no solo con asterisco.
- No deshabilites el submit para “evitar errores”: valida y explica.

## `prefers-reduced-motion`

- El `0.01ms` global es red de seguridad, no estrategia.
- Todo movimiento autoral necesita equivalente sin movimiento: color, opacidad,
  borde, posición instantánea o texto.
- Usa `motion-safe:` para la versión animada; el default es el estado final
  visible, no un elemento oculto que depende de la animación.
- Verifica con la preferencia emulada: tarea completada y feedback presente.

## Criterios WCAG 2.2 adicionales

- **2.4.11 Focus Not Obscured (Minimum):** el foco no puede quedar oculto por una
  topbar/header sticky o footer fijo. Define `scroll-padding-top` (y bottom) en
  el contenedor de scroll o `html`, igual o mayor a la altura del header.
  Verifica con Tab en listas largas, anclas y validación de formularios.
- **2.5.7 Dragging Movements:** toda interacción de arrastre necesita alternativa
  de puntero único: botones subir/bajar, selección numérica, menú “Mover a…”.
  Aplica a reordenar, mover tarjetas, sliders y tableros. No bases una acción
  esencial solo en drag.
- **1.4.10 Reflow:** a 320 CSS px de ancho (400 % de zoom en 1280) el contenido
  vertical no exige scroll horizontal. Refluye a una columna, apila acciones,
  permite wrap y deja scroll horizontal solo dentro de tablas/gráficos.
- Ninguna se cubre solo con axe: verifica teclado, zoom y viewport de 320 px.

## Verificación

- axe con tags WCAG A/AA en la ruta principal de cada módulo, en los temas que el proyecto soporte (claro por defecto; oscuro solo si se solicita);
  cero violaciones `critical`/`serious`.
- axe no sustituye teclado, contraste visual ni lector de pantalla.
