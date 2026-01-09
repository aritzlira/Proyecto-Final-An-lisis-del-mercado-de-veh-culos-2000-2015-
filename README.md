Proyecto Final – Análisis del mercado de vehículos (2000–2015)

Este repositorio contiene el desarrollo completo del proyecto final del máster, en el que se analiza el mercado de vehículos a partir de dos datasets distintos: uno de precios de vehículos y otro de consumo de combustible. El trabajo se ha realizado siguiendo un flujo paso a paso en Python (VS Code + Jupyter Notebooks) y una fase final de visualización y dashboard en Excel.

El proyecto está estructurado en 5 notebooks, que deben leerse en orden, y un archivo Excel final donde se construye el dashboard interactivo.

⸻

Estructura del proyecto
	•	datos/crudos/
	•	car_prices.csv
	•	Fuel_Consumption_2000-2022.csv
	•	datos/procesados/
	•	dataset_final_coches.csv
	•	notebooks/
	•	01_carga_e_inspeccion_datos.ipynb
	•	02_limpieza_y_transformacion.ipynb
	•	03_union_datasets.ipynb
	•	04_eda_analisis_descriptivo.ipynb
	•	05_analisis_estadistico.ipynb
	•	dashboard_coches 2.0.xlsx

⸻

Notebook 01 – Carga e inspección de datos

En este primer notebook se realiza:
	•	Instalación e importación de librerías básicas (pandas, numpy).
	•	Carga de los dos datasets originales desde la carpeta datos/crudos:
	•	Dataset de precios de vehículos.
	•	Dataset de consumo de combustible.
	•	Primera inspección de los datos:
	•	Dimensiones de cada dataset.
	•	Visualización de columnas.
	•	Tipos de datos.
	•	Identificación inicial de valores nulos.

El objetivo de este notebook es entender qué información tenemos y en qué estado se encuentra antes de comenzar la limpieza.

⸻

Notebook 02 – Limpieza y transformación

En este notebook se trabaja la limpieza básica de ambos datasets:
	•	Normalización de nombres de columnas (minúsculas, eliminación de espacios).
	•	Conversión de columnas numéricas usando pd.to_numeric con control de errores.
	•	Revisión y cuantificación de valores nulos.
	•	Ajustes de tipos de datos para asegurar coherencia en los campos clave.

No se eliminan todavía registros de forma masiva, sino que se prepara el terreno para poder unir los datasets correctamente en el siguiente paso.

⸻

Notebook 03 – Unión de datasets

Este notebook es clave en el proyecto, ya que aquí se integran los dos datasets:
	•	Selección de columnas relevantes en ambos datasets.
	•	Definición de claves comunes para la unión (year, make, model).
	•	Unión mediante merge (left join) tomando como base el dataset de precios.
	•	Uso del indicador _merge para comprobar cuántos registros coinciden entre ambos datasets.
	•	Eliminación del indicador una vez validada la unión.

Después de la unión:
	•	Revisión de dimensiones finales.
	•	Revisión detallada de valores nulos por columna.
	•	Filtrado del rango temporal para quedarnos únicamente con vehículos entre 2000 y 2015, que es el periodo común y coherente para ambos datasets.
	•	Eliminación de registros sin información crítica (sellingprice, year).

Finalmente, se genera y exporta el dataset final limpio:
	•	dataset_final_coches.csv

Este archivo es el que se utiliza en los siguientes notebooks y en Excel.

⸻

Notebook 04 – Análisis exploratorio descriptivo (EDA)

En este notebook se realiza el análisis exploratorio del dataset final:
	•	Carga del dataset procesado.
	•	Revisión general con info() y describe().
	•	Análisis de variables clave como:
	•	Precio de venta (sellingprice).
	•	Año de fabricación.
	•	Marca.
	•	Consumo de combustible.
	•	Visualizaciones con matplotlib:
	•	Histogramas de precios.
	•	Distribución de vehículos por año.
	•	Top marcas por número de registros.
	•	Distribución del consumo de combustible.
	•	Relación entre consumo y precio (scatter plot).

Este notebook sirve para entender visualmente los datos antes de pasar a un análisis más numérico.

