# Dirección visual sin sistema previo

## Cuándo aplica

Úsala únicamente si el proyecto no tiene tokens, marca ni design system. Si alguno existe, manda la identidad del proyecto y este archivo no se usa.

## Decide antes de escribir código

Presenta y justifica estas cinco líneas antes de implementar:

1. **Ánimo:** qué sensación debe transmitir y por qué sirve a la tarea.
2. **Color dominante y acento:** familias elegidas según el dominio y el público.
3. **Pareja tipográfica:** una voz para títulos y otra para interfaz, o una sola con intención explícita.
4. **Forma:** radios y tratamiento de bordes, apropiados a la densidad y al uso.
5. **Elemento ancla:** el elemento visual que organiza esta pantalla y su función.

### Color según dominio

Elige a partir de qué resuelve el producto y quién lo usa; no por gusto personal. Justifica la paleta en una línea. La tabla orienta, no sustituye el brief:

| Dominio | Carácter de paleta orientativo | Razón |
| --- | --- | --- |
| Gestión de proyectos | Azules, verdes o neutros equilibrados; acento nítido | Orden, coordinación y lectura sostenida |
| Finanzas | Azules profundos, verdes sobrios y neutros | Confianza, precisión y jerarquía numérica |
| Salud | Verdes, azules suaves y neutros cálidos | Calma y claridad en tareas sensibles |
| Educación | Tonos acogedores y diferenciables, con acentos vivos medidos | Orientación, aprendizaje y reconocimiento |
| Comercio | Neutros de producto con acento alineado al catálogo o la marca | Prioridad al producto y a la acción comercial |
| Analítica y operaciones | Neutros fríos o cálidos contenidos con acento funcional | Densidad, comparación y sesiones prolongadas |
| Creatividad y medios | Dominante expresivo según audiencia, con base que preserve legibilidad | Personalidad sin competir con el contenido |
| Administración pública | Azules, verdes o tierras sobrios y alto contraste | Servicio, confianza y lectura inclusiva |

Un color incoherente con el dominio —por ejemplo, rosa pastel para un sistema de gestión de proyectos— es un error de dirección, no una preferencia estética.

## Preferencia de color y contraste

- Prefiere superficies claras con matices pastel o apagados cuando el dominio lo permita, texto en tinta oscura y un acento más profundo que alcance AA para botones y enlaces.
- Reserva los pasteles para superficies y fondos; nunca los uses en texto pequeño.
- Calcula con un script los ratios de cada par texto/fondo y entrega una tabla con los valores medidos. Incluye estados interactivos y cada tema solicitado/soportado.
- Texto normal: mínimo 4.5:1; texto grande: mínimo 3:1. Texto de botón y enlace también debe cumplir el mínimo correspondiente.
- No estimes el contraste a ojo.

## Varía entre proyectos

No reutilices por costumbre el mismo acento ni la misma paleta. Un preset solo se usa cuando encaja con el dominio, la audiencia y el brief.

## Anti-defaults prohibidos

- Tema oscuro con acento lavanda/violeta elegido por inercia; el tema claro es el predeterminado salvo petición explícita.
- Gradientes púrpura sobre blanco.
- Tarjetas iguales organizadas en rejilla como composición automática.
- Una sola tipografía genérica sin intención.

## Ideas estéticas

Explora tipografía con carácter, color dominante con acento puntual, un elemento firma por pantalla, composición con aire y profundidad sutil. Modera estas ideas en UI de producto: prioriza lectura, orientación y uso prolongado. Los bans universales de `SKILL.md` prevalecen si hay conflicto.
