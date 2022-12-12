# INFORME DEL MODELO FINAL

Informe que describe el modelo final que se entregará - normalmente compuesto por uno o más de los modelos construidos durante la vida del proyecto_.

## INFORME DEL MODELO DE REFERENCIA - ENFOQUE ANALÍTICO

### Cuál es la definición del objetivo

El enfoque analítico propuesto en este proyecto tiene como objetivo automatizar el proceso de clasificación de eventos en el sistema de gestión de mantenimiento de una serie de estaciones de bombeo de hidrocarburos. Para ello, se utilizarán técnicas de procesamiento de lenguaje natural para identificar palabras clave en los eventos registrados y asignarles automáticamente la categoría correspondiente. De esta manera, se busca simplificar y agilizar el proceso de clasificación de eventos en el sistema de gestión de mantenimiento.

### Cuáles son las entradas (descripción)

El modelo propuesto en este proyecto utiliza la descripción de la falla y el texto extendido del aviso del sistema de gestión de mantenimiento SAP como entradas. Para generar las bolsas de palabras, se realiza un pre-procesamiento del texto que incluye la eliminación de números y preposiciones, la conversión a minúsculas y la corrección de palabras mal escritas. Estas bolsas de palabras representan el vocabulario utilizado en los avisos y se utilizan como entradas para el clasificador.

El clasificador recibe la descripción del aviso y el texto explicativo y utiliza las bolsas de palabras generadas para determinar si el evento corresponde a una falla, una condición del equipo o si no se trata de una falla.

