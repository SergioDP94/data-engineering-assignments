# Caso 06: De pedidos en JSON a una tabla de ventas

## Situación
Una tienda registra sus pedidos en un archivo JSON. Cada pedido contiene información del cliente y una lista de productos. El área comercial necesita el detalle de los pedidos entregados y un resumen de ventas por ciudad.

Los datos son sintéticos. Los precios están expresados en soles y corresponden a una unidad.

## Archivo disponible
`data/pedidos.json` contiene 18 pedidos. Cada pedido incluye:

- `pedido_id`: identificador del pedido.
- `fecha`: fecha del pedido.
- `cliente`: diccionario con `cliente_id` y `ciudad`.
- `estado`: entregado, pendiente o cancelado.
- `productos`: lista de productos con nombre, cantidad y precio.

## Actividades
1. Lee el JSON e identifica su estructura.
2. Explora cómo acceder a los datos del cliente y a los productos.
3. Selecciona únicamente los pedidos con estado `entregado`.
4. Construye un DataFrame con una fila por producto de cada pedido.
5. Calcula el importe: cantidad multiplicada por precio.
6. Calcula el importe total por ciudad.
7. Exporta ambos resultados a `salidas`, sin el índice.

La tabla detallada debe contener, en este orden:
`pedido_id`, `fecha`, `cliente_id`, `ciudad`, `producto`, `cantidad`, `precio`, `importe`.

El resumen debe contener: `ciudad`, `importe_total`.

## Archivos de salida
- `salidas/detalle_ventas.csv`
- `salidas/ventas_por_ciudad.csv`

## Preguntas
- ¿Cuántos pedidos tienen estado entregado?
- ¿Cuántas filas tiene el detalle de esos pedidos?
- ¿Por qué un pedido puede generar varias filas?
- ¿Qué ciudad registra el mayor importe total?
- ¿El importe del detalle coincide con la suma del resumen?

## Entrega
Presenta el notebook ejecutado, las respuestas y los dos CSV. El notebook se proporcionará por separado; este caso todavía no lo incluye.

## Ubicación de los datos
Si utilizas la celda de clase que descarga y conserva la carpeta `data` del repositorio, la ruta desde ese entorno será:

`data/caso_06_pedidos_json/data/pedidos.json`

Si trabajas desde la carpeta de este caso, la ruta será `data/pedidos.json`.
Guarda las salidas dentro de la carpeta de este caso.

Si tu entorno ya tenía una carpeta `data` descargada antes de incorporar este caso, actualiza la descarga: la celda original omite la descarga cuando esa carpeta existe.
