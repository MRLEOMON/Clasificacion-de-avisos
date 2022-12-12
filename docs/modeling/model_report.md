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
* Lista de características brutas y derivadas 
* Clasificación de la importancia.

## Algoritmo
* Descripción o imágenes del gráfico de flujo de datos
  ## Si es AzureML, enlace a:
    * Experimento de entrenamiento
    * Flujo de trabajo de puntuación
* ¿Qué aprendiz(es) se utilizó(n)?
* Hiperparámetros del aprendiz

## Resultados
* Gráficos ROC/Lift, AUC, R^2, MAPE, según proceda
* Gráficos de rendimiento para los barridos de parámetros, si procede
