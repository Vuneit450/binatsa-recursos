---
name: dashboards-cobranza-kpis
description: Tarjetas KPI con deltas y glosario de definiciones estándar de métricas de Cobranza BINATSA. Usar al crear tarjetas, calcular métricas o documentar cómo se calculan.
---

# KPIs · Dashboards de Cobranza BINATSA

## Tarjetas KPI
- Todas las vistas llevan tarjetas KPI con dos deltas: "vs periodo previo" (mismo rango anterior) y "vs 7 días previos", con ▲ verde / ▼ rojo (invertir color cuando bajar es bueno, ej. Sin gestión).
- Cada tarjeta debe ayudar a decidir. Descartar métricas descriptivas sin acción (día de mayor volumen, franja más cargada, pico de personas, peso fin de semana, días con operación). Preferir cobertura, % contacto titular, promesas, % promesa, $ recuperado, pagos, sin gestión, intentos por cuenta.

## Anatomía de la tarjeta (propuesta, confirmar en la primera revisión de cada cliente)
De arriba hacia abajo, todo alineado a la izquierda:
1. Nombre de la métrica: 10-11 pt, texto secundario.
2. Número grande: 28-32 pt en negrita, color primario (o semáforo si la tarjeta tiene meta). Formato de módulo estructura: % con símbolo y 1 decimal, dinero con $ y miles.
3. Dos deltas en una línea o en dos: "▲ 4.2% vs periodo previo" y "▼ 1.1 pp vs 7 días previos", 10-11 pt, verde o rojo según sea mejor o peor.
4. Sin borde ni fondo. Misma altura y ancho en toda la fila; máximo 5 tarjetas por fila.

## Glosario de KPIs (definiciones estándar; confirmar con el cliente si difieren)
Contacto, promesa y los demás resultados se identifican SIEMPRE por la tipificación que registra el historial de llamadas. Cada cliente nombra sus tipificaciones distinto: al iniciar, mapear cuáles cuentan como contacto con titular y cuáles como promesa, y confirmarlo con el usuario.
- Cuentas asignadas: cuentas en la base del periodo/segmento.
- Gestión / cuentas gestionadas: cuentas con al menos una gestión en el periodo. % gestión (o % cartera gestionada) = gestionadas ÷ asignadas. % sin gestión = 1 − % gestión.
- Intentos (de llamada): número de gestiones/llamadas realizadas. Intentos por cuenta gestionada = intentos ÷ cuentas gestionadas.
- Contacto con titular: gestiones cuya tipificación en el historial de llamadas indica que se habló con el titular. % contacto = contactos con titular ÷ gestiones totales del historial.
- Promesa de pago: gestiones cuya tipificación en el historial de llamadas es de promesa. % promesa = promesas ÷ contactos con titular. Monto prometido = suma del monto de las promesas.
- Pago / pagos recibidos: número de pagos aplicados. $ recuperado = suma de pagos aplicados en el periodo.
- Periodo previo: rango inmediatamente anterior de la misma duración que el rango seleccionado.
- 7 días previos: el mismo rango desplazado 7 días atrás.
- Delta: variación relativa en % contra la referencia; para métricas que ya son porcentaje, diferencia en puntos porcentuales (pp).
- Documentar siempre la definición real usada en el tooltip "Cómo se calcula" y avisar al usuario si el cliente la define distinto.
