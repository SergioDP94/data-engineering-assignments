# Caso 05 - Pipeline ETL

Archivos preparados para construir un pipeline que integre varias fuentes.

- `ventas_fuente_a.csv`: ventas en el formato original.
- `ventas_fuente_b.csv`: ventas con un esquema diferente.
- `pedidos_fuente_api.json`: respuesta JSON anidada simulando una API.
- `mapa_columnas_fuente_b.json`: equivalencias para estandarizar las columnas de la fuente B.
- `mapa_canales_fuente_b.json`: equivalencias para normalizar canales de la fuente B.
- `output/`: carpeta destinada a los resultados del pipeline.

Objetivo esperado: extraer, transformar, validar e integrar las fuentes para producir un dataset estandarizado.
