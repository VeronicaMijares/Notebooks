# Notebooks
Sube notebook con análisis de ConnectaTel
ConnectaTel — Análisis de comportamiento de clientes

# Descripción del proyecto

Este proyecto analiza el comportamiento de los clientes de ConnectaTel, una empresa de telecomunicaciones de Latinoamérica, utilizando información de clientes y registros de uso de servicios durante 2024.

El objetivo principal es explorar los datos, detectar problemas de calidad, preparar la información para el análisis y segmentar a los clientes de acuerdo con su edad y nivel de uso. Finalmente, se presentan hallazgos y recomendaciones que pueden apoyar decisiones relacionadas con planes y estrategias comerciales.

# Objetivos

Explorar y comprender la estructura de los datos.

Identificar valores nulos, sentinels y datos inválidos.

Estandarizar y corregir columnas de fecha.

Analizar la ausencia de datos en las variables duration y length.

Crear un perfil de uso por cliente.

Analizar la distribución de edad, llamadas, mensajes y minutos utilizados.

Detectar posibles valores atípicos mediante el método IQR.

Segmentar clientes por edad y nivel de uso.

Obtener conclusiones y recomendaciones para los stakeholders.

# Datos utilizados

El proyecto utiliza tres archivos principales:

plans.csv

Contiene información de los planes disponibles para los clientes.

No presenta valores nulos relevantes.

Debido a su tamaño reducido, no requiere una exploración adicional extensa.

users.csv

Contiene información de los clientes, incluyendo variables como:

- user_id: identificador del cliente.

- age: edad del cliente.

- city: ciudad.

- reg_date: fecha de registro.

- plan: plan contratado.

- churn_date: fecha de cancelación, cuando aplica.

- usage.csv

Contiene los registros de utilización de los servicios:

- user_id: identificador del cliente.

- type: tipo de servicio utilizado (call o text).

- duration: duración de las llamadas.

- length: longitud de los mensajes.

# Limpieza y preparación de datos

Durante la exploración se identificaron diferentes problemas de calidad.

Valores sentinel

En la columna age se encontró el valor -999, que no representa una edad válida.

*Tratamiento:*

Se reemplazó -999 por un valor nulo.

Posteriormente, se imputó utilizando la mediana de edad, para reducir el impacto de valores extremos sobre la medida utilizada.

Valores inválidos en city

Se identificó el valor ? en la columna city.

*Tratamiento:*

Se reemplazó ? por pd.NA.

Fechas inválidas

Se revisaron las columnas de fecha para detectar valores fuera del rango esperado, particularmente fechas posteriores al 31 de diciembre de 2024.

*Tratamiento:*

Las fechas inválidas se convirtieron en valores nulos.

Las columnas de fecha fueron convertidas al formato datetime utilizando pd.to_datetime(..., errors='coerce').

Valores nulos en duration y length

Se analizó si los valores faltantes estaban relacionados con el tipo de registro (type).

Los resultados mostraron que:

duration presenta prácticamente todos sus valores faltantes en registros de tipo text.

length presenta prácticamente todos sus valores faltantes en registros de tipo call.

Esto indica que estas variables son no aplicables dependiendo del tipo de servicio. Por esta razón, no se realizó una imputación artificial de estos valores.

# Perfil de uso por cliente

Para facilitar el análisis se crearon variables agregadas por user_id:

- cant_mensajes: cantidad total de mensajes.

- cant_llamadas: cantidad total de llamadas.

- cant_minutos_llamada: cantidad total de minutos de llamadas.

Posteriormente, esta información se integró con los datos de clientes mediante un merge.

El resultado fue el DataFrame:

user_profile

# Análisis exploratorio

Se analizaron las distribuciones de:

Edad.

Cantidad de mensajes.

Cantidad de llamadas.

Minutos de llamadas.

También se compararon estas variables de acuerdo con el plan contratado para identificar posibles diferencias en el comportamiento de los clientes.

Se utilizaron principalmente:

Histogramas.

Gráficas de barras.

Boxplots.

Estadísticos descriptivos.

# Detección de outliers

Los valores atípicos se analizaron utilizando el rango intercuartílico.


Se aplicó este análisis a:

age

cant_mensajes

cant_llamadas

cant_minutos_llamada

Los posibles outliers no fueron eliminados automáticamente, ya que un consumo elevado puede representar un comportamiento real de los clientes y ser relevante para el negocio.

# Segmentación por nivel de uso

Los clientes fueron clasificados utilizando la cantidad de llamadas y mensajes.

*Bajo uso*

Llamadas < 5
Y
Mensajes < 5

*Uso medio*

Llamadas < 10
Y
Mensajes < 10

*Alto uso*

Todos los clientes que no cumplen las condiciones anteriores.


Esta clasificación permite identificar clientes con diferentes niveles de consumo y facilita el análisis de posibles necesidades comerciales.

# Segmentación por edad

Los clientes fueron agrupados en tres categorías:

Segmento

Rango de edad

*Joven*

Menos de 30 años

*Adulto*

30 a 59 años

*Adulto Mayor*

60 años o más

Esta variable permite complementar el análisis de consumo con una dimensión demográfica.

# Análisis ejecutivo

*Problemas detectados en los datos*

Se identificaron valores sentinel, como -999 en age.

Se encontraron valores no válidos como ? en city.

Se detectaron fechas fuera del rango esperado.

Los valores faltantes de duration y length están fuertemente relacionados con el tipo de servicio y representan variables no aplicables en determinados registros.

*Segmentos por edad*

La segmentación permite distinguir entre clientes jóvenes, adultos y adultos mayores, facilitando la comparación de sus patrones de consumo.

*Segmentos por nivel de uso*

La segmentación permite identificar clientes de bajo, medio y alto consumo con base en llamadas y mensajes.

Los clientes de alto uso pueden representar una oportunidad para analizar la adecuación de los planes actuales y la capacidad incluida en cada uno.

*Interpretación general*

El análisis muestra que el comportamiento de los clientes puede estudiarse desde diferentes dimensiones: consumo, edad y plan contratado. La combinación de estas variables puede ayudar a identificar patrones de uso y oportunidades para mejorar la oferta comercial.

# Recomendaciones

Analizar conjuntamente plan, nivel de uso y churn para identificar patrones asociados con cancelaciones.

Revisar si los clientes de alto consumo tienen planes adecuados para sus necesidades.

Considerar ofertas diferenciadas según el nivel de consumo.

Utilizar la edad como variable complementaria, evitando basar decisiones comerciales únicamente en ella.

Revisar los posibles outliers antes de eliminarlos, ya que pueden representar clientes reales con un consumo elevado.

Mantener documentadas las reglas de limpieza para garantizar la reproducibilidad del análisis.

*Herramientas utilizadas*

Python

Pandas — limpieza, transformación y análisis de datos.

NumPy — creación de condiciones y segmentación.

Matplotlib — visualización de datos.

Seaborn — generación de gráficas estadísticas.

Jupyter Notebook — desarrollo y documentación del análisis.



# Conclusión

El proyecto permitió transformar datos de clientes y registros de uso en información estructurada para el análisis.

El proceso incluyó exploración, limpieza, validación de datos, agregación, visualización, detección de outliers y segmentación de clientes.

La segmentación por edad y nivel de uso proporciona una base para profundizar posteriormente en el análisis de comportamiento, planes contratados, y para generar recomendaciones comerciales respaldadas por datos.
