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
