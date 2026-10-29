> **OBSOLETO. No usar como skill.** Es el borrador original con los 6 módulos juntos. Las reglas vigentes están en `skills/*/SKILL.md` y varias de las de aquí ya cambiaron (por ejemplo: tamaño en Rango con altura mínima 1300 px, tarjetas KPI con título redondeado, desglose de asesores siempre visible, Desde y Hasta como parámetros). Se conserva solo como historial.

# Skills de dashboards de Cobranza BINATSA (borrador dividido)

Documento con la skill dividida en 6 módulos. Cada módulo es un SKILL.md independiente (cabecera `---` incluida) para guardarlo por separado cuando decidas.

Orden sugerido de uso: 1 (principal, siempre) → 2 (estructura y estilo) → 3 (KPIs) → 4 (tooltips) → 5 (vista cliente y limpieza) → 6 (publicar y monitoreo).

Índice
1. dashboards-cobranza-base: preguntas iniciales, recursos, reglas generales y flujo
2. dashboards-cobranza-estructura: Dirección, Operación, layout, interactividad, estilo visual
3. dashboards-cobranza-kpis: tarjetas KPI y glosario de definiciones
4. dashboards-cobranza-tooltips: descripciones emergentes
5. dashboards-cobranza-cliente-limpieza: vista del cliente y limpieza de huérfanos
6. dashboards-cobranza-publicacion: checklist, publicación y monitoreo de actualización

---

## 1. dashboards-cobranza-base

```markdown
---
name: dashboards-cobranza-base
description: Punto de partida para cualquier dashboard de Cobranza BINATSA en Tableau Cloud: preguntas iniciales, recursos, reglas generales y flujo de trabajo. Usar primero; luego los módulos de estructura, KPIs, tooltips, cliente/limpieza y publicación.
---

# Base · Dashboards de Cobranza BINATSA

Responde siempre en español, corto y directo. Usuario: Jonathan, BINATSA.
Plantilla para cualquier cliente. Nada es específico de un proyecto; los datos de cada proyecto se preguntan al iniciar.

## Módulos relacionados
- dashboards-cobranza-estructura: Dirección, Operación, layout, estilo.
- dashboards-cobranza-kpis: tarjetas KPI y glosario.
- dashboards-cobranza-tooltips: descripciones emergentes.
- dashboards-cobranza-cliente-limpieza: vista del cliente y limpieza de huérfanos.
- dashboards-cobranza-publicacion: checklist, publicación y monitoreo.

## Recursos de BINATSA
- Repositorio de GitHub: Vuneit450/binatsa-recursos.
  - logos/binatsa.svg: logo vectorial (turquesa #00B3B8, azul marino #0B1F3A). Usarlo siempre; si Tableau no acepta SVG en el objeto Imagen, generar un PNG desde el SVG.
  - clientes/<cliente>/: logo y paleta del cliente (si no existe, pedirlo y, con permiso del usuario, subirlo ahí).
  - Si el repositorio no está conectado a la sesión, leerlo desde el navegador o pedir el archivo.
- Los archivos no se guardan en la skill; solo la ruta.

## Preguntas obligatorias al iniciar un proyecto nuevo
Hacerlas con la herramienta de preguntas de opción múltiple (no en texto suelto), en una sola tanda de máximo 4 preguntas, ofreciendo opciones concretas y una recomendada. No empezar a construir hasta tener las bloqueantes (1, 2 y 3). Si el usuario ya las respondió en el chat, no repetirlas. Si la sesión es desatendida, elegir lo razonable, declararlo arriba y marcarlo "por confirmar".

Tanda 1 (bloqueantes):
1. Logo del cliente: opciones "Lo subo ahora", "Está en el repositorio (clientes/<cliente>/)", "No hay logo: usar solo texto con sus colores". Siempre confirmarlo, aunque ya exista en el repositorio.
2. Colores de marca del cliente: "Los paso (hex)", "Sácalos del logo", "Usa la paleta BINATSA por ahora". La paleta de encabezados, acentos y KPIs sale de aquí.
3. Fuente de datos: "Tabla/consulta existente", "Archivo (CSV/Excel)", "Aún no hay: usar datos de ejemplo del kit". Confirmar campos disponibles: canales (llamadas, SMS, Mail, Blaster, WhatsApp, Visitas, Predictivo, Inbound), tipificaciones, asesor, zona, monto, promesas, pagos.

Tanda 2 (antes de publicar):
4. Segmentación de cartera del cliente (buckets/rangos de mora, nombres y días). No asumir A/B/C.
5. Workbook, proyecto y sitio de Tableau Cloud (publicar siempre sobre el workbook existente cuando ya hay uno).
6. Horario, frecuencia y zona horaria de actualización del extracto.
7. Canal de alertas de fallo de actualización: opciones "Slack (¿cuál canal?)", "Correo", "Otro", "Sin alertas". Nunca asumir uno.
8. Qué vistas ve el cliente final y quiénes tienen acceso.
9. Si el usuario sube un .twbx, trabajar sobre ESE archivo.

## Reglas generales (Tableau Cloud)
1. NUNCA mover ni modificar consultas/fuentes. Solo ocultar campos huérfanos que ningún reporte use ni vaya a usar.
2. Las credenciales las captura SIEMPRE el usuario; nunca escribir contraseñas.
3. Publicar SOBRE el workbook existente (mismo nombre y proyecto) para conservar programación y credenciales; con otro nombre se pierde la programación.
4. Edición web: autoguardado como "Borrador"; Publicar sobrescribe. Arrastrar anchos de columna no funciona. Hojas ocultas se abren desde el icono "Ir a hoja" de la zona del dashboard.
5. Alertas de fallo: canal elegido por el usuario para cada proyecto; lo configura el usuario en Tableau.

## Flujo de trabajo
1. Hacer las preguntas iniciales; usar el archivo subido.
2. Cambios de XML (tooltips, campos ocultos): trabajar en copia versionada del .twbx (.twb + Data/Extracts/*.hyper + Image/), con nombre versionado; el usuario publica.
3. Cambios simples: edición web sin marcas seleccionadas y publicar sobre el mismo workbook.
4. Para revisar dashboards publicados: usar el navegador (Claude in Chrome o el integrado con sesión del usuario); si pide contraseña, que el usuario inicie sesión.
5. Correr el checklist de publicación; verificar y reportar en 1-2 frases.
```

