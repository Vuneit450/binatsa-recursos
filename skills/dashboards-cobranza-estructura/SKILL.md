---
name: dashboards-cobranza-estructura
description: Estructura estándar (Dirección y Operación), layout, interactividad y estilo visual de dashboards de Cobranza BINATSA en Tableau Cloud. Usar al diseñar o modificar vistas.
---

# Estructura y estilo · Dashboards de Cobranza BINATSA

## Estructura estándar
Como mínimo dos vistas, Dirección y Operación; el proyecto puede agregar más (por ejemplo un tablero Daily o un detalle de gestiones). Todas llevan el título principal, el logo de BINATSA y los botones de navegación hacia las demás vistas, con el mismo formato.

### Logo
Solo el logo de BINATSA (`logos/binatsa.svg`; en PNG si Tableau no acepta SVG), arriba a la derecha, en la misma fila del título principal y pegado a la esquina superior derecha. Unos 250 px de ancho (el PNG de referencia mide 250 x 46 px; con el margen del objeto ocupa unos 268 px), alto proporcional sin deformar, y en la misma posición en todas las vistas. El logo del cliente no va en el dashboard salvo que se pida: se usa para sacar su paleta.

### Título principal del dashboard
Texto de 20 pt en negrita, color blanco, sobre una franja de color de marca (en su tono oscuro, ver Contraste), con un emoji al inicio y sin borde. Arriba a la izquierda, como todo título. Es el texto más grande del dashboard: los títulos de zona (14-16 pt) quedan por debajo.

### Botones de navegación
Objeto Botón de navegación de tipo texto, uno por vista de destino:
- Ancho fijo de 165 px; alto de 40 px (propuesto: en los tableros de referencia varía de 32 a 65 px porque se dimensiona en porcentaje; fijarlo en píxeles evita que cambie con el alto del dashboard).
- Fuente Tableau Bold de 11 pt, texto blanco.
- Fondo en el tono oscuro del color primario del cliente (el mismo de las franjas), sin borde.
- Texto del botón: emoji + nombre de la vista, por ejemplo "📊 Dirección" y "⚙️ Operación", sin flechas.
- Todos los botones de la fila con el mismo tamaño y separados por un espacio igual; la fila va centrada, bajo el título principal.

### Dirección (¿cómo va la campaña?)
- KPIs generales: monto recuperado, pagos, promesas, % cartera gestionada, % contacto titular.
- Otros canales si existen: datos propios por canal en un gráfico comparativo (contactos, promesas, efectividad).
- Intensidad de base por segmento de cartera (asignadas, gestionadas, sin gestión, intentos por cuenta).
- Mapa de visitas por zona: de dónde salen más promesas y recuperación (zona/colonia/municipio/estado según el campo disponible).
- Tendencia día a día de promesas y recuperación.

### Operación (¿qué hay que corregir hoy?) — siempre estas 3 piezas
1. Mapa de calor día × franja horaria con segmentador (parámetro "Métrica") para: Gestiones, Contactos con titular, Promesas, Cuentas distintas, % contacto, % promesa, Monto recuperado (ver el patrón al final).
2. Tipificaciones ordenadas DESC (a dónde se va el mayor flujo).
3. Asesores (SIEMPRE presente y visible para el cliente): cuentas asignadas, gestiones totales, % promesado, monto recuperado.

Tarjetas KPI de Operación: Operación también lleva tarjetas, las que correspondan al proyecto. Se eligen con el usuario al iniciar; criterio: que ayuden a decidir qué corregir hoy (por ejemplo gestiones, % contacto titular, promesas, % promesa, sin gestión, intentos por cuenta). Misma anatomía y reglas que las de Dirección.

Layout de referencia de Operación (dos columnas bajo las tarjetas KPI; cada bloque con franja de encabezado emoji + pregunta + subtítulo):
- Fila 1: "¿En qué horas contestan los titulares?" (mapa de calor + selector de Métrica) | "¿Quién produce y quién necesita apoyo?" (tabla por asesor).
- Fila 2: "¿Qué está pasando en las llamadas?" (tipificaciones DESC apiladas por segmento) | "¿A qué horas se trabaja más?" (barras por hora apiladas por segmento).
- Fila 3: "¿Qué segmento tiene más cuentas sin tocar?" (pastel) | "Visitas por resultado" (barras apiladas).
- Pie: texto "Cómo leer" con la aclaración de fuentes.

