# Caso 05: Consolidación automática de archivos CSV

## Descripción

En este caso trabajaremos con múltiples archivos CSV que representan entregas periódicas de ventas provenientes de distintas sucursales.

El objetivo es construir un proceso en Python que permita:

- identificar automáticamente los archivos disponibles;
- leer y transformar cada archivo;
- reutilizar código mediante funciones;
- validar la estructura de los datos;
- manejar errores sin detener todo el proceso;
- conservar información sobre el archivo de origen;
- consolidar los registros válidos;
- generar un único archivo CSV de salida.

Este caso continúa la secuencia de trabajo del módulo después de haber utilizado listas, diccionarios, condicionales, bucles, archivos CSV y datos JSON.

---

## Estructura de la carpeta

Los archivos de entrada se encuentran en:

```text
data/
└── caso_05_consolidacion_csv/
    └── entrada/
        ├── ventas_2026_09_01_lima.csv
        ├── ventas_2026_09_02_arequipa.csv
        ├── ventas_2026_09_03_trujillo.csv
        ├── ...
        └── ventas_2026_09_24_piura.csv
```

La carpeta contiene **24 archivos CSV**.

Cada archivo corresponde a una entrega de ventas y, en condiciones normales, contiene las columnas:

```text
fecha
producto
cantidad
precio
```

Ejemplo:

```csv
fecha,producto,cantidad,precio
2026-09-01,Laptop,2,2500.00
2026-09-01,Mouse,5,80.00
2026-09-01,Teclado,3,120.00
```

---

## Importante

La mayoría de los archivos tiene una estructura correcta, pero algunos contienen **inconsistencias intencionales**.

Estas inconsistencias forman parte del caso y permiten practicar:

- validación de columnas;
- conversión de tipos;
- manejo de excepciones;
- identificación de registros problemáticos;
- continuidad del proceso ante errores.

No se recomienda corregir manualmente los archivos antes de realizar el ejercicio.

La finalidad es que el código sea capaz de identificar y manejar estos problemas.

---

## Flujo esperado

El proceso general del caso es:

```text
Archivos CSV
     ↓
Identificación automática
     ↓
Lectura de cada archivo
     ↓
Validación
     ↓
Transformación
     ↓
Manejo de errores
     ↓
Consolidación
     ↓
Archivo CSV final
```

---

## Conceptos de Python utilizados

Durante el caso se trabajará principalmente con:

- `Path` y manejo de rutas;
- `glob()` para identificar varios archivos;
- `csv.DictReader`;
- `csv.DictWriter`;
- listas;
- diccionarios;
- conjuntos (`set`);
- condicionales;
- bucles `for`;
- funciones;
- parámetros y `return`;
- `append()` y `extend()`;
- conversión de tipos con `int()` y `float()`;
- `try` y `except`;
- `continue`.

---

## Objetivo de aprendizaje

Hasta este punto, los casos anteriores han permitido trabajar con archivos individuales.

En este caso el reto cambia:

> ¿Qué ocurre cuando el mismo proceso debe aplicarse automáticamente a muchos archivos?

La intención es pasar de un procesamiento manual a un flujo reutilizable.

En lugar de escribir código diferente para cada archivo, se buscará construir una función que pueda recibir una ruta, procesar el archivo correspondiente y devolver sus registros transformados.

Conceptualmente:

```text
archivo
   ↓
procesar_archivo()
   ↓
filas procesadas
```

Luego, esa misma función podrá utilizarse dentro de un bucle:

```text
archivo 1 ─┐
archivo 2 ─┤
archivo 3 ─┤
   ...     ├──→ procesar_archivo() ──→ consolidación
archivo N ─┘
```

---

## Archivo de origen

Durante la consolidación se recomienda agregar una columna que permita identificar de qué archivo proviene cada registro.

Por ejemplo:

```text
archivo_origen
```

Un resultado podría verse así:

```csv
fecha,producto,cantidad,precio,importe,archivo_origen
2026-09-01,Laptop,2,2500.00,5000.00,ventas_2026_09_01_lima.csv
```

Esta información permite mantener la **trazabilidad del dato** durante el proceso.

---

## Carpeta de salida

El resultado del proceso no debe mezclarse con los archivos originales.

Se recomienda generar una estructura como:

```text
data/
└── caso_05_consolidacion_csv/
    ├── entrada/
    │   ├── ventas_2026_09_01_lima.csv
    │   ├── ventas_2026_09_02_arequipa.csv
    │   └── ...
    │
    └── salida/
        └── ventas_consolidadas.csv
```

La carpeta `entrada` contiene los datos recibidos.

La carpeta `salida` contiene los archivos producidos por nuestro proceso.

Separar ambas carpetas evita que un archivo generado sea leído accidentalmente como si fuera un nuevo archivo de entrada.

---

## Recomendaciones

1. No modificar manualmente los archivos de entrada.
2. No asumir que todos los archivos tienen exactamente la misma estructura.
3. No asumir que todos los valores numéricos podrán convertirse correctamente.
4. Revisar primero un archivo antes de automatizar el procesamiento completo.
5. Construir el proceso progresivamente.
6. Utilizar funciones cuando aparezca código repetido.
7. Registrar o mostrar los errores encontrados sin detener innecesariamente todo el proceso.
8. Mantener separados los archivos de entrada y salida.

---

## Preguntas para orientar el análisis

Mientras desarrollas el caso, intenta responder:

1. ¿Cuántos archivos fueron encontrados automáticamente?
2. ¿Todos contienen las columnas esperadas?
3. ¿Todos los valores de `cantidad` pueden convertirse a enteros?
4. ¿Todos los valores de `precio` pueden convertirse a números decimales?
5. ¿Qué debería ocurrir cuando aparece un registro inválido?
6. ¿Qué debería ocurrir cuando un archivo completo tiene una estructura incorrecta?
7. ¿Cuántos registros válidos llegan al archivo consolidado?
8. ¿Cómo podemos saber de qué archivo provino cada fila?
9. ¿Por qué es conveniente utilizar una función para procesar cada archivo?
10. ¿Por qué la carpeta de salida debe mantenerse separada de la carpeta de entrada?

---

## Resultado esperado

Al finalizar el caso se tendrá un proceso capaz de:

```text
detectar archivos
      ↓
validarlos
      ↓
procesarlos
      ↓
manejar errores
      ↓
consolidar registros
      ↓
generar una salida
```

Este ejercicio representa una versión introductoria de un proceso de **ingestión, transformación, validación y consolidación de datos**.

El objetivo principal no es únicamente producir un CSV final, sino comprender cómo diseñar un proceso que pueda repetirse de manera automática sobre múltiples archivos.
