---
name: dashboards-cobranza-base
description: "Punto de partida para cualquier dashboard de Cobranza BINATSA en Tableau Cloud: preguntas iniciales, recursos, reglas generales y flujo de trabajo. Usar primero; luego los módulos de estructura, KPIs, tooltips, cliente/limpieza y publicación."
---

# Base · Dashboards de Cobranza BINATSA

Responde siempre en español, corto y directo. Quien usa este skill es del equipo de BINATSA; no asumir quién es.
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
  - logos/paleta-binatsa.md y logos/Preferences-BINATSA.tps: paleta de BINATSA (derivada del logo) y su versión para cargar en Tableau.
  - clientes/<cliente>/: logo y recursos de marca de cada cliente (ver clientes/README.md y clientes/_plantilla/). Si no hay carpeta del cliente, pedir el logo y los colores y, con permiso del usuario, crearla a partir de la plantilla. El repositorio es público: subir solo el logo y los colores de marca, nunca datos internos.
  - Si el repositorio no está conectado a la sesión, leerlo desde el navegador o pedir el archivo.
- Los archivos no se guardan en la skill; solo la ruta.

## Preguntas obligatorias al iniciar un proyecto nuevo
Hacerlas con la herramienta de preguntas de opción múltiple si existe (en Claude Code, AskUserQuestion); si no, en texto con opciones numeradas. Cada tanda tiene máximo 4 preguntas, ofreciendo opciones concretas y una recomendada. No empezar a construir hasta tener las bloqueantes (1, 2 y 3). Si el usuario ya las respondió en el chat, no repetirlas. Si la sesión es desatendida, elegir lo razonable, declararlo arriba y marcarlo "por confirmar".

Tanda 1 (bloqueantes):
1. Logo del cliente: opciones "Lo subo ahora", "Está en el repositorio (clientes/<cliente>/)", "No hay logo: usar solo texto con sus colores". Siempre confirmarlo, aunque ya exista en el repositorio.
2. Colores de marca del cliente: "Los paso (hex)", "Sácalos del logo", "Usa la paleta BINATSA por ahora". La paleta de encabezados, acentos y KPIs sale de aquí.
3. Fuente de datos: "Tabla/consulta existente", "Archivo (CSV/Excel)", "Aún no hay: usar datos de ejemplo del kit". Confirmar campos disponibles: canales (llamadas, SMS, Mail, Blaster, WhatsApp, Visitas, Predictivo, Inbound), tipificaciones, asesor, zona, monto, promesas, pagos.
4. Tarjetas KPI de Dirección y de Operación (no bloqueante): opciones "Las propuestas del skill", "Las que defina el cliente", "Propongo yo según los campos disponibles". Recomendada: las propuestas del skill, ajustadas al proyecto.

Tanda 2 (antes de publicar):
5. Segmentación de cartera del cliente (buckets/rangos de mora, nombres y días). No asumir A/B/C.
6. Workbook, proyecto y sitio de Tableau Cloud (publicar siempre sobre el workbook existente cuando ya hay uno).
7. Horario, frecuencia y zona horaria de actualización del extracto.
8. Canal de alertas de fallo de actualización: opciones "Slack (¿cuál canal?)", "Correo", "Otro", "Sin alertas". Nunca asumir uno.

Tanda 3 (antes de compartir con el cliente):
9. Quiénes tienen acceso. Por defecto el cliente ve las dos vistas (Dirección y Operación), con el desglose por asesor.

## Reglas generales (Tableau Cloud)
1. NUNCA mover ni modificar consultas/fuentes. Solo ocultar campos huérfanos que ningún reporte use ni vaya a usar.
2. Las credenciales las captura SIEMPRE el usuario; nunca escribir contraseñas.
3. Publicar SOBRE el workbook existente (mismo nombre y proyecto) para conservar programación y credenciales; con otro nombre se pierde la programación.
4. Edición web: autoguardado como "Borrador"; Publicar sobrescribe. Arrastrar anchos de columna no funciona. Hojas ocultas se abren desde el icono "Ir a hoja" de la zona del dashboard.
5. Alertas de fallo: canal elegido por el usuario para cada proyecto; lo configura el usuario en Tableau.

## Flujo de trabajo
1. Hacer las preguntas iniciales. Si el usuario sube un .twbx, trabajar sobre ESE archivo.
2. Cambios de XML (tooltips, campos ocultos): trabajar en copia versionada del .twbx (.twb + Data/Extracts/*.hyper + Image/), con nombre versionado; el usuario publica.
3. Cambios simples: edición web sin marcas seleccionadas y publicar sobre el mismo workbook.
4. Para revisar dashboards publicados: usar el navegador (Claude in Chrome o el integrado con sesión del usuario); si pide contraseña, que el usuario inicie sesión.
5. Correr el checklist de publicación, incluida la prueba de que todos los gráficos interactúan entre sí; verificar y reportar en 1-2 frases más la tabla de interacción.