---

## 2. dashboards-cobranza-estructura

```markdown
---
name: dashboards-cobranza-estructura
description: Estructura estándar (Dirección y Operación), layout, interactividad y estilo visual de dashboards de Cobranza BINATSA en Tableau Cloud. Usar al diseñar o modificar vistas.
---

# Estructura y estilo · Dashboards de Cobranza BINATSA

## Estructura estándar
Siempre dos vistas, Dirección y Operación, con botones de navegación entre ellas ("Ir a Operación" / "Ir a Dirección"). Encabezado con logo BINATSA y logo del cliente, ambos visibles.

### Dirección (¿cómo va la campaña?)
- KPIs generales: monto recuperado, pagos, promesas, % cartera gestionada, % contacto titular.
- Otros canales si existen: datos propios por canal en un gráfico comparativo (contactos, promesas, efectividad).
- Intensidad de base por segmento de cartera (asignadas, gestionadas, sin gestión, intentos por cuenta).
- Mapa de visitas por zona: de dónde salen más promesas y recuperación (zona/colonia/municipio/estado según el campo disponible).
- Tendencia día a día de promesas y recuperación.

### Operación (¿qué hay que corregir hoy?) — siempre estas 3 piezas
1. Mapa de calor día × franja horaria con segmentador (parámetro "Métrica") para: Gestiones, Promesas, Monto recuperado, % de contacto.
2. Tipificaciones ordenadas DESC (a dónde se va el mayor flujo).
3. Asesores: cuentas asignadas, gestiones totales, % promesado, monto recuperado.

Layout de referencia de Operación (dos columnas bajo las tarjetas KPI; cada bloque con franja de encabezado emoji + pregunta + subtítulo):
- Fila 1: "¿En qué horas contestan los titulares?" (mapa de calor + selector de Métrica) | "¿Quién produce y quién necesita apoyo?" (tabla por asesor).
- Fila 2: "¿Qué está pasando en las llamadas?" (tipificaciones DESC apiladas por segmento) | "¿A qué horas se trabaja más?" (barras por hora apiladas por segmento).
- Fila 3: "¿Qué segmento tiene más cuentas sin tocar?" (pastel) | "Visitas por resultado" (barras apiladas).
- Pie: texto "Cómo leer" con la aclaración de fuentes.

## Layout
- Todo en contenedores en MOSAICO (no flotante).
- Tamaño automático, lo más grande posible para escritorios grandes (ajustar a ancho; altura suficiente).
- NINGÚN gráfico, tarjeta ni filtro lleva borde ni color de fondo: todo transparente (zonas, hojas, KPIs, filtros, parámetros, contenedores). Solo los encabezados de zona pueden usar la franja de color de marca.

## Interactividad
- Gráficos dinámicos entre sí: clic en una marca filtra los demás (acciones de filtro de dashboard; segmento, asesor, canal, hora, día, tipificación y zona como dimensiones de enlace).
- Preferir tipos de gráfico que admitan segmentador/parámetro.
- Filtros globales arriba: segmento, Desde, Hasta. Enlace "Guía de uso".
- En edición web NO dejar marcas seleccionadas ni parámetros cambiados antes de publicar.

## Estilo visual
- Encabezados de zona: franja de color de marca, título blanco con emoji coherente + subtítulo de una línea con la pregunta de negocio.
- KPIs grandes con número en color (adaptar a la marca del cliente).
- Todo porcentaje con símbolo % (1 decimal). Dinero con $ y miles; M/K en cifras grandes. Si el % se corta en celdas angostas (p. ej. mapa de calor dentro del tablero), avisar y proponer sin decimales o ensanchar; nunca dejar el número sin %.
- Barras de un solo color: resaltar la más alta (acento) con su número arriba, resto neutro. Barras apiladas por segmento mantienen un color fijo por segmento; si chocan con la marca, proponer ajuste.
- Sin ruido: nada de gráficos huérfanos, hojas visibles que el cliente no consulta (ocultas; acceso por "Ir a hoja"), ni calculados sin uso.

## Paleta y tipografía
Paleta (derivarla de los colores del cliente; si solo hay logo, extraer 2 colores dominantes):
- Primario del cliente: encabezados de zona, selección y barra destacada (la más alta).
- Secundario del cliente: acentos y líneas.
- Neutro: barras no destacadas y texto secundario en gris con matiz hacia el primario (no gris puro). Texto principal casi negro, nunca #000 puro.
- Semáforo fijo, independiente de la marca: verde #2e7d32 (mejora), rojo #c62828 (empeora), ámbar #b45f06 (alerta). Invertir cuando bajar es bueno.
- Segmentos de cartera: una rampa del primario del cliente de claro a oscuro (menos mora = más claro); mismo color por segmento en TODAS las hojas. Nunca más de 6 colores categóricos.
- Contraste: texto sobre franja de color en blanco; verificar legibilidad en el color de marca del cliente. Sin fondos ni bordes (todo transparente).

Tipografía (una sola familia, la de Tableau o la del cliente si la tiene):
- Número de tarjeta KPI: 28-32 pt en negrita, color primario o semáforo.
- Título de zona: 14-16 pt en negrita, blanco sobre franja. Subtítulo: 10-11 pt.
- Etiquetas de ejes y marcas: 9-10 pt (mínimo 8 en web). Delta de tarjeta: 10-11 pt.
- Tooltip: título 12-14 pt, valores 12 pt, secciones 10-11 pt.
- Valores marcados como "propuestos" hasta que el usuario los confirme en la primera revisión de cada cliente.

## Patrón del mapa de calor con selector de métrica
Parámetro de texto "Métrica del mapa de calor" (Gestiones, Contactos con titular, Promesas, Cuentas distintas, % contacto, % promesa, Monto recuperado). Un cálculo "Métrica seleccionada" (CASE sobre el parámetro) para el color y otro "Métrica (texto)" para la etiqueta que agrega % cuando la métrica es porcentual. Etiqueta mínima 8 pt en web.
```

