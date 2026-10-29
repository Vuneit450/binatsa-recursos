# Paleta BINATSA

Sale de los dos colores del logo (`logos/binatsa.svg`). Lo demás son derivados.

## Colores de marca

| Nombre | Hex | Uso |
|---|---|---|
| Azul marino | `#0B1F3A` | Franjas de encabezado de zona (título blanco), texto de marca, barra o segmento más oscuro |
| Turquesa | `#00B3B8` | Acento: barra destacada (la más alta), líneas, selección, bordes de foco |
| Turquesa oscuro | `#007F84` | Turquesa cuando va con texto blanco encima o como texto sobre fondo claro |

## Neutros (con matiz hacia el azul marino, no gris puro)

| Nombre | Hex | Uso |
|---|---|---|
| Texto principal | `#14202E` | Casi negro, nunca `#000000` |
| Texto secundario | `#55657A` | Subtítulos, etiquetas de ejes |
| Barras no destacadas | `#B4BFCB` | Todas las barras menos la destacada |

Fondos: todo transparente (regla del módulo de estructura).

## Rampa de segmentos de cartera (menos mora = más claro)

Un solo color por segmento, igual en TODAS las hojas. Máximo 6 pasos; esta rampa tiene 5.

| Paso | Hex | Para |
|---|---|---|
| 1 (más claro) | `#B8EBED` | Segmento con menos mora |
| 2 | `#5CD0D4` | |
| 3 | `#00B3B8` | |
| 4 | `#007F84` | |
| 5 (más oscuro) | `#0B1F3A` | Segmento con más mora |

Si el cliente tiene menos segmentos, tomar pasos salteados (por ejemplo 3 segmentos: 1, 3 y 5).

## Semáforo (fijo, no depende de la marca)

| Estado | Hex |
|---|---|
| Mejora | `#2e7d32` |
| Empeora | `#c62828` |
| Alerta (marcas, flechas y números grandes) | `#C77700` |
| Alerta (texto pequeño) | `#9A5A00` |

Siempre acompañar el color con el símbolo ▲ / ▼, para que se entienda sin distinguir colores.

## Contraste (texto blanco sobre el color)

| Color | Contraste | Resultado |
|---|---|---|
| `#0B1F3A` | 16.5:1 | Cumple |
| `#007F84` | 4.8:1 | Cumple |
| `#00B3B8` | 2.6:1 | **No cumple**: no poner texto blanco encima |

Sobre turquesa `#00B3B8` el texto legible es azul marino `#0B1F3A` (6.4:1).

## Para Tableau

`Preferences-BINATSA.tps` trae tres paletas listas para cargar: categórica, secuencial de segmentos y semáforo divergente. Copiarlo a `Mi repositorio de Tableau/Preferencias/Preferences.tps` y reiniciar Tableau Desktop.
