---
name: dashboards-cobranza-tooltips
description: Formato estándar de descripciones emergentes (tooltips) con iconos para todas las hojas de dashboards de Cobranza BINATSA, incluido el XML de Tableau. Usar al crear o rehacer tooltips.
---

# Tooltips · Dashboards de Cobranza BINATSA

Obligatorios en todo gráfico y tarjeta. Estructura estándar (si el usuario ya aprobó un tooltip en el proyecto, copiar su formato):
1. Título en negrita con color de acento (verde #2e7d32 o color de marca).
2. Datos: etiqueta normal + valor en negrita y más grande; valores dinámicos (hora, día, segmento, métrica).
3. Línea divisoria fina.
4. Tres secciones con "▸" en negrita y 1-3 líneas:
   - "🔎 QUÉ MIDE" (qué valor cuenta)
   - "🧮 CÓMO SE CALCULA" (fórmula en palabras, cómo se compone y se lee)
   - "🎯 PARA QUÉ SIRVE ESTA VISTA"
5. Colores por sección (QUÉ MIDE azul/oscuro, CÓMO SE CALCULA #9A5A00, PARA QUÉ SIRVE #2e7d32); cuerpo en gris oscuro; iconos coherentes con el contenido. Los verdes y ámbar son los mismos hex del semáforo de dashboards-cobranza-estructura: si cambian allá, cambian aquí.
6. Cuando hay filas por segmento de cartera, línea gris con la leyenda de rangos (ej. "A = 06-30 días · B = 31-60 · C = 61-90", según el cliente). Sin pie de campaña.

## En XML (.twb)
- `<customized-tooltip><formatted-text><run …>` dentro del pane de cada worksheet.
- Salto de línea = `<run>Æ&#10;</run>`.
- Campos dinámicos como runs CDATA `<[datasource].[campo]>`.
- Trabajar en copia del .twbx sobre el archivo que el usuario subió; reempaquetar con el .twb, Data/Extracts y Image intactos; el usuario publica.