---

## 3. dashboards-cobranza-kpis

```markdown
---
name: dashboards-cobranza-kpis
description: Tarjetas KPI con deltas y glosario de definiciones estándar de métricas de Cobranza BINATSA. Usar al crear tarjetas, calcular métricas o documentar cómo se calculan.
---

# KPIs · Dashboards de Cobranza BINATSA

## Tarjetas KPI
- Todas las vistas llevan tarjetas KPI con dos deltas: "vs periodo previo" (mismo rango anterior) y "vs 7 días previos", con ▲ verde / ▼ rojo (invertir color cuando bajar es bueno, ej. Sin gestión).
- Cada tarjeta debe ayudar a decidir. Descartar métricas descriptivas sin acción (día de mayor volumen, franja más cargada, pico de personas, peso fin de semana, días con operación). Preferir cobertura, % contacto titular, promesas, % promesa, $ recuperado, pagos, sin gestión, intentos por cuenta.

## Glosario de KPIs (definiciones estándar; confirmar con el cliente si difieren)
- Cuentas asignadas: cuentas en la base del periodo/segmento.
- Gestión / cuentas gestionadas: cuentas con al menos una gestión en el periodo. % gestión (o % cartera gestionada) = gestionadas ÷ asignadas. % sin gestión = 1 − % gestión.
- Intentos (de llamada): número de gestiones/llamadas realizadas. Intentos por cuenta gestionada = intentos ÷ cuentas gestionadas.
- Contacto con titular: gestiones cuyo interlocutor es el titular. % contacto = contactos con titular ÷ gestiones (confirmar si se mide sobre gestiones o sobre cuentas).
- Promesa de pago: gestiones con resultado de promesa. % promesa = promesas ÷ contactos con titular (confirmar base). Monto prometido = suma del monto de las promesas.
- Pago / pagos recibidos: número de pagos aplicados. $ recuperado = suma de pagos aplicados en el periodo.
- Periodo previo: rango inmediatamente anterior de la misma duración que el rango seleccionado.
- 7 días previos: el mismo rango desplazado 7 días atrás.
- Delta: variación relativa en % contra la referencia; para métricas que ya son porcentaje, diferencia en puntos porcentuales (pp).
- Documentar siempre la definición real usada en el tooltip "Cómo se calcula" y avisar al usuario si el cliente la define distinto.
```

