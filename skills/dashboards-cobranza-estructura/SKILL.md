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
- Tamaño: opción "Rango" (no Automático, que no permite fijar altura). Alto: 1300 px (mínimo y máximo). Ancho: automático, que se estira en pantallas muy grandes; propuesto mínimo 1200 px y máximo 3840 px (confirmar en la primera revisión de cada cliente).
- La información no lleva borde ni color de fondo: todo transparente (gráficos, números de tarjetas KPI, filtros, parámetros, hojas y contenedores). Los ÚNICOS elementos que pueden llevar fondo o borde son los títulos: encabezados de zona, títulos de gráficos y títulos de tarjetas KPI (franja de color de marca; en las tarjetas, con esquinas redondeadas, ver dashboards-cobranza-kpis).
- Todo va centrado (gráficos y tablas dentro de su zona, el contenido de las tablas, números y deltas de las tarjetas, filtros, parámetros, botones de navegación, texto "Cómo leer") EXCEPTO los títulos, que van alineados a la izquierda: títulos de gráficos, títulos de tablas y encabezados de zona.

## Interactividad
- TODOS los gráficos interactúan entre sí, sin excepciones salvo que el usuario la apruebe y quede declarada en el reporte: clic en una marca filtra los demás (acciones de filtro de dashboard; segmento, asesor, canal, hora, día, tipificación y zona como dimensiones de enlace). Los gráficos son origen y destino; las tarjetas KPI también responden a toda selección, pero por acciones de parámetro (ver Implementación).
- Implementación entre gráficos: una acción de filtro con origen y destino en todos los gráficos, al seleccionar. Si una hoja no comparte la dimensión de enlace, agregarla o crear una acción para esa pareja.
- Implementación en las tarjetas KPI (patrón propuesto; validar en el primer dashboard de cada cliente): los deltas siguen la selección, y una acción de filtro quita del KPI las filas del periodo previo (y un cálculo FIXED ignora ese filtro). Por eso las tarjetas NO son destino de las acciones de filtro: cada clic en un gráfico dispara además acciones de parámetro que llenan parámetros de selección ("Día seleccionado" de fecha, y uno de texto por dimensión: segmento, asesor, canal, hora, tipificación, zona; valor por defecto "Todos"). Los cálculos del KPI, del periodo actual y del previo, usan los mismos parámetros, así la selección se aplica a los dos periodos. Detalle de los rangos en dashboards-cobranza-kpis.
- La verificación obligatoria está en dashboards-cobranza-publicacion (Prueba de interacción).
- Preferir tipos de gráfico que admitan segmentador/parámetro.
- Controles globales arriba: segmento (filtro) y Desde / Hasta (PARÁMETROS de fecha, no filtros: Tableau no permite leer el valor de un filtro dentro de un cálculo, y los deltas, el periodo previo y la regla de 7 días lo necesitan). Un campo calculado "En rango" (fecha entre [Desde] y [Hasta]) va en los filtros de cada hoja, con valor Verdadero. Enlace "Guía de uso".
- En edición web NO dejar marcas seleccionadas ni parámetros cambiados antes de publicar.

## Estilo visual
- Encabezados de zona: franja de color de marca (en su tono oscuro si hace falta, ver Contraste), título blanco con emoji coherente + subtítulo de una línea con la pregunta de negocio.
- KPIs grandes con número en color (adaptar a la marca del cliente).
- Todo porcentaje con símbolo % (1 decimal). Dinero con $ y miles; M/K en cifras grandes. Si el % se corta en celdas angostas (p. ej. mapa de calor dentro del tablero), avisar y proponer sin decimales o ensanchar; nunca dejar el número sin %.
- Barras de un solo color: resaltar la más alta (acento) con su número arriba, resto neutro. Barras apiladas por segmento usan el paso que le toca a cada segmento en la rampa de segmentos (ver Paleta): la rampa es la jerarquía de mora y es la misma en todas las hojas.
- Sin ruido: nada de gráficos huérfanos, hojas visibles que el cliente no consulta (ocultas; acceso por "Ir a hoja"), ni calculados sin uso.

## Paleta y tipografía
Paleta de BINATSA (y modelo de cómo documentar la de un cliente): `logos/paleta-binatsa.md`. Para cargarla en Tableau: ver la sección "Para Tableau" de ese mismo documento (el método depende de la versión).

Paleta (derivarla de los colores del cliente; si solo hay logo, extraer 2 colores dominantes):
- Primario del cliente: encabezados de zona, selección y barra destacada (la más alta).
- Secundario del cliente: acentos y líneas.
- Neutro: barras no destacadas y texto secundario en gris con matiz hacia el primario (no gris puro). Texto principal casi negro, nunca #000 puro.
- Semáforo fijo, independiente de la marca: verde #2e7d32 (mejora), rojo #c62828 (empeora), ámbar #C77700 (alerta; en texto pequeño usar #9A5A00 para que se lea). Invertir cuando bajar es bueno. Nunca usar el color como única señal: acompañarlo siempre con ▲ / ▼ o con texto.
- Segmentos de cartera: una rampa del primario del cliente de claro a oscuro (menos mora = más claro); mismo color por segmento en TODAS las hojas. Todos los pasos deben llegar a 3:1 de contraste contra el fondo (el paso más claro no puede ser un tono pastel). Nunca más de 6 colores categóricos.
- Contraste: texto blanco sobre franja de color solo si el contraste es de al menos 4.5:1. Si el primario del cliente no llega (el turquesa de BINATSA da 2.6:1), usar su tono oscuro para la franja (en BINATSA, turquesa oscuro `#007F84`) y reservar el color claro del logo para acento decorativo. Toda barra, línea o número de color debe llegar a 3:1 contra el fondo; si el color de marca no llega (el turquesa del logo da 2.6:1), usar su tono oscuro. Sin fondos ni bordes en la información (todo transparente); solo los títulos pueden llevarlos.

Tipografía (una sola familia, la de Tableau o la del cliente si la tiene):
- Número de tarjeta KPI: 28-32 pt en negrita, en un tono del primario que llegue a 3:1 contra el fondo (en BINATSA, turquesa oscuro `#007F84`) o en color de semáforo.
- Título de zona: 14-16 pt en negrita, blanco sobre franja. Subtítulo: 10-11 pt.
- Etiquetas de ejes y marcas: 9-10 pt (mínimo 8 en web). Delta de tarjeta: 10-11 pt.
- Tooltip: título 12-14 pt, valores 12 pt, secciones 10-11 pt.
- Valores marcados como "propuestos" hasta que el usuario los confirme en la primera revisión de cada cliente.

## Patrón del mapa de calor con selector de métrica
Parámetro de texto "Métrica del mapa de calor" (Gestiones, Contactos con titular, Promesas, Cuentas distintas, % contacto, % promesa, Monto recuperado). Un cálculo "Métrica seleccionada" (CASE sobre el parámetro) para el color y otro "Métrica (texto)" para la etiqueta que agrega % cuando la métrica es porcentual. Etiqueta mínima 8 pt en web.
