# Gráficos (genérico)

Usa la librería del proyecto (Recharts, visx, ECharts, D3, etc.). Esta guía fija
las reglas de comunicación, no la implementación.

## Reglas

- **Máximo 4 series por gráfico + “Otros”** cuando haya más categorías. La serie
  “Otros” usa el token de comparativo/muted (`chart-muted` si existe). Más
  series dejan de ser legibles; agrupa o divide.
- **Colores:** tokens de chart del proyecto (`chart-1..n`). Nunca inventes hex.
- **Distinción no solo por color:** además del tono, usa estilo de línea
  (sólida/discontinua), marcadores, etiquetas directas o patrón. Leyenda visible.
- **Gradientes de relleno:** permitidos solo como decoración bajo una línea o
  barra (del color de la serie al fondo, opacidad baja). No son la codificación
  de la categoría, no sustituyen a la leyenda, no se usan en texto ni en el
  trazo principal, y deben ser legibles en ambos temas. Un gradiente que
  distingue series o comunica un valor está prohibido.
- **Ejes y unidades visibles:** eje Y con formato local y unidad (`$`, `%`,
  miles). Sin decimales donde no aportan. Grid discreto, solo horizontal.
- **Sin doble eje** salvo magnitudes incompatibles y brief explícito; rotula
  ambos lados.
- **Tooltip accesible:** fondo, borde y texto del sistema; nunca solo hover.
  Activa las capas de accesibilidad de la librería si existen y ofrece tabla.
- **Resumen `sr-only`:** una frase con el insight y los totales, derivada de los
  mismos datos.
- **Alternativa en tabla:** toggle “Ver tabla” o tabla visible para lectores de
  pantalla y cifras exactas.
- **Estado vacío:** mensaje dentro de la tarjeta, no un gráfico con ejes vacíos.
- **Carga diferida:** lazy + suspense con skeleton de la altura final para
  evitar layout shift.
- **Una sola fuente:** el gráfico consume la misma agregación que el KPI y la
  tabla. No recalcules en el componente.

## Checklist de un gráfico nuevo

- [ ] Máx. 4 series + “Otros”.
- [ ] Tokens de chart y distinción adicional.
- [ ] Ejes con unidad y formato local.
- [ ] Tooltip legible y accesible.
- [ ] Resumen `sr-only` con el insight.
- [ ] Tabla alternativa o exportación con las mismas cifras.
- [ ] Estado vacío y de error.
- [ ] Carga diferida y sin layout shift.
- [ ] Misma fuente que KPI/tabla.