---

## 4. dashboards-cobranza-tooltips

```markdown
---
name: dashboards-cobranza-tooltips
description: Formato estándar de descripciones emergentes (tooltips) con iconos para todas las hojas de dashboards de Cobranza BINATSA, incluido el XML de Tableau. Usar al crear o rehacer tooltips.
---

# Tooltips · Dashboards de Cobranza BINATSA

Obligatorios en todo gráfico y tarjeta. Estructura (referencia aprobada "Ventas que se siguen marcando"):
1. Título en negrita con color de acento (verde #2e7d32 o color de marca).
2. Datos: etiqueta normal + valor en negrita y más grande; valores dinámicos (hora, día, segmento, métrica).
3. Línea divisoria fina.
4. Tres secciones con "▸" en negrita y 1-3 líneas:
   - "🔎 QUÉ MIDE" (qué valor cuenta)
   - "🧮 CÓMO SE CALCULA" (fórmula en palabras, cómo se compone y se lee)
   - "🎯 PARA QUÉ SIRVE ESTA VISTA"
5. Colores por sección (QUÉ MIDE azul/oscuro, CÓMO SE CALCULA #b45f06, PARA QUÉ SIRVE #2e7d32); cuerpo en gris oscuro; iconos coherentes con el contenido.
6. Cuando hay filas por segmento de cartera, línea gris con la leyenda de rangos (ej. "A = 06-30 días · B = 31-60 · C = 61-90", según el cliente). Sin pie de campaña.

## En XML (.twb)
- `<customized-tooltip><formatted-text><run …>` dentro del pane de cada worksheet.
- Salto de línea = `<run>Æ&#10;</run>`.
- Campos dinámicos como runs CDATA `<[datasource].[campo]>`.
- Trabajar en copia del .twbx sobre el archivo que el usuario subió; reempaquetar con el .twb, Data/Extracts y Image intactos; el usuario publica.
```

---

## 5. dashboards-cobranza-cliente-limpieza

```markdown
---
name: dashboards-cobranza-cliente-limpieza
description: Configurar la vista que ve el cliente final y limpiar hojas, orígenes, cálculos y campos huérfanos de un workbook de Cobranza BINATSA sin tocar las consultas.
---

