# Análisis de casas en venta en Toluca

## Descripción

`Casa_toluca.csv` contiene información de anuncios de casas en venta en Toluca, Estado de México. El conjunto de datos tiene **2,004 registros** y **8 columnas**, incluyendo la ubicación, el área, el número de baños, las habitaciones y el precio.

Este archivo puede utilizarse para realizar análisis exploratorios y estudiar la relación entre las características de una vivienda y su precio.

## Columnas del conjunto de datos

| Columna | Descripción |
|---|---|
| `Ubicación` | Texto con la ubicación o descripción geográfica del anuncio. |
| `Area` | Área reportada de la vivienda. La unidad no está especificada en el archivo. |
| `Baños` | Número de baños reportado. |
| `Habitaciones` | Número de habitaciones reportado. |
| `Precio` | Precio anunciado de la vivienda. La moneda no está especificada explícitamente en el archivo. |
| `Unnamed: 0`, `Unnamed: 0.1`, `Unnamed: 0.2` | Columnas que parecen ser índices duplicados; conviene revisarlas y eliminarlas si no son necesarias. |

## Calidad de los datos

- Hay valores faltantes en `Area` (283), `Baños` (54), `Habitaciones` (73) y `Precio` (5).
- La columna `Ubicación` contiene 1,274 valores distintos.
- Algunas cifras extremas, como áreas o cantidades de baños/habitaciones muy altas, podrían ser errores de captura o casos atípicos. Se recomienda revisarlas antes de modelar.
- Antes del análisis, conviene confirmar las unidades del área y la moneda del precio.

## Posibles análisis

- Calcular el precio promedio y la mediana de las viviendas.
- Comparar precios según el área, los baños y las habitaciones.
- Identificar ubicaciones con mayor cantidad de anuncios.
- Visualizar la distribución de precios y detectar valores atípicos.
- Construir un modelo de regresión para explorar qué características se relacionan con el precio.

## Cómo cargar el archivo con Python

```python
import pandas as pd

df = pd.read_csv("Casa_toluca.csv")

print(df.head())
print(df.info())
print(df.isnull().sum())
```

## Limpieza inicial sugerida

```python
# Eliminar columnas de índice duplicadas, si no son necesarias
df = df.drop(columns=["Unnamed: 0", "Unnamed: 0.1", "Unnamed: 0.2"],
             errors="ignore")

# Revisar los valores faltantes
print(df.isnull().sum())

# Consultar estadísticas descriptivas
print(df[["Area", "Baños", "Habitaciones", "Precio"]].describe())
```

No se eliminan ni imputan valores faltantes automáticamente en este ejemplo. La estrategia de limpieza debe elegirse según el objetivo del análisis.

## Archivo

- `Casa_toluca.csv`: datos originales de anuncios de casas en venta.

## Nota

Este conjunto de datos describe precios anunciados, que pueden diferir de los precios finales de venta. Los resultados del análisis dependen de la calidad, actualidad y consistencia de los registros.