![image](https://user-images.githubusercontent.com/109122368/206909852-7483bfac-8ff7-4186-b4c3-eea68ab81627.png)

El modelo se ejecuta de manera automática y permite clasificar los eventos de manera rápida y precisa, lo que reduce el tiempo y los costos asociados al proceso manual actual.

### ¿Qué tipo de modelo se ha construido?

Este proyecto propone un clasificador que utiliza técnicas de procesamiento de lenguaje natural (NLP) para automatizar la clasificación de eventos en el sistema de gestión de mantenimiento. El modelo consta de tres etapas: extracción de datos, pre-procesamiento y clasificación.

En la primera etapa, se extraen los datos de SAP y se convierten en un dataset en formato excel. Luego, se realiza un pre-procesamiento del texto que incluye la eliminación de números y preposiciones, la conversión a minúsculas y la corrección de palabras mal escritas utilizando bolsas de palabras.

Finalmente, en la etapa de clasificación, se implementa un clasificador que utiliza las bolsas de palabras como entradas para determinar la categoría de un evento: falla, condición del equipo o sin falla. La salida del modelo es la categoría asignada automáticamente al evento.

En resumen, el modelo es un clasificador que utiliza técnicas de NLP y bolsas de palabras para determinar automáticamente la categoría de un evento en el sistema de gestión de mantenimiento.

## Descripción de la solución

### Arquitectura simple de la solución

La arquitectura simple del modelo de clasificación construido en este proyecto se compone de tres etapas principales: extracción de datos, pre-procesamiento y clasificación.

En la primera etapa, los datos se extraen de SAP y se exportan a un dataset en formato excel. En la segunda etapa, se realiza un pre-procesamiento del texto que incluye la eliminación de números y preposiciones mediante expresiones regulares, la conversión del texto a minúsculas y la corrección de palabras mal escritas utilizando técnicas de bolsa de palabras.

En la etapa de clasificación, se implementa un clasificador que utiliza las bolsas de palabras generadas en la etapa de pre-procesamiento como entradas para determinar si el evento corresponde a una falla, una condición del equipo o si no se trata de una falla. La salida del modelo es la categoría asignada automáticamente al evento.

En resumen, la arquitectura simple del modelo construido es la siguiente:

Extracción de datos: se extraen los datos de SAP y se exportan a un dataset en formato excel.
Pre-procesamiento: se realiza un pre-procesamiento del texto que incluye la eliminación de números y preposiciones mediante expresiones regulares, la conversión del texto a minúsculas y la corrección de palabras mal escritas utilizando técnicas de bolsa de palabras.
Clasificación: se implementa un clasificador que utiliza las bolsas de palabras generadas en la etapa de pre-procesamiento como entradas para determinar la categoría del evento. La salida del modelo es la categoría asignada automáticamente al evento.

#### Fuentes de datos

En este proyecto, la fuente de datos es el sistema de gestión de mantenimiento SAP. Los datos se extraen de SAP y se exportan a un dataset en formato excel para su procesamiento.

#### Componentes de la solución

**1. Diccionario para corregir palabras mal escritas**: se utiliza para autocompletar y estandarizar las palabras en el campo "Descripción del aviso" y "Texto explicativo".

**2. Bolsa de palabras**: se utiliza para generar las características de entrada del clasificador.

**3. Clasificador**: se implementa un clasificador que utiliza las bolsas de palabras generadas en la etapa de pre-procesamiento como entradas para determinar la categoría del evento.

**4. Dataset**: se utiliza para almacenar los datos extraídos de SAP y luego procesarlos.

**5. Lógica de Pre-procesamiento**: se realiza un pre-procesamiento del texto que incluye la eliminación de números y preposiciones mediante expresiones regulares, la conversión del texto a minúsculas y la corrección de palabras mal escritas utilizando técnicas de bolsa de palabras.

#### Flujo de datos

**1.** Los datos se extraen de SAP y se exportan a un dataset en formato excel.

**2.** Se realiza un pre-procesamiento del texto en el dataset, que incluye la eliminación de números y preposiciones mediante expresiones regulares, la conversión del texto a minúsculas y la corrección de palabras mal escritas utilizando técnicas de bolsa de palabras.

**3.** Se generan las características de entrada del clasificador utilizando la bolsa de palabras.

**4.** El clasificador utiliza las características generadas en la etapa de pre-procesamiento como entradas para determinar la categoría del evento.

### ¿Cuál es la salida?

La salida del modelo es la categoría asignada automáticamente al evento.

## Datos

### Fuente

Los datos provienen del CMMS **SAP** donde cada tipo de evento ocurrido en las diferentes estaciones de petróleo es registrado, almacenando datos puntales que pueden ser de interes para realizar muchos tipos de análisis

### Esquema de datos

Esta base de datos contiene los avisos de falla de equipos de la semana inmediatamente anterior de las estaciones de bombeo de hidrocarburos objeto del contrato de servicio integral de mantenimiento de estaciones de los sistemas de transporte y logística de hidrocarburos.  A continuación se muestra como los datos se encuentran relacionados en SAP

![image](https://user-images.githubusercontent.com/109122368/206936663-41fd6781-9b11-40b1-a5ff-9a5c4ed78d4a.png)

### Muestreo

para validar el modelo, se dividió el conjunto de datos en **70%** para entrenamiento y **30%** para prueba.

### Selección (fechas, segmentos)

Los datos utilizados para entrenar y evaluar el modelo se refieren a los eventos de falla (avisos Y2) de 24 estaciones de bombeo del 01-ene-2018 al 20-sep-2022.

### Estadísticas (recuentos)

El total de entradas des de 29.970.  Como los campos **Descripción** y **Texto explicativo** son de tipo Objetct (Texto), no es posible obtener datos estadísticos descriptivos. 

## Características

### Lista de características brutas y derivadas

**La lista de características brutas** podría incluir las palabras extraídas del campo Descripción del aviso y Texto explicativo después de aplicar la corrección de palabras mal escritas.

**La lista de características derivadas** podría incluir las bolsas de palabras generadas en la etapa de pre-procesamiento, así como la representación del texto obtenida mediante TF-IDF. Estas características se utilizarán como entradas para el clasificador, y se basan en las palabras extraídas del texto original.
 
### Clasificación de la importancia.

La clasificación de la importancia es una tarea subjetiva que depende de diversos factores, como la relevancia del evento para la operación del equipo o sistema, su impacto en la disponibilidad o en el rendimiento, entre otros.

En general, la clasificación de la importancia se podría realizar teniendo en cuenta el equipo que está presentando la falla o avería, los equipos ya se encuentran clasificados en SAP  mediante una escala de valores que van desde "crítico por disponibilidad", "Esencial", "No crítico" y "Crítico por seguridad" dependiendo de como se encuentra clasificado de equipo, así es el nivel de impacto del evento en cuestión. Sin embargo, esta clasificación puede variar según el contexto operacional y las necesidades específicas del cliente.

## Algoritmo

#### Descripción o imágenes del gráfico de flujo de datos

El flujo de datos en el modelo construido se compone de tres etapas principales: extracción de datos, pre-procesamiento y clasificación. En la primera etapa, se extraen los datos referentes a eventos de fallas del sistema de gestión de mantenimiento SAP PM y se exportan a un archivo de dataset en formato excel. En la segunda etapa, se realiza un pre-procesamiento de los datos, enfocándose en la descripción del aviso y el texto explicativo. Esto incluye la eliminación de números y preposiciones, la conversión a minúsculas y la corrección de palabras mal escritas mediante el uso de técnicas de bolsa de palabras.

Posteriormente, en la tercera etapa, se utiliza un clasificador para determinar la categoría a la que pertenece cada evento de falla. Para ello, se utilizan las bolsas de palabras generadas en la etapa de pre-procesamiento como entradas para el clasificador. La salida del modelo es la categoría asignada al evento de manera automática.
	
#### ¿Qué aprendizaje se utilizó?
	
En el proyecto se utilizó un aprendizaje supervisado para entrenar el clasificador. En este tipo de aprendizaje, se proporcionan datos etiquetados con las categorías correctas a las que pertenecen, de manera que el modelo pueda aprender a asignar categorías de manera precisa en base a los patrones encontrados en los datos de entrenamiento. Para implementar el clasificador, se utilizó el algoritmo de machine learning llamado "Linear Support Vector Classification". Este algoritmo toma un conjunto de datos de fallas etiquetados y asigna categorías a nuevos avisos de fallas en base a lo que ha aprendido de los datos de entrenamiento.
	
#### Hiperparámetros del aprendizaje

A continuación se muestran los detalles referentes a la configuración y el ajuste del modelo de clasificación:

a. Diccionario para corregir las palabras mal escritas del campo Descripción del aviso y Texto explicativo: compuesta por 5.538 y 248 palabras respectivamente.  Se encargan de realizar el autocompletado (ej. shut por shutdown) y estandarizar las palabras (ej. shutoff por shutdown).

b. Bolsa de palabras para clasificar los avisos: Está compuesta por 180 palabras o frases clave que realizan la clasificación que se muestra a continuación:

| clasificación | proceso de gestión |
| --- | --- |
| No aplica | No aplica |
| Condición | Inteligencia artificial |
| Falla | Seguridad de procesos |
| Falla | Eliminación de defectos |

c. Para el proceso de entrenamiento, vamos a evaluar distintos tipos de representaciones o características:

1. Se utilizará esta matriz obtenida con la **bolsa** de palabras bow como entrada del clasificador.
2. Usaremos la representación del texto obtenida con **TF-IDF**.

En todos los casos, se utilizará validación cruzada (**hold out cross-validation**) para validar el modelo, por lo que dividiremos el conjunto de datos en **70%** para entrenamiento y **30%** para prueba. Se usará un parámetro ``random_state=0`` para inicializar una semilla para asegurarnos que todos obtengamos los mismos resultados. 

Las variables que le pasaremos a nuestros clasificadores para entrenar y validar los modelos son las siguientes: **X_train**, **X_test**, **y_train**, **y_test**

## Resultados

En el proyecto, se implementaron diferentes modelos de clasificación para evaluar su eficacia en el proceso de clasificación de eventos en el sistema de gestión de mantenimiento. Estos modelos incluyen Multinomial Naive Bayes, Logistic Regression classifier, Support Vector Classification, Linear Support Vector Classification y Pipelines.

| CLASIFICADOR | REPRESENTACIÓN DE TEXTO | ACCURACY |
| --- | --- | --- | 
| Multinomial Naive Bayes | BoW | 87,4% |
| Multinomial Naive Bayes | TF-IDF| 83,0% |
| Logistic Regression classifier | BoW | 93,5% |
| Logistic Regression classifier | TF-IDF| 93,2% |
| Support Vector Classification | BoW | 82,5% |
| Support Vector Classification | TF-IDF|82,5% |
| ***Linear Support Vector Classification*** | ***BoW*** | ***93,8%*** |
| Linear Support Vector Classification | TF-IDF| 93,7% |
| Pipeline | TF-IDF | 93,4% | 

**Matriz de desempeño del mejor modelo**

De acuerdo a los resultados obtenidos al implementar diferentes modelos de clasificación, se concluyó que el modelo "Linear Support Vector Classification" con la representación de texto BoW ofreció el mejor desempeño, logrando un accuracy del 93.8%. Esto significa que el modelo es capaz de predecir correctamente la categoría a la que pertenece un evento en el 93.8% de los casos. Este resultado positivo se debe a que "Linear Support Vector Classification" es un clasificador lineal que se basa en la maximización del margen entre las categorías, lo que le permite realizar una clasificación más precisa de los eventos en el dataset.

![image](https://user-images.githubusercontent.com/109122368/206931851-bf2e9584-7d74-43ba-a731-ca3b45c1f360.png)

![image](https://user-images.githubusercontent.com/109122368/206931866-4a6ae93a-be72-435a-a925-3f07df12ac56.png)

Vemos que con este modelo se obtuvo un excelente desempeño, a continuación las métricas de desempeño:

![image](https://user-images.githubusercontent.com/109122368/206931948-1c961ce5-c360-4a1a-a992-4e0bf2377b58.png)

Sin embargo, dado que se cuenta con un número limitado de datos, el accuracy del modelo es inferior al 98%, lo que indica que todavía hay margen de mejora en su capacidad de clasificación. Por lo tanto, se propone continuar trabajando con la implementación del clasificador para mejorar su precisión, obteniendo más datos de entrenamiento para el modelo. Esto permitirá aumentar la calidad de las predicciones del clasificador y su capacidad de clasificación de eventos de falla.