## Layout
- Todo en contenedores en MOSAICO (no flotante).
- Tamaño (como en los tableros de referencia): Dirección en tamaño Automático. Operación en "Rango" definido solo con mínimos y sin máximos: alto mínimo 1800 px y ancho mínimo 1400 px; sin máximo, se estira en pantallas muy grandes y crece en alto si la ventana es más alta. Las vistas adicionales (por ejemplo un Daily) usan las medidas que se definan con el usuario.
- La información no lleva borde ni color de fondo: todo transparente (gráficos, números de tarjetas KPI, filtros, parámetros, hojas y contenedores). Los ÚNICOS elementos que pueden llevar fondo o borde son los títulos (título principal, encabezados de zona, títulos de gráficos y de tarjetas KPI: franja de color de marca; en las tarjetas, con esquinas redondeadas, ver dashboards-cobranza-kpis) y los botones de navegación (fondo de color de marca).
- Todo va centrado (gráficos y tablas dentro de su zona, el contenido de las tablas, números y deltas de las tarjetas, filtros, parámetros, botones de navegación, texto "Cómo leer") EXCEPTO los títulos, que van alineados a la izquierda: títulos de gráficos, títulos de tablas y encabezados de zona.

## Interactividad
- La mayoría de los gráficos se comunican entre sí: clic en una marca filtra los demás. Cuáles quedan fuera depende del proyecto (por ejemplo, un gráfico con otra fuente de datos o sin campos en común) y se declaran en el reporte con el motivo. Las tarjetas KPI son destino, no origen.
- Patrón de comunicación de referencia (tomado de los tableros de referencia; no es exacto, cada proyecto lo adapta):
  - Cada gráfico o tabla es origen de una acción de filtro al seleccionar, con "todos los campos" que comparte con las demás hojas, y todas las demás hojas del dashboard como destino.
  - Las tarjetas KPI nunca son origen; solo reciben.
  - Orígenes típicos en Dirección: segmento, tendencia día a día, canal y promesas por día. En Operación: horas, asesores, resultados o tipificaciones, cobertura por segmento, sin gestión, gestiones por hora y visitas.
  - Se excluye como destino la hoja que viene de otra fuente de datos (por ejemplo, una encuesta que no comparte campos con las llamadas).
  - Clic en un segmento: además del filtro, una acción de parámetro llena el parámetro "Segmento", para que lo que depende del segmento elegido (tarjetas, métricas) se adapte.
  - Al pasar el mouse sobre un segmento se resalta ese segmento en todas las hojas (acción de resaltar al pasar el mouse, a nivel del dashboard).
- Implementación en las tarjetas KPI: los periodos se calculan con banderas por fila a partir de los parámetros de fecha (ver dashboards-cobranza-kpis) y cada KPI se calcula una vez por periodo con IF bandera THEN medida END. Así las tarjetas son destino normal de las acciones de filtro de segmento, asesor, canal, hora, tipificación y zona: esos filtros no tocan las fechas y el periodo previo sigue disponible, de modo que los deltas siguen la selección. La fecha es la excepción: si un clic filtrara por día, desaparecerían las filas de los demás periodos. Por eso el día NO va en una acción de filtro: un clic en un día dispara una acción de parámetro que llena "Día seleccionado" (fecha) y todo el dashboard usa [Desde efectivo] y [Hasta efectivo]. La parte del día seleccionado es un patrón propuesto: validarlo en el primer dashboard de cada cliente.
- La verificación obligatoria está en dashboards-cobranza-publicacion (Prueba de interacción).
- Preferir tipos de gráfico que admitan segmentador/parámetro.
- Controles globales arriba: segmento (filtro) y Desde / Hasta (PARÁMETROS de fecha, no filtros: Tableau no permite leer el valor de un filtro dentro de un cálculo, y los deltas y el periodo previo lo necesitan). Un campo calculado "En rango" (fecha entre [Desde efectivo] y [Hasta efectivo]) va en los filtros de cada hoja, con valor Verdadero. Enlace "Guía de uso".
- En edición web NO dejar marcas seleccionadas ni parámetros cambiados antes de publicar.

## Parámetros estándar
Mismos nombres en todos los proyectos, en español y sin pistas entre paréntesis (la explicación va en la "Guía de uso"):
- Desde (fecha): por defecto sin límite (2000-01-01).
- Hasta (fecha): por defecto hoy; no puede pasar de hoy.
- Día seleccionado (fecha): vacío por defecto; lo llena la acción de parámetro al hacer clic en un día.
- Segmento (lista): valor por defecto "Todos"; las opciones son los segmentos de cartera del cliente.
- Métrica del mapa de calor (lista): ver el patrón del mapa de calor.
Cualquier otro parámetro lo define el proyecto, con nombre en español y sin pistas entre paréntesis. Los cálculos que derivan de estos (Desde efectivo, Hasta efectivo, banderas de periodo) se nombran igual en todos los proyectos.

