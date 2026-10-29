---
name: dashboards-cobranza-tooltips
description: Formato estándar de descripciones emergentes (tooltips) con iconos para todas las hojas de dashboards de Cobranza BINATSA, incluido el XML de Tableau. Usar al crear o rehacer tooltips.
---

# Tooltips · Dashboards de Cobranza BINATSA

Obligatorios en todo gráfico y tarjeta. Formato tomado de los tooltips de las hojas visibles de los tableros de referencia; copiarlo en todas las hojas, en este orden:
1. Título en negrita en verde #2e7d32.
2. Datos: una línea por dato, con emoji + etiqueta en negrita + valor dinámico en negrita (por ejemplo "⏰ Hora: …", "📅 Día: …", "📊 Gestiones: …", "📌 Métrica elegida: …").
3. Una línea en blanco (no hay línea divisoria).
4. Si la hoja tiene segmentos de cartera, desglose: encabezado en negrita "📊 Por segmento — <métrica>" y una línea por segmento con ■ en el color de ese segmento en la rampa de segmentos, el nombre del segmento y el valor en negrita.
5. Tres secciones separadas por una línea en blanco, cada una con "▸", su emoji y 1-3 líneas de cuerpo en el color normal:
   - "▸ 🔎 QUÉ MIDE" (qué valor cuenta), título en negrita #9A5A00.
   - "▸ 🧮 CÓMO SE CALCULA" (fórmula en palabras, cómo se compone y se lee), título en negrita #9A5A00.
   - "▸ 🎯 PARA QUÉ SIRVE" (para qué sirve esta vista), título en negrita #2e7d32.
6. Al final de CÓMO SE CALCULA, en gris #757575, la leyenda de rangos de los segmentos (ej. "A = 06-30 días · B = 31-60 · C = 61-90", según el cliente). Sin pie de campaña.
7. Tamaños: título y valores 12 pt, títulos de sección 10 pt.

Los hex repiten los del semáforo de dashboards-cobranza-estructura (verde, y el ámbar en su variante oscura para texto pequeño): si cambian allá, cambian aquí. Aquí son solo decoración; no indican mejora ni alerta.

## En XML (.twb)
- `<customized-tooltip><formatted-text><run …>` dentro del pane de cada worksheet.
- Salto de línea = `<run>Æ&#10;</run>`.
- Campos dinámicos como runs CDATA `<[datasource].[campo]>`.
- Trabajar en copia del .twbx sobre el archivo que el usuario subió; reempaquetar con el .twb, Data/Extracts y Image intactos; el usuario publica.
