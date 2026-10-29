---
name: dashboards-cobranza-kpis
description: Tarjetas KPI con deltas y glosario de definiciones estándar de métricas de Cobranza BINATSA. Usar al crear tarjetas, calcular métricas o documentar cómo se calculan.
---

# KPIs · Dashboards de Cobranza BINATSA

## Tarjetas KPI
- Todas las vistas llevan tarjetas KPI con dos deltas: "vs periodo previo" (mismo rango anterior) y "vs 7 días previos", con ▲ verde / ▼ rojo (invertir color cuando bajar es bueno, ej. Sin gestión). Excepción: cuando el rango seleccionado es de 7 días o menos, se oculta "vs 7 días previos" (coincide con el periodo previo o lo repite) y la tarjeta muestra solo "vs periodo previo". Con 8 días o más se muestran los dos.
- Cada tarjeta debe ayudar a decidir. Descartar métricas descriptivas sin acción (día de mayor volumen, franja más cargada, pico de personas, peso fin de semana, días con operación). Preferir cobertura, % contacto titular, promesas, % promesa, $ recuperado, pagos, sin gestión, intentos por cuenta.

## Anatomía de la tarjeta (propuesta, confirmar en la primera revisión de cada cliente)
De arriba hacia abajo. Todo va centrado excepto el título, que va a la izquierda:
1. Título de la tarjeta (nombre de la métrica): 10-11 pt, a la izquierda, sobre una franja de color de marca (en su tono oscuro si hace falta contraste, texto blanco) con esquinas redondeadas.
2. Número grande, centrado: 28-32 pt en negrita, en un tono del primario que llegue a 3:1 contra el fondo (en BINATSA, turquesa oscuro `#007F84`; el turquesa del logo no llega) o en color de semáforo si la tarjeta tiene meta. Formato de módulo estructura: % con símbolo y 1 decimal, dinero con $ y miles.
3. Dos deltas, centrados, en una línea o en dos: "▲ 4.2% vs periodo previo" y "▼ 1.1 pp vs 7 días previos", 10-11 pt, verde o rojo según sea mejor o peor. Con rango de 7 días o menos, solo el primero (ver Tarjetas KPI).
4. Solo el título lleva fondo (la franja) y esquinas redondeadas (radio propuesto: 12 px). El número y los deltas van SIN borde ni fondo, transparentes. En Tableau, la tarjeta son dos objetos apilados: el del título (caja de texto u hoja propia) con el radio de esquina, y la hoja del valor transparente. Aplicar el radio al objeto del título, no al contenedor que los envuelve (el contenedor no recorta a sus hijos). Requiere Tableau 2026.1 o posterior; revisar las exportaciones a PDF o imagen, que pueden mostrar las esquinas distinto.
5. Misma altura y ancho en toda la fila; máximo 5 tarjetas por fila.

## Glosario de KPIs (definiciones estándar; confirmar con el cliente si difieren)
Contacto, promesa y los demás resultados se identifican SIEMPRE por la tipificación que registra el historial de llamadas. Cada cliente nombra sus tipificaciones distinto: al iniciar, mapear cuáles cuentan como contacto con titular y cuáles como promesa, y confirmarlo con el usuario.
- Cuentas asignadas: cuentas en la base del periodo/segmento.
- Gestión / cuentas gestionadas: cuentas con al menos una gestión en el periodo. % gestión (o % cartera gestionada) = gestionadas ÷ asignadas. % sin gestión = 1 − % gestión.
- Intentos (de llamada): número de gestiones/llamadas realizadas. Intentos por cuenta gestionada = intentos ÷ cuentas gestionadas.
- Contacto con titular: gestiones cuya tipificación en el historial de llamadas indica que se habló con el titular. % contacto = contactos con titular ÷ gestiones totales del historial.
- Promesa de pago: gestiones cuya tipificación en el historial de llamadas es de promesa. % promesa = promesas ÷ contactos con titular. Monto prometido = suma del monto de las promesas.
- Pago / pagos recibidos: número de pagos aplicados. $ recuperado = suma de pagos aplicados en el periodo.
- Rango seleccionado: el definido por los parámetros de fecha [Desde] y [Hasta] (son parámetros, no filtros; ver dashboards-cobranza-estructura).
- Periodo previo: rango inmediatamente anterior de la misma duración que el rango seleccionado.
- 7 días previos: el mismo rango desplazado 7 días atrás. Solo se calcula y se muestra si el rango seleccionado dura más de 7 días; en Tableau, ocultar el delta con un cálculo que devuelva vacío cuando DATEDIFF('day', [Desde], [Hasta]) + 1 <= 7.
- Delta: variación relativa en % contra la referencia; para métricas que ya son porcentaje, diferencia en puntos porcentuales (pp).
- Documentar siempre la definición real usada en el tooltip "Cómo se calcula" y avisar al usuario si el cliente la define distinto.
