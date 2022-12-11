# INFORME DEL MODELO DE REFERENCIA

## INTRODUCCIÓN

El problema que se trata de resolver, se refiere a que se presenta un alto número de eventos que se registran en un sistema de gestión de mantenimiento de una serie de estaciones de bombeo de petróleo, lo que implica una alta carga de trabajo para el equipo encargado de clasificarlos de manera manual.  Debido al gran volumen de eventos que se registran en el sistema, el equipo de ingenieros dedica una gran cantidad de tiempo a revisar y clasificar cada uno de ellos, lo que genera costos anuales significativos.  Esta tarea se realiza de manera manual, lo que hace que sea tediosa y poco eficiente.  El objetivo de este documento es presentar una solución que permita automatizar el proceso de clasificación de eventos en el sistema de gestión de mantenimiento, con el fin de reducir los costos y aumentar la eficiencia del equipo de ingenieros.  Se propone utilizar técnicas de procesamiento de lenguaje natural para identificar palabras clave en los eventos registrados en el sistema y asignarles automáticamente la categoría correspondiente.  Con esta solución se espera reducir el tiempo que se dedica a la clasificación de eventos de manera manual, lo que permitirá al equipo de ingenieros dedicar su tiempo a tareas más productivas y aumentar la eficiencia del sistema en general.

## DESCRIPCIÓN DEL MODELO DE REFERENCIA

El modelo de referencia propuesto en este proyecto se basa en el uso de técnicas de procesamiento de lenguaje natural (NLP) para clasificar automáticamente los eventos registrados en el sistema de gestión de mantenimiento de una estación de bombeo de petróleo.

El modelo se compone de tres etapas principales: extracción de datos, pre-procesamiento y clasificación. En la primera etapa, se extraen los datos de SAP y se exportan a un dataset en formato excel. En la segunda etapa, se realiza un pre-procesamiento del texto que incluye la eliminación de números y preposiciones mediante expresiones regulares, la conversión del texto a minúsculas y la corrección de palabras mal escritas utilizando técnicas de bolsa de palabras.

Finalmente, en la etapa de clasificación, se implementa un clasificador que utiliza las bolsas de palabras para determinar si el evento corresponde a una falla, una condición del equipo o si no se trata de una falla.

![image](https://user-images.githubusercontent.com/109122368/206909852-7483bfac-8ff7-4186-b4c3-eea68ab81627.png)

El modelo se ejecuta de manera automática y permite clasificar los eventos de manera rápida y precisa, lo que reduce el tiempo y los costos asociados al proceso manual actual.

## RESULTADOS OBTENIDOS

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

De acuerdo a los resultados obtenidos al implementar diferentes modelos de clasificación, se concluyó que el modelo Linear Support Vector Classification con la representación de texto BoW ofreció el mejor desempeño, logrando un accuracy de 93.8%. Esto significa que el modelo es capaz de predecir correctamente la categoría a la que pertenece un evento en el 93.8% de los casos.  Esto se debe a que Linear Support Vector Classification es un clasificador lineal que se basa en la maximización del margen entre las categorías, lo que le permite realizar una clasificación más precisa de los eventos en el dataset.

Sin embargo, dado que se cuentan con un número limitado de datos, el accuracy del modelo es inferior al 98%, lo que indica que todavía hay margen de mejora en su capacidad de clasificación. Por lo tanto, se propone continuar trabajando con la implementación del clasificador mientras se obtienen mas datos de entrenamiento para el modelo y así para aumentar su precisión.

------------------------



Los resultados obtenidos muestran que el mejor desempeño se obtuvo con el clasificador Linear Support Vector Classification utilizando la representación de texto BoW, con un accuracy del 93.8%. Aunque este resultado es bueno, se observa que aún hay margen de mejora, ya que se requiere un accuracy superior al 98% para considerar la implementación del clasificador.


4.	Resultados obtenidos: en esta sección debes presentar los resultados obtenidos al evaluar el modelo de referencia en tus datos. Debes incluir información sobre las métricas utilizadas para evaluar el rendimiento del modelo, así como un análisis detallado de los resultados obtenidos y cómo se comparan con los resultados previamente reportados en la literatura.
5.	Análisis y discusión: en esta sección debes analizar los resultados obtenidos y discutir cualquier aspecto interesante o destacable del rendimiento del modelo. También debes incluir una discusión sobre cómo se podría mejorar el modelo en el futuro y cómo se podría utilizar para resolver el problema de manera más efectiva.
6.	Conclusiones: en esta sección debes resumir los principales hallazgos de tu informe y presentar tus conclusiones finales sobre el rendimiento del modelo de referencia. También debes discutir cómo estos resultados pueden ser útiles para otros investigadores y cómo se podrían aplicar en la práctica.


El modelo base es el modelo que un científico de datos entrenaría y evaluaría rápidamente después de tener el primer conjunto de características (preliminares) listo para el modelado de aprendizaje automático. A través de la construcción del modelo de referencia, el científico de datos puede tener una evaluación rápida de la viabilidad de la tarea de aprendizaje automático.


## Enfoque analítico
* Cuál es la definición del objetivo
* Cuáles son las entradas (descripción)
* ¿Qué tipo de modelo se ha construido?

## Descripción del modelo

* Modelos y parámetros

	* Descripción o imágenes del gráfico de flujo de datos
  		* Si es AzureML, enlace a:
    		* Experimento de entrenamiento
    		* Flujo de trabajo de puntuación
	* ¿Qué aprendiz(es) se utilizó(n)?
	* Hiperparámetros del aprendizaje


## Resultados (Rendimiento del modelo)
* Gráficos ROC/Lift, AUC, R^2, MAPE, según proceda
* Gráficos de rendimiento para los barridos de parámetros, si procede

## Comprensión del modelo

* Importancia de las variables (importancia)

## Comprensión del modelo

## Conclusión y debates para los próximos pasos

* Conclusión sobre la evaluación de la viabilidad de la tarea de aprendizaje automático

* Debate sobre el sobreajuste (si procede)

* ¿Qué otras características pueden generarse a partir de los datos actuales?

* Qué otras fuentes de datos relevantes están disponibles para ayudar al modelado
