# Caso 07: Consolidación de ventas diarias con scripts

## Situación
Una tienda genera un CSV al terminar cada día. La fecha está en el nombre del archivo y no aparece en sus columnas. El área comercial necesita reunir las ventas y conocer qué archivos se procesaron, incluidos los días sin ventas.

## Datos disponibles
`data/ventas_diarias` contiene siete archivos. Ejemplo: `ventas_2026-09-01.csv`.

Todos contienen las siguientes columnas:

- `venta_id`: identificador único de la venta.
- `producto`: producto vendido.
- `cantidad`: unidades vendidas.
- `precio_unitario`: precio por unidad, en soles.

Cada fila representa la venta de un producto. Los datos son sintéticos.
En este ejercicio, un archivo con solo encabezados indica que la extracción diaria se ejecutó y no encontró ventas. No agregues ventas ficticias para esos días.

Todos los archivos tienen el formato correcto. No se solicita resolver archivos dañados, nombres incorrectos ni ventas duplicadas.

## Actividades
1. Identifica todos los CSV de `data/ventas_diarias`.
2. Extrae la fecha del nombre de cada archivo.
3. Lee cada CSV y registra su cantidad de filas.
4. Agrega las columnas `fecha` y `archivo_origen` a las ventas.
5. Consolida las ventas en un solo DataFrame.
6. Calcula `importe`: cantidad multiplicada por precio unitario.
7. Construye una tabla de control con una fila por archivo leído.
8. Exporta los resultados a `salidas`, sin el índice.
9. Muestra en pantalla cuántos archivos y ventas se procesaron.

Puedes conservar la fecha como texto con formato AAAA-MM-DD.

## Organización del código
Completa los dos archivos proporcionados:

- `funciones.py`: define las funciones.
- `main.py`: importa las funciones y ejecuta el proceso.

Implementa al menos estas funciones:

- `consolidar_ventas(carpeta_datos)`: devuelve el DataFrame de ventas y el DataFrame de control, en ese orden.
- `guardar_resultados(ventas, control, carpeta_salida)`: crea la carpeta si hace falta y exporta ambos DataFrames a CSV.

Puedes definir funciones adicionales. Las plantillas no contienen la solución; deben completarse antes de generar resultados.

## Archivos de salida
### salidas/ventas_consolidadas.csv
Columnas, en este orden:
`venta_id`, `producto`, `cantidad`, `precio_unitario`, `fecha`, `archivo_origen`, `importe`.

### salidas/control_archivos.csv
Columnas, en este orden:
`archivo`, `fecha`, `filas_leidas`, `resultado`.

Valores de `resultado`:
- `Con ventas`: el archivo contiene registros.
- `Sin ventas`: contiene únicamente encabezados.

Los días sin ventas deben aparecer en el control con cero filas leídas.

## Cómo trabajar
1. Descarga y descomprime el repositorio.
2. Abre la carpeta `caso_07_ventas_scripts` en VS Code.
3. Si necesitas instalar pandas, ejecuta en la terminal:

```bash
python -m pip install -r requirements.txt
```

4. Completa `funciones.py` y `main.py`.
5. Desde la carpeta del caso, ejecuta:

```bash
python main.py
```

No necesitas descargar los datos otra vez desde el script: ya están dentro del caso.

## Verificaciones
- La suma de `filas_leidas` debe coincidir con las filas consolidadas.
- Todos los archivos deben aparecer en el control, incluidos los días sin ventas.
- Una segunda ejecución debe reemplazar las salidas anteriores sin acumular ni duplicar ventas.

## Prueba final
Agrega un CSV de un nuevo día con las mismas columnas e identificadores nuevos. Ejecuta otra vez el programa. El archivo debe incorporarse sin modificar el código. No escribas una lista fija de archivos.

## Entrega
Presenta `main.py`, `funciones.py` y los dos CSV generados. Explica brevemente cómo identificaste los días sin ventas.
