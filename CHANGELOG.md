# Registro de cambios

## Sin publicar (rama `video-guia`)
- Módulo `dashboards-cobranza-video-guia`: video guía para un usuario nuevo, último paso de la entrega.
- Módulo `dashboards-cobranza-datos`: tablas mínimas, reglas de negocio, validación de cifras, rendimiento y seguridad por usuario.
- Estructura: vistas estándar (Guía de uso y Seguimiento), formato regional, estados vacíos, cuándo usar cada gráfico y dispositivos.
- Publicación: mantenimiento después de la entrega.
- Carpeta `ejemplos/` (aún sin imágenes).
- Se eliminó `archivo/` (el borrador original queda solo en el historial de Git).
- Las metas y el límite de hojas no son parte del estándar: las metas se preguntan por proyecto y no hay límite de hojas.

## Sin publicar
- Libro de prueba con datos inventados (`ejemplos/libro-prueba/prueba_publicacion.twbx`) y su generador `herramientas/crear_libro_prueba.py`, para la primera prueba de publicación. Aún no abierto en Tableau.
- Carpeta `herramientas/`: script de publicación con token (`publicar_libro.py`, no probado contra un sitio real), preparación paso a paso y cómo aplicar en Tableau lo que el XML no puede.
- Plantillas `brief.md` y `diccionario-datos.md` en `clientes/_plantilla/`.
- Módulo base: preguntas reordenadas en tres tandas (se agregan las vistas y el nombre del cliente, y las metas pasan a su propia pregunta), flujo de trabajo con una secuencia explícita de construcción y nueva sección "Trabajo con una carpeta local".
- Módulo de datos: "Primer acercamiento a los datos".
- Video: dónde se guardan el motor, las versiones y el guion (carpeta `video/` del cliente), y qué hacer si la sesión no tiene acceso a la carpeta.
- Módulo base: regla de permisos mínimos y datos sensibles (usuario dedicado, acceso mínimo, nunca borrar, datos agregados, política y vida del token).
- Módulo base: herramientas de Tableau para trabajar sin pasar por la web (servidor MCP, tableauserverclient, API de Hyper y navegador), por validar.
- Publicación por la sesión con un token que el usuario configura; el ciclo termina al cumplir el checklist, con un tope de 5 vueltas y confirmación antes de tocar producción.
- Módulo de video: nueva sección "Composición del cuadro" (marco estándar de 1664 x 976 px, simulación de monitor chico en réplicas, franja de texto abajo, cámara y zoom, barrido único en elementos anchos, regla para no repetir gráficos, escena de arranque y prueba de cuadros a 3840 x 2160).
- Alineado con el libro de referencia más reciente: tamaño fijo de 1910 x 1300 px en todas las vistas, ícono del cliente y logo de BINATSA, botones "Ir a <Vista> →" de 164 x 36 px con color por destino, tarjetas KPI de 271 x 190 px, tooltips de cinco secciones, parámetro Periodo y formato de título "Cobranza <Cliente> · <Vista>".
- Los deltas sin periodo previo muestran "-", no "+0.0 %".
- La prohibición de nombres técnicos, "Excel" y sistemas internos se extiende al texto visible del dashboard, no solo al video.
- Botones de navegación pegados a la izquierda; número de tarjeta KPI de 28 pt; los colores de canales los define el proyecto; Periodo con "Año actual" por defecto.
- Módulo de video revisado: filtros con Periodo, tooltip de cinco secciones, botones, colores iguales a los del tablero real y cómo mostrar un tablero de 1910 x 1300 px en 16:9.
- Carpeta `ejemplos/` con 9 ilustraciones de datos inventados que reproducen el estilo de referencia.
- El símbolo de "sin dato" es el mismo en todo el skill: "-" (guion corto), en tarjetas, deltas y tablas.
- Encabezado con una franja de fondo completo y esquina recta; los filtros y parámetros no llevan fondo ni borde propios. Un 0 real en una tarjeta se muestra como 0.
- Video: capturas HD hechas con código; cada segmentador se demuestra con el antes y el después de un solo cambio, como recorrido de cómo manejar el tablero.
- Etiquetas de valor: los valores 0 o nulos no muestran etiqueta en los gráficos, para no saturar, y en las tablas se muestran como "-".
- Esquinas redondeadas en todos los títulos con fondo (gráficos, tablas y tarjetas KPI); el resto, transparente y sin borde.
- La escala de color del mapa de calor la define el proyecto y el número de cada celda debe contrastar.

## 29 de octubre de 2026
- Skill dividido en 6 módulos independientes (base, estructura, KPIs, tooltips, cliente y limpieza, publicación).
- Paleta de BINATSA derivada del logo, con contraste verificado, y paletas para Tableau.
- Carpeta `clientes/` con plantilla.
- Reglas de diseño acordadas: tamaños por vista, bordes y fondos solo en títulos y botones, todo centrado menos los títulos, sin líneas de fondo ni título del segundo eje, familia Tableau, medidas estándar y comunicación entre gráficos.
- Tarjeta de cierre de los videos (`logos/cierre-video.png`).
- El borrador original se conservó un tiempo como obsoleto (después se eliminó).
