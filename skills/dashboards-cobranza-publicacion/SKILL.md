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
- [ ] Tarjetas KPI con los dos deltas y color de ▲▼ correcto (con rango de 7 días o menos, solo "vs periodo previo"; probar con un rango corto y uno largo).
- [ ] Botones de navegación funcionan; logos BINATSA y cliente visibles.
- [ ] Todo transparente, sin bordes ni fondos (excepto tarjetas KPI: borde fino y esquinas redondeadas); mosaico.
- [ ] Tamaño en "Rango", altura mínima 1300 px.
- [ ] Prueba de interacción hecha (ver sección siguiente) y reportada.
- [ ] Cifras cuadradas contra la fuente en al menos un caso de control.
- [ ] Publicar sobre el workbook existente; credenciales incrustadas (las pone el usuario desde Desktop).
- [ ] Después de publicar: vistas, fuentes, hora de Modificado y actualización de extracción OK.

## Prueba de interacción (obligatoria)
Todos los gráficos deben interactuar entre sí. No darlo por hecho: probarlo en el dashboard abierto en el navegador, en las dos vistas (Dirección y Operación).
1. Hacer una lista de las hojas visibles del dashboard (gráficos, tablas y tarjetas KPI).
2. Por cada gráfico, hacer clic en una marca y comprobar que se actualizan TODAS las demás hojas, incluidas las tarjetas KPI. Anotar cuáles no respondieron.
3. Limpiar la selección (clic fuera de las marcas) y comprobar que todo vuelve al estado inicial.
4. Corregir lo que no responda (dimensión de enlace faltante, acción mal configurada) y repetir desde el paso 2.
5. Reportar al usuario en una tabla corta: hoja, ¿filtra a las demás?, ¿responde a las demás?. No publicar con huecos sin que el usuario los apruebe.
6. Dejar el dashboard sin marcas seleccionadas antes de publicar.

## Publicación
- Publicar SOBRE el workbook existente (mismo nombre y proyecto) para conservar programación y credenciales; con otro nombre se pierde la programación.
- La contraseña incrustada solo se fija publicando desde Desktop con "Incrustar contraseña" (en web no hay campo). Las credenciales las captura siempre el usuario.

## Monitoreo de actualización
- Revisar en la pestaña Actualizaciones de la extracción del workbook: estado, hora de la última corrida y programación activa.
- Tras cada publicación, verificar que la programación sigue vigente y lanzar "Ejecutar ahora" para confirmar que corre sin error.
- Causas típicas de fallo: contraseña no incrustada (fallo en "Insertado"), credenciales vencidas, cambio en la fuente. 5 fallos seguidos suspenden la programación.
- Alertas: ofrecer automatizar el aviso al canal que el usuario elija (correo de Tableau al correo del canal de Slack u otro) y una tarea programada de revisión si lo pide; si se crea, usar las herramientas de tareas programadas, no cron local.
