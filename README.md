# binatsa-recursos

Recursos de BINATSA para trabajar con Claude: logo, paleta y skills de dashboards de Cobranza en Tableau Cloud.

## Contenido

```
logos/
  binatsa.svg                 logo vectorial
  paleta-binatsa.md           colores derivados del logo, con contraste y rampa de segmentos
  Preferences-BINATSA.tps     paletas para cargar en Tableau Desktop
skills/
  dashboards-cobranza-base/            punto de partida: preguntas, reglas y flujo (usar primero)
  dashboards-cobranza-estructura/      vistas Dirección y Operación, layout, estilo
  dashboards-cobranza-kpis/            tarjetas KPI y glosario de métricas
  dashboards-cobranza-tooltips/        descripciones emergentes
  dashboards-cobranza-cliente-limpieza/  vista del cliente y limpieza de huérfanos
  dashboards-cobranza-publicacion/     checklist, publicación y monitoreo
  dashboards-cobranza-BINATSA.md       documento original con los 6 módulos juntos (respaldo)
```

## Cómo usar los skills

Cada carpeta de `skills/` tiene un `SKILL.md` independiente. El módulo `base` indica el orden: base, estructura, KPIs, tooltips, cliente y limpieza, publicación.

## Usar desde otra cuenta de Claude

El repositorio es público a propósito, para poder leerlo desde otras cuentas. Cada carpeta de `skills/` es un skill independiente que se puede copiar o subir a la otra cuenta. Como es público, nunca subir aquí credenciales ni datos de clientes: solo logos, paletas y procesos.

## Paleta en Tableau

Copiar `logos/Preferences-BINATSA.tps` a `Mi repositorio de Tableau/Preferencias/Preferences.tps` y reiniciar Tableau Desktop. Es el método de Desktop 2025.2 y anteriores; en 2026.1 puede no funcionar, y entonces se crean las paletas dentro de Tableau con los hex de `logos/paleta-binatsa.md`. Detalles ahí.

## Clientes

La carpeta `clientes/<cliente>/` (logo y paleta de cada cliente) se crea cuando hace falta, siguiendo el formato de `logos/paleta-binatsa.md`.