## Estilo visual
- Encabezados de zona: franja de color de marca (en su tono oscuro si hace falta, ver Contraste), título blanco con emoji coherente + subtítulo de una línea con la pregunta de negocio.
- KPIs grandes con número en color (adaptar a la marca del cliente).
- Todo porcentaje con símbolo % (1 decimal). Dinero con $ y miles; M/K en cifras grandes. Si el % se corta en celdas angostas (p. ej. mapa de calor dentro del tablero), avisar y proponer sin decimales o ensanchar; nunca dejar el número sin %.
- Barras de un solo color: resaltar la más alta (acento) con su número arriba, resto neutro. Barras apiladas por segmento usan el paso que le toca a cada segmento en la rampa de segmentos (ver Paleta): la rampa es la jerarquía de mora y es la misma en todas las hojas.
- Sin ruido: nada de gráficos huérfanos, hojas visibles que el cliente no consulta (ocultas; acceso por "Ir a hoja"), ni calculados sin uso.
- Nombres de hojas: sin estándar; cada proyecto usa los suyos. Los parámetros sí son estándar (ver Parámetros estándar).
- Ningún gráfico lleva líneas de fondo: quitar la cuadrícula, las líneas de cero, las líneas de referencia sin uso y las divisiones de fila y columna. Como la cuadrícula ya no ayuda a leer los valores, mostrar la etiqueta del valor en las marcas donde haga falta (en las barras, el número arriba, como ya pide la regla de la barra destacada).
- Ningún gráfico muestra el título del segundo eje (en gráficos de doble eje). Lo que mide el segundo eje se explica en el subtítulo de la zona y en el tooltip "Cómo se calcula".

## Paleta y tipografía
Paleta de BINATSA (y modelo de cómo documentar la de un cliente): `logos/paleta-binatsa.md`. Para cargarla en Tableau: ver la sección "Para Tableau" de ese mismo documento (el método depende de la versión).

Paleta (derivarla de los colores del cliente; si solo hay logo, extraer 2 colores dominantes):
- Primario del cliente: encabezados de zona, selección y barra destacada (la más alta).
- Secundario del cliente: acentos y líneas.
- Neutro: barras no destacadas y texto secundario en gris con matiz hacia el primario (no gris puro). Texto principal casi negro, nunca #000 puro.
- Semáforo fijo, independiente de la marca: verde #2e7d32 (mejora), rojo #c62828 (empeora), ámbar #C77700 (alerta; en texto pequeño usar #9A5A00 para que se lea). Invertir cuando bajar es bueno. Nunca usar el color como única señal: acompañarlo siempre con ▲ / ▼ o con texto.
- Segmentos de cartera: una rampa del primario del cliente de claro a oscuro (menos mora = más claro); mismo color por segmento en TODAS las hojas. Todos los pasos deben llegar a 3:1 de contraste contra el fondo (el paso más claro no puede ser un tono pastel). Nunca más de 6 colores categóricos.
- Contraste: texto blanco sobre franja de color solo si el contraste es de al menos 4.5:1. Si el primario del cliente no llega (el turquesa de BINATSA da 2.6:1), usar su tono oscuro para la franja (en BINATSA, turquesa oscuro `#007F84`) y reservar el color claro del logo para acento decorativo. Toda barra, línea o número de color debe llegar a 3:1 contra el fondo; si el color de marca no llega (el turquesa del logo da 2.6:1), usar su tono oscuro. Sin fondos ni bordes en la información (todo transparente); solo los títulos y los botones de navegación pueden llevarlos.

Tipografía: familia Tableau en todos los proyectos (no usar la tipografía del cliente). Se juega con los pesos, no con otras familias:
- Tableau Bold: título principal, número de tarjeta KPI, valores en negrita (tooltips) y botones.
- Tableau Semibold: títulos de zona y de tarjeta, encabezados de tabla y textos destacados.
- Tableau Medium: etiquetas de ejes y marcas.
- Tableau Light: subtítulos.
- Tableau Book: cuerpo de texto y tooltips.
Tamaños:
- Número de tarjeta KPI: 28-32 pt en negrita, en un tono del primario que llegue a 3:1 contra el fondo (en BINATSA, turquesa oscuro `#007F84`) o en color de semáforo.
- Título principal del dashboard: 20 pt en negrita, blanco sobre franja.
- Título de zona: 14-16 pt en negrita, blanco sobre franja. Subtítulo: 10-11 pt.
- Título de tarjeta KPI: 13 pt en negrita; subtítulo opcional de 10 pt.
- Botón de navegación: Tableau Bold 11 pt, blanco sobre el color de marca.
- Etiquetas de ejes y marcas: 9-10 pt (mínimo 8 en web). Delta de tarjeta: 10-11 pt.
- Tooltip: título 12 pt, valores 12 pt, secciones 10 pt.
- Valores marcados como "propuestos" hasta que el usuario los confirme en la primera revisión de cada cliente.

## Patrón del mapa de calor con selector de métrica
Parámetro de texto "Métrica del mapa de calor" (Gestiones, Contactos con titular, Promesas, Cuentas distintas, % contacto, % promesa, Monto recuperado). Un cálculo "Métrica seleccionada" (CASE sobre el parámetro) para el color y otro "Métrica (texto)" para la etiqueta que agrega % cuando la métrica es porcentual. Etiqueta mínima 8 pt en web.
