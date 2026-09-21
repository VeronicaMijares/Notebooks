# Notebooks
Sube notebook con análisis de ConnectaTel
ConnectaTel — Análisis de comportamiento de clientes


#  Análisis de ConnectaTel

##  Objetivo del proyecto

El objetivo de este proyecto es realizar un análisis exploratorio de los datos de clientes de ConnectaTel para identificar patrones de comportamiento, características de los usuarios y oportunidades de segmentación.

El análisis busca comprender principalmente:

- La distribución de edad de los clientes.
- La cantidad de mensajes enviados.
- La cantidad de llamadas realizadas.
- La cantidad de minutos utilizados en llamadas.
- La presencia de valores faltantes y valores atípicos (outliers).
- Los diferentes niveles de uso de los clientes.
- Oportunidades para mejorar o crear nuevos planes comerciales.

---

##  Datasets utilizados

El proyecto utiliza un dataset de clientes de ConnectaTel con aproximadamente **4,000 registros**.

Entre las principales variables analizadas se encuentran:

| Variable | Descripción |
|----------|-------------|
| `age` | Edad del cliente |
| `cant_mensajes` | Cantidad de mensajes enviados |
| `cant_llamadas` | Cantidad de llamadas realizadas |
| `cant_minutos_llamada` | Cantidad de minutos utilizados en llamadas |

El dataset fue utilizado para realizar el análisis exploratorio y detectar patrones de comportamiento entre los clientes.

---

##  Etapas del análisis realizadas

El análisis se desarrolló mediante las siguientes etapas:

### 1. Carga y exploración de los datos

Se cargó el dataset y se revisó su estructura para conocer:

- Número de filas y columnas.
- Tipos de datos.
- Variables disponibles.
- Estadísticos descriptivos.

### 2. Limpieza de datos

Se revisó la calidad de los datos y se identificaron valores faltantes.

Se encontraron:

- 1 dato faltante en `cant_mensajes`.
- 1 dato faltante en `cant_llamadas`.
- 1 dato faltante en `cant_minutos_llamada`.

Cada uno representa aproximadamente el **0.025% de las 4,000 filas**.

### 3. Análisis estadístico

Se calcularon medidas descriptivas como:

- Media.
- Mediana.
- Desviación estándar.
- Mínimo.
- Máximo.
- Cuartiles.

Esto permitió conocer el comportamiento general de las variables.

### 4. Análisis de outliers

Se utilizaron boxplots para identificar valores atípicos.

Se encontraron outliers principalmente en:

- `cant_mensajes`
- `cant_llamadas`
- `cant_minutos_llamada`

Estos valores fueron conservados debido a que pueden representar comportamientos reales de clientes con un nivel de uso elevado.

### 5. Análisis de segmentos

Se analizaron los clientes considerando principalmente:

- Edad.
- Nivel de uso de los servicios.
- Cantidad de mensajes.
- Cantidad de llamadas.
- Minutos de llamadas.

Esto permitió identificar clientes con diferentes niveles de consumo.

### 6. Insight ejecutivo

Finalmente, los resultados se tradujeron en conclusiones orientadas al negocio.

Entre los principales hallazgos se encuentra la existencia de clientes con diferentes niveles de consumo, lo que representa una oportunidad para desarrollar ofertas y planes más personalizados.

---

##  Cómo ejecutar el notebook

El análisis puede ejecutarse utilizando **Google Colab**, sin necesidad de instalar Python o las librerías de manera local.

### Opción 1: Google Colab

1. Abrir [Google Colab](https://colab.research.google.com/).
2. Seleccionar **"Proyecto S7 → Abrir Notebook"**.
3. Subir el archivo `.ipynb` del proyecto.
4. Subir también el dataset utilizado, si el notebook lo requiere.
5. Ejecutar las celdas en orden utilizando **"Entorno de ejecución → Ejecutar todas"**.

### Opción 2: Ejecución local

Si se desea ejecutar el proyecto de manera local, se recomienda utilizar Python 3 y las principales librerías utilizadas en el análisis.














Matplotlib — visualización de datos.

Seaborn — generación de gráficas estadísticas.

Jupyter Notebook — desarrollo y documentación del análisis.



# Conclusión

El proyecto permitió transformar datos de clientes y registros de uso en información estructurada para el análisis.

El proceso incluyó exploración, limpieza, validación de datos, agregación, visualización, detección de outliers y segmentación de clientes.

La segmentación por edad y nivel de uso proporciona una base para profundizar posteriormente en el análisis de comportamiento, planes contratados, y para generar recomendaciones comerciales respaldadas por datos.
