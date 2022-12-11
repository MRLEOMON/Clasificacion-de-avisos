# INFORME DEL MODELO DE REFERENCIA

## INTRODUCCIÓN

El problema que se trata de resolver, se refiere a que se presenta un alto número de eventos que se registran en un sistema de gestión de mantenimiento de una serie de estaciones de bombeo de petróleo, lo que implica una alta carga de trabajo para el equipo encargado de clasificarlos de manera manual.  Debido al gran volumen de eventos que se registran en el sistema, el equipo de ingenieros dedica una gran cantidad de tiempo a revisar y clasificar cada uno de ellos, lo que genera costos anuales significativos.  Esta tarea se realiza de manera manual, lo que hace que sea tediosa y poco eficiente.  El objetivo de este documento es presentar una solución que permita automatizar el proceso de clasificación de eventos en el sistema de gestión de mantenimiento, con el fin de reducir los costos y aumentar la eficiencia del equipo de ingenieros.  Se propone utilizar técnicas de procesamiento de lenguaje natural para identificar palabras clave en los eventos registrados en el sistema y asignarles automáticamente la categoría correspondiente.  Con esta solución se espera reducir el tiempo que se dedica a la clasificación de eventos de manera manual, lo que permitirá al equipo de ingenieros dedicar su tiempo a tareas más productivas y aumentar la eficiencia del sistema en general.

## DESCRIPCIÓN DEL MODELO DE REFERENCIA

## Enfoque analítico

### Cuál es la definición del objetivo

El objetivo del enfoque analítico propuesto en este proyecto es automatizar el proceso de clasificación de eventos en el sistema de gestión de mantenimiento de para una serie de estaciones de bombeo de hidrocarburos. Para lograr esto, se utilizan técnicas de procesamiento de lenguaje natural (NLP) para identificar palabras clave en los eventos registrados en el sistema y asignarles automáticamente la categoría correspondiente.

### Cuáles son las entradas (descripción)

Las entradas del modelo propuesto en este proyecto son las bolsas de palabras generadas a partir de la descripción de la falla y el texto extendido del aviso del sistema de gestión de mantenimiento SAP. Para generar las bolsas de palabras, se realiza un pre-procesamiento del texto que incluye la eliminación de números y preposiciones mediante expresiones regulares, la conversión del texto a minúsculas y la corrección de palabras mal escritas.  Estas bolsas de palabras representan el vocabulario utilizado en los avisos del sistema y se utilizan como entradas para el clasificador.

Una vez generadas las bolsas de palabras, se implementa un clasificador que recibe como entradas los datos de la descripción del aviso y el texto explicativo y utiliza las bolsas de palabras generadas anteriormente para determinar si el evento corresponde a una falla, una condición del equipo o si no se trata de una falla.

