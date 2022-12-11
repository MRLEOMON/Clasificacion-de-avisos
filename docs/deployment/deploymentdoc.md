# ENTORNO DE DESPLIEGUE:

El documento de despliegue es una parte importante del proyecto de ciencia de datos ya que describe cómo se implementará el modelo de ciencia de datos en producción.  Para abordar este tema se tienen en cuenta los siguientes aspectos:

## 1. ENTORNO DE DESPLIEGUE

A continuación se enumerarán los requisitos de software y hardware necesarios para realizar la implementación del modelo:

### 1.1 REQUISITOS DE HARDWARE

El modelo de ciencia de datos se implementará en un servidor que tenga como mínimo las siguientes especificaciones:

- Procesador: 2 núcleos
- Memoria RAM: 4 GB
- Disco duro: 5 GB
- GPU: 8 GB de memoria
- Tarjeta de red: 100 Mbps

### 1.2 REQUISITOS PREVIOS DE SOFTWARE PARA PREPARAR LA INSTALACIÓN DEL REPOSITORIO  

Se requerirá tener una conexión a internet para descargar y actualizar el software necesario.

El software previo a la instalación del repositorio se detalla a continuación:

- Sistema operativo Linux distribución Debian versión 1.13 

- Python versión 3.9.2 como lenguaje de programación.
- Curl para descargar los datos y poetry para gestionar las dependencias del proyecto.

Los datos se ingresarán al servidor de manera manual a través de un archivo en formato Excel que se pondrá en la carpeta 'data' del proyecto. Se actualizará semanalmente y se utilizará para entrenar y evaluar el modelo.

### 1.3 GESTIÓN DE DATOS USADOS POR EL MODELO

Los datos se ingresarán al servidor de manera manual a través de un archivo en formato Excel que se pondrá en la carpeta 'data' del proyecto. Se agregarán datos  semanalmente con información descargada de el ERP SAP y estos datos serán los que utilizará el modelo para realizar la clasificación de las fallas.

--

En esta carpeta puedes añadir la documentación de despliegue, incluyendo

* Documentación de las APIs (por ejemplo, swagger).
* Documentación de los paquetes (por ejemplo, sphinx).
* Documentación del panel de control.
* Cualquier otra documentación dependiendo del tipo de despliegue.