⸻

Notebook 05 – Análisis estadístico

En el último notebook se realiza un análisis más cuantitativo:
	•	Selección de variables numéricas relevantes:
	•	Precio, consumo, odómetro, tamaño de motor, cilindros y año.
	•	Creación de un subconjunto limpio sin valores nulos para análisis estadístico.
	•	Cálculo de:
	•	Estadísticos básicos.
	•	Matriz de correlaciones.
	•	Análisis de la relación entre el precio y el resto de variables.
	•	Agrupaciones para obtener:
	•	Precio medio por número de cilindros.
	•	Precio medio por año.

Este análisis confirma cuantitativamente tendencias que ya se intuían en el EDA.

⸻

Dashboard en Excel

Con el dataset final exportado se construye un dashboard interactivo en Excel:

Preparación
	•	Importación del CSV final usando separador correcto y formato numérico adecuado.
	•	Conversión de los datos en tabla (Datos).

KPIs

Se crean KPIs dinámicos (sensibles a la segmentación):
	•	TOTAL DE VEHÍCULOS
	•	PRECIO MEDIO
	•	MARCA MÁS FRECUENTE
	•	CONSUMO MEDIO (L/100km)

Todos los KPIs se calculan mediante tablas dinámicas para que respondan a los filtros.

Tablas dinámicas y gráficos

Se incluyen, entre otros:
	•	Precio medio por año.
	•	Precio medio por marca.
	•	Consumo medio por año.
	•	Total de vehículos por año.
	•	Distribución de vehículos por rangos de precio.
	•	Precio medio por rangos de consumo.

Cada tabla dinámica está correctamente nombrada siguiendo buenas prácticas.

Interactividad
	•	Segmentadores por año y marca.
	•	Los segmentadores afectan a todas las tablas dinámicas y KPIs.

El resultado final es un dashboard visual, claro e interactivo, que resume todo el análisis realizado previamente en Python.

⸻

Conclusión

Este proyecto recorre todo el flujo típico de un análisis de datos:
	1.	Carga y comprensión de los datos.
	2.	Limpieza y preparación.
	3.	Unión de fuentes distintas.
	4.	Análisis exploratorio.
	5.	Análisis estadístico.
	6.	Visualización final en un dashboard interactivo.

Todo el contenido del proyecto se ciñe estrictamente a lo trabajado en los notebooks y en el Excel final.

Resultados del análisis

A partir del análisis exploratorio y estadístico del dataset final, se han identificado varias tendencias relevantes en el mercado de vehículos entre los años 2000 y 2015.

En primer lugar, el precio medio de los vehículos muestra una tendencia claramente creciente a lo largo del tiempo. Este incremento es especialmente notable a partir de los años más recientes del periodo analizado, lo que sugiere un encarecimiento progresivo del mercado, posiblemente asociado a mejoras tecnológicas y cambios en el tipo de vehículos disponibles.

En cuanto al volumen de vehículos, se observa que el número de registros varía según el año, con una mayor concentración en determinados periodos. Este comportamiento indica que el mercado no es homogéneo a lo largo del tiempo y que existen años con mayor presencia de vehículos en el dataset.

Respecto al consumo de combustible, el análisis muestra una tendencia general a la reducción del consumo medio a lo largo de los años, lo que apunta a una mejora progresiva en la eficiencia de los vehículos. No obstante, este análisis se ha realizado únicamente sobre aquellos registros que disponen de información de consumo, ya que no todos los vehículos cuentan con este dato.

El estudio de la distribución de precios revela que el mercado está fuertemente concentrado en rangos de precio bajos y medios, mientras que los vehículos de precio elevado representan un porcentaje mucho menor del total. Esto indica que, aunque existen vehículos de gama alta, el grueso del mercado se sitúa en segmentos más accesibles.

Finalmente, al relacionar precio y consumo, se aprecia que no existe una relación lineal directa entre ambas variables. Esto sugiere que un mayor precio no implica necesariamente un mayor consumo, y que factores como la marca, el tipo de vehículo o la tecnología utilizada influyen de manera significativa.

Este README actúa como informe explicativo del análisis realizado.