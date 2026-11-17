# Copy de interfaz (genérico)

El texto es contenido de diseño. Se escribe con la misma intención que el
espaciado y el color: cada elemento hace un solo trabajo.

Las reglas de estilo (sentence case, tratamiento de anglicismos, gerundios,
puntuación) dependen del idioma y de la guía de estilo del producto. Los
ejemplos en español de este archivo son ilustrativos; si el producto está en
otro idioma, aplica su convención.

## Voz del producto

- Idioma, tono y registro del producto y su audiencia.
- Respeta la convención de mayúsculas del idioma; si el producto no define una,
  sentence case es un buen default. Las micro-etiquetas de datos son una
  excepción visual, no de copy.
- Evita anglicismos innecesarios según el idioma y el público; usa el término
  que el usuario reconoce.
- Verbos activos y concretos.

## Acciones

- El control nombra exactamente lo que hace: “Guardar cambios”, “Crear
  proyecto”, “Archivar”.
- Una acción conserva su nombre en todo el flujo: el botón “Publicar” produce
  “Publicado”.
- Sin “Enviar”, “Aceptar” ni “Continuar” genéricos cuando hay un verbo preciso.
- Estado de carga con gerundio: “Guardando…”, “Exportando…”.
- Acción destructiva con verbo y objeto exactos.

## Errores

- Nombran el problema y la recuperación, en la voz de la interfaz.
- No se disculpan, no culpabilizan y no son vagos.
- Sin códigos ni jerga técnica visibles.
- Un error de red no borra lo escrito; ofrece reintento.
- Un 403 explica el permiso y la vía de solicitud.

## Vacíos

- Enseñan la interfaz y ofrecen la acción siguiente.
- Vacío inicial: “Aún no hay X” + crear el primero.
- Sin resultados: “No encontramos X con estos filtros” + limpiar filtros.
- Nunca “No hay datos” a secas.

## Éxito

- Confirma la acción nombrada y el objeto.
- Un solo toast por acción; sin duplicar en banner.
- No uses “Éxito”, “OK” ni “Hecho” sin contexto.

## Datos y claims

- No inventes cifras, nombres, fechas ni beneficios.
- Rotula datos simulados o de demostración.
- Presenta cifras con periodo y fecha de corte.
- No cambies copy factual ni añadas promesas sin confirmación.

## Consistencia y fuente

- Todo texto de dominio sale del archivo de labels del proyecto.
- Mensajes de formulario centralizados en el schema o en un objeto del módulo.
- Mismo término para el mismo concepto en toda la app.
- Evita puntos suspensivos decorativos y flechas pegadas al CTA.

## Antes de escribir

1. ¿Qué necesita entender el usuario para actuar?
2. ¿Cuál es la acción y cuál su resultado?
3. ¿Se puede decir con menos palabras sin perder precisión?
4. ¿Suena como el producto o como una plantilla?