# Vista del cliente y limpieza · Dashboards de Cobranza BINATSA

## Vista del cliente
- Definir con el usuario qué vistas ve el cliente final (por ejemplo una vista de gestiones o resultados) y cuáles son solo internas.
- Las vistas internas y las hojas de trabajo van ocultas; el cliente solo ve lo que se le comparte.
- Dar permisos a nivel de vista/proyecto solo a esa vista (lo configura el usuario en Tableau Cloud; confirmar con él antes de compartir).
- Cuidar que la vista del cliente no muestre datos de otras campañas ni información interna (asesores, notas internas) salvo que el usuario lo pida.
- Probar la vista como la verá el cliente (filtros por defecto, sin marcas seleccionadas).

## Limpieza de huérfanos (cuando el usuario la pida)
1. Inventariar: hojas sin uso en ningún dashboard, orígenes de datos sin hojas, cálculos sin referencias, parámetros sin uso.
2. Cruzar referencias en el XML (.twb) antes de quitar; un cálculo puede usarse dentro de otro, en acciones, filtros o tooltips.
3. Ocultar hojas que el cliente no consulta (no borrar si hay duda); quitar solo lo confirmado sin referencias.
4. Campos: solo ocultar (hidden='true'), sin tocar consultas. No ocultar campos que el reporte usa o usará aunque hoy no tengan datos. Ocultar no reduce el tamaño del extracto.
5. Hacerlo en copia versionada, entregar un resumen de lo quitado/ocultado y que el usuario publique.
```

---

## 6. dashboards-cobranza-publicacion

```markdown
---
name: dashboards-cobranza-publicacion
description: Checklist previo a publicar, reglas de publicación en Tableau Cloud y monitoreo de la actualización del extracto para dashboards de Cobranza BINATSA.
---

# Publicación y monitoreo · Dashboards de Cobranza BINATSA

## Checklist antes de publicar
- [ ] Sin marcas seleccionadas y parámetros en su valor por defecto (en web quedan guardados en el borrador).
- [ ] Filtros y fechas por defecto correctos (segmento, Desde, Hasta).
- [ ] Todos los % con símbolo; dinero con $ y miles.
- [ ] Tooltips completos en todas las hojas.
- [ ] Tarjetas KPI con los dos deltas y color de ▲▼ correcto.
- [ ] Botones de navegación funcionan; logos BINATSA y cliente visibles.
- [ ] Todo transparente, sin bordes ni fondos; mosaico; tamaño automático.
- [ ] Filtros cruzados entre gráficos funcionan.
- [ ] Cifras cuadradas contra la fuente en al menos un caso de control.
- [ ] Publicar sobre el workbook existente; credenciales incrustadas (las pone el usuario desde Desktop).
- [ ] Después de publicar: vistas, fuentes, hora de Modificado y actualización de extracción OK.

## Publicación
- Publicar SOBRE el workbook existente (mismo nombre y proyecto) para conservar programación y credenciales; con otro nombre se pierde la programación.
- La contraseña incrustada solo se fija publicando desde Desktop con "Incrustar contraseña" (en web no hay campo). Las credenciales las captura siempre el usuario.

## Monitoreo de actualización
- Revisar en la pestaña Actualizaciones de la extracción del workbook: estado, hora de la última corrida y programación activa.
- Tras cada publicación, verificar que la programación sigue vigente y lanzar "Ejecutar ahora" para confirmar que corre sin error.
- Causas típicas de fallo: contraseña no incrustada (fallo en "Insertado"), credenciales vencidas, cambio en la fuente. 5 fallos seguidos suspenden la programación.
- Alertas: ofrecer automatizar el aviso al canal que el usuario elija (correo de Tableau al correo del canal de Slack u otro) y una tarea programada de revisión si lo pide; si se crea, usar las herramientas de tareas programadas, no cron local.
```

---