![image](https://user-images.githubusercontent.com/109122368/206909852-7483bfac-8ff7-4186-b4c3-eea68ab81627.png)

El modelo se ejecuta de manera automática y permite clasificar los eventos de manera rápida y precisa, lo que reduce el tiempo y los costos asociados al proceso manual actual.

### ¿Qué tipo de modelo se ha construido?

El modelo propuesto en este proyecto es un clasificador que utiliza técnicas de procesamiento de lenguaje natural (NLP) para automatizar el proceso de clasificación de eventos del sistema de gestión de mantenimiento. El modelo se compone de tres etapas principales: extracción de datos, pre-procesamiento y clasificación.

En la primera etapa, se extraen los datos de SAP y se exportan a un dataset en formato excel. En la segunda etapa, se realiza un pre-procesamiento del texto que incluye la eliminación de números y preposiciones mediante expresiones regulares, la conversión del texto a minúsculas y la corrección de palabras mal escritas utilizando técnicas de bolsa de palabras.

Finalmente, en la etapa de clasificación, se implementa un clasificador que utiliza las bolsas de palabras generadas en la etapa de pre-procesamiento como entradas para determinar si el evento corresponde a una falla, una condición del equipo o si no se trata de una falla. La salida del modelo es la categoría asignada automáticamente al evento.

En resumen, el modelo construido es un clasificador que utiliza técnicas de procesamiento de lenguaje natural y bolsas de palabras para determinar automáticamente la categoría a la que pertenece un evento registrado en el sistema de gestión de mantenimiento.

## Descripción del modelo

### Modelos y parámetros

#### Descripción o imágenes del gráfico de flujo de datos

El flujo de datos en el modelo construido se compone de tres etapas principales: extracción de datos, pre-procesamiento y clasificación. En la primera etapa, se extraen los datos referentes a eventos de fallas del sistema de gestión de mantenimiento SAP PM y se exportan a un dataset en formato excel. En la segunda etapa, se realiza un pre-procesamiento del texto de este archivo, específicamente la descripción del aviso y el texto explicativo que incluye la eliminación de números y preposiciones, la conversión a minúsculas y la corrección de palabras mal escritas mediante técnicas de bolsa de palabras.

En la tercera etapa, se utiliza un clasificador para determinar la categoría a la que pertenece el evento en cuestión. Para ello, se utilizan las bolsas de palabras generadas en la etapa de pre-procesamiento como entradas para el clasificador. La salida del modelo es la categoría asignada al evento de manera automática.
	
#### ¿Qué aprendizaje se utilizó?
	
En el proyecto se utilizó un aprendizaje supervisado para entrenar el clasificador. Este tipo de aprendizaje requiere que se proporcionen datos etiquetados con las categorías correctas a las que pertenecen, de manera que el modelo pueda aprender a asignar categorías de manera precisa en base a los patrones encontrados en los datos de entrenamiento.  Para implementar el clasificador, se utilizó el algoritmo de machine learning Linear Support Vector Classification el cual toma un conjunto de datos de falla etiquetados asigna las categorías a nuevos avisos de falla.
	
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

## RESULTADOS OBTENIDOS (RENDIMIENTO DEL MODELO)

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

MATRIZ DE DESEMPEÑO DEL MODELO CON MEJOR DESEMPEÑO

![image](https://user-images.githubusercontent.com/109122368/206931801-b71fb00a-c0ab-40a0-b49a-a8537c325b33.png)


## CONCLUSIONES

Como conclusiones se puede decir que una de las claves de éxito de este modelo está en generar adecuadamente las bolsas de palabras y hacer un correcto preprocesamiento de la información. Los autocorrectores son importantes ya que nos permiten tener las palabras correctas y de esta manera agrupar conjuntos de texto exactos ya que como se pudo apreciar, existen muchos errores ortográficos en la redacción de los textos.

Otro aspecto importante es realizar los pasos correctos del diagrama de flujo para colocar las etiquetas, esto se debe a que existe un orden lógico propio para este tipo de textos y que son puntuales de la industria del Oil&Gas, si se comete un error o se hacen pasos invertidos, el resultado puede variar considerablemente.

En cuanto a los modelos se puede apreciar que el clasificador Linear Support Vector Classification ***(LinearSVC)*** obtuvo el mejor resultado. Esto se debe a que las máquinas de soporte vectorial permiten encontrar la forma óptima de clasificar varias clases. La clasificación óptima se realiza maximizando el margen de separación entre las clases y los vectores que definen el borde de esta separación son los vectores de soporte.

Finalmente como recomendación podemos decir que es importante estar actualizando constantemente las bolsas de palabras y los autocorrectores con el lenguaje propio de esta industria para poder tener textos con mayor calidad que le permita al modelo realizar una clasificación adecuada.

------------------------

El modelo base es el modelo que un científico de datos entrenaría y evaluaría rápidamente después de tener el primer conjunto de características (preliminares) listo para el modelado de aprendizaje automático. A través de la construcción del modelo de referencia, el científico de datos puede tener una evaluación rápida de la viabilidad de la tarea de aprendizaje automático.


 




### Gráficos ROC/Lift, AUC, R^2, MAPE, según proceda
### Gráficos de rendimiento para los barridos de parámetros, si procede

## Comprensión del modelo

* Importancia de las variables (importancia)

## Comprensión del modelo

## Conclusión y debates para los próximos pasos

* Conclusión sobre la evaluación de la viabilidad de la tarea de aprendizaje automático

* Debate sobre el sobreajuste (si procede)

* ¿Qué otras características pueden generarse a partir de los datos actuales?

* Qué otras fuentes de datos relevantes están disponibles para ayudar al modelado
