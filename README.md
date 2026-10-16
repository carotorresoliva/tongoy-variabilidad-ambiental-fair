# Variabilidad espacial y estacional de las condiciones ambientales en Bahía Barnes, Tongoy

## Descripción del proyecto

Este repositorio presenta un análisis exploratorio de la variabilidad espacial y estacional de indicadores espectrales y temperatura superficial del mar (SST) en cinco puntos de Bahía Barnes, Tongoy, Chile.

El estudio utiliza datos satelitales de Sentinel-2 y MODIS Aqua para comparar dos períodos: verano 2025–2026 e invierno 2026.

El trabajo fue desarrollado en el contexto de un taller de geomática aplicada, procesamiento de datos satelitales y principios FAIR.

## Área y períodos de estudio

- **Área:** Bahía Barnes, Tongoy, Chile.
- **Puntos de estudio:** cinco ubicaciones geográficas.
- **Verano:** diciembre de 2025 a febrero de 2026.
- **Invierno:** junio a agosto de 2026.
- **Sistema de coordenadas:** WGS84 (EPSG:4326).

## Fuentes de datos y metodología

**Sentinel-2 Level-2A**

Se analizaron observaciones satelitales correspondientes a cinco puntos de estudio, considerando los índices NDCI, NDWI (formulación NIR–SWIR1, también denominada NDMI), NDVI y la reflectancia de la banda roja B04.

Se realizaron comparaciones descriptivas entre puntos y estaciones. Los resultados se interpretaron como variaciones espectrales exploratorias, considerando las limitaciones radiométricas y la disponibilidad desigual de observaciones.

**MODIS Aqua**

Se utilizó el producto mensual MODIS Aqua L3 SST Thermal Daytime, con resolución espacial nominal de 4 km.

Se seleccionaron seis meses, se conservaron observaciones con código de calidad `qual_sst = 0` y se identificaron los píxeles únicos para evitar contabilizar repetidamente observaciones de un mismo píxel.

## Resultados principales

El conjunto Sentinel-2 contiene 375 registros correspondientes a ambas estaciones. Las medianas del NDCI fueron más negativas durante el invierno, aunque estas diferencias no permiten inferir directamente cambios en la concentración de clorofila-a.

En MODIS Aqua, los cinco puntos estuvieron representados por tres píxeles distintos. La media de las medianas mensuales de SST fue de 18,55 °C en verano y 14,70 °C en invierno, con una diferencia descriptiva de 3,85 °C.

Estos resultados corresponden a los períodos y píxeles seleccionados. No constituyen una climatología histórica ni una evaluación inferencial de diferencias estacionales.

## Archivos del repositorio

| Archivo | Descripción |
|---|---|
| `Tongoy_variabilidad_ambiental_FAIR.ipynb` | Cuaderno de procesamiento y análisis |
| `resultados_tongoy/sentinel2_tongoy_estacional.parquet` | Datos espectrales Sentinel-2 |
| `resultados_tongoy/modis_aqua_sst_puntos.parquet` | SST mensual extraída por punto |
| `resultados_tongoy/modis_aqua_sst_pixeles.parquet` | SST mensual por píxel único |
| `resultados_tongoy/modis_aqua_sst_resumen_mensual.parquet` | Resumen mensual de SST |
| `resultados_tongoy/metadata.json` | Metadatos, diccionario de variables y procedencia |

## Reproducibilidad y principios FAIR

Los conjuntos de datos procesados se distribuyen en formato Parquet y se acompañan de metadatos en formato JSON.

El cuaderno permite recuperar los archivos publicados y documenta el procesamiento geoespacial y las principales decisiones metodológicas. La reconstrucción de los productos MODIS originales requiere acceso a NASA Earthdata.

La documentación incluye identificadores de productos, períodos analizados, variables, unidades y procedencia del código.

## Código utilizado y atribución

Se utilizaron funciones del repositorio [Geomática Aplicada](https://github.com/alvaroparedesl/geomatica-aplicada), especialmente de los módulos `utils.raster` y `utils.series`.

El código original de dicho repositorio está distribuido bajo licencia GNU GPL versión 3. Esta información no implica que todos los datos satelitales y archivos derivados tengan automáticamente la misma licencia.
