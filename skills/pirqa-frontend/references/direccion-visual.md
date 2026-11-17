# Identidad visual desde el producto

## Cuándo aplica

Usa esta guía para crear una identidad visual cuando el producto aún no la tenga. Si ya hay marca o sistema, consérvalos y aplica el método solo a las decisiones que no estén definidas; no impongas los colores ni las formas de los presets.

Si el usuario aporta una pantalla o referencia, identifica qué la hace propia —composición, navegación, jerarquía, forma o tono— y conserva esa intención. Adapta el principio al producto actual; no copies la silueta ni conviertas la referencia en plantilla.

## Presenta la identidad antes del código

Antes de construir una interfaz nueva, presenta al usuario estas cinco líneas, con decisiones justificadas por el producto, su audiencia y su tarea. Evita adjetivos sueltos como «moderno», «limpio» o «amigable» sin explicar cómo se ven en la pantalla.

1. **Tesis visual:** la idea que une el carácter de la interfaz con la forma en que el usuario trabaja o decide.
2. **Señal de marca:** marca existente o símbolo/wordmark propuesto, y una frase de producto solo si aporta voz y tiene un lugar natural.
3. **Color:** roles para fondo, superficies, tinta y acento, con una razón ligada al dominio y al público.
4. **Tipografía y forma:** familias disponibles, jerarquía tipográfica, radios y bordes que expresen el carácter sin dañar lectura.
5. **Composición:** disposición concreta de la pantalla, estrategia de navegación, foco visual y cómo se organiza el contenido.

Acompaña la composición con un esquema breve o una descripción por regiones cuando ayude a entender el layout. No fuerces una hero section en una herramienta de producto.

### Si el producto aún no tiene marca

- Propón una identidad visual provisional, no una marca oficial. Cuando ayude a darle voz al producto, incluye una opción de nombre o frase breve y deja claro que es propuesta.
- Diseña un símbolo propio a partir de una acción, relación o forma del dominio cuando la pantalla necesite marca. No uses una inicial dentro de un recuadro como sustituto automático de identidad.
- No inventes beneficios, cifras ni promesas. No añadas un lema como kicker encima del encabezado ni lo repitas en cada pantalla.

No conviertas la propuesta en una fase de aprobación. Expón el razonamiento y continúa; pregunta solo si falta información que impide construir correctamente.

## Haz que la diferencia sea estructural

Antes de escribir código, comprueba que la identidad sobreviva más allá del color y el logo:

- **Prueba de transferencia:** ¿la misma navegación, composición y jerarquía funcionaría sin cambios en otro producto? Si sí, ajusta una decisión estructural a partir del dominio, el contenido o la tarea.
- **Prueba sin marca:** imagina la pantalla sin logo y sin color. ¿La organización de la información y los patrones de interacción siguen teniendo intención? Si no, todavía es una plantilla con otra piel.
- **Prueba de tarea:** ¿el foco visual ayuda a decidir, comprender o completar la acción principal? Si solo decora, descártalo.
- **Prueba de uso:** ¿la firma visual sigue siendo legible, accesible y cómoda durante el tiempo de uso previsto? Si no, modérala.

Haz que la tesis se note en la navegación y la composición principal cuando corresponda, y que se repita con coherencia en los componentes. No impongas siempre una barra lateral, tarjetas, panel oscuro, avatar, logo geométrico ni una única composición. Elige cada patrón por la arquitectura de información, el dispositivo y el trabajo del usuario.

## Deriva el lenguaje visual del producto

Inspecciona el brief, el flujo, los datos, las pantallas vecinas y el vocabulario del usuario. Usa esas señales para dar forma a la jerarquía, agrupación y ritmo visual. Sigue [`copy.md`](copy.md) para la voz y no inventes datos ni afirmaciones de negocio.

Elige el color según qué resuelve el producto y quién lo usa, no solo según una etiqueta de industria. Justifica la paleta en una línea. Si el usuario indica una paleta o la interfaz ya establece una, consérvala: deriva los estados y acentos de sus tokens semánticos. No introduzcas un color complementario ni un nuevo acento por gusto; añade otra familia solo si el usuario la pide o el sistema del producto ya la contempla. Si no hay paleta ni preferencia, propón una coherente con el dominio y la tarea antes de codificar. Esta tabla orienta; no prescribe:

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

Un color incoherente con el dominio —por ejemplo, rosa pastel para un sistema de gestión de proyectos— es un error de dirección. También lo es elegir un color solo porque suele asociarse a esa industria, sin comprobar si sirve al producto concreto.

## Color y contraste

- Prefiere superficies claras con matices pastel o apagados cuando el dominio lo permita; usa tinta oscura y un acento profundo para botones y enlaces.
- Reserva los pasteles para superficies y fondos, nunca para texto pequeño.
- Calcula con un script los ratios de cada par de texto y fondo que se use; entrega una tabla con los valores medidos. Incluye estados interactivos y todos los temas que el proyecto soporte. El oscuro solo se implementa si lo pide el brief o el usuario y su contraste se mide aparte.
- Texto normal: mínimo 4.5:1; texto grande: mínimo 3:1. Texto de botón y enlace también debe cumplir el mínimo correspondiente.
- No estimes el contraste a ojo.

## Varía sin perder coherencia

No reutilices por costumbre el mismo acento, composición, tratamiento tipográfico ni ancla. Usa un preset solo si encaja con el dominio, la audiencia y el brief. Busca diferencia en la organización y jerarquía, además del color.

## Expresión con medida

Concentra la expresión en decisiones que hagan más reconocible el producto y ayuden a usarlo. Deja que el resto facilite lectura y acción. Los bans universales de `SKILL.md` prevalecen si hay conflicto.
