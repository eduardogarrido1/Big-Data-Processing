# Big-Data-Processing
En este espacio se puede encontrar la práctica de Big Data Processing.

Esta consiste en la implementación de una Arquitectura Lambda principalmente enfocada en dos capas: Capa de Velocidad (Speed Layer) y Capa de Batch (Batch Layer). A continuación se imparten más detalles sobre cada capa.

## Capa de Velocidad (Speed Layer)
En esta capa se crea una instancia de Maquina Virtual (Para este proyecto fue utilizado Google Cloud Platform) y se configura para poder utilizar Apache Kafka. Aquí se recibirán los mensajes de las fuentes de datos.
Adicional a esto, se lanza un contenedor Docker para simular los datos.
También se utiliza una solución cloud para un entorno virtual de una Base de Datos en PostgreSQL. Aquí será guardada la información.

Las métricas a ser guardadas son:
1. Total de bytes por antena.
2. Total de por id de usuario.
3. Total de bytes por aplicación.

Dicha data será clasificada y particionada por año, mes, día y hora en formato PARQUET para ser guardado en un Bucket de Google Storage.

## Capa de Batch (Batch Layer)
En esta capa se crea un servicio para el análisis de los clientes. Se realiza mediante un Job de SparkSQL y las métricas se almacenan en PostgreSQL.

Las métricas a ser guardadas son:
1. Total de bytes por antena.
2. Total de bytes por email.
3. Total de bytes por aplicación.
4. emails de los usuarios que han sobrepasado la cuota por hora.

## Captura de la Base de Datos.
### Tabla user_metadata
![image](https://user-images.githubusercontent.com/107654215/199132901-433ae87a-c09c-4903-8a5d-3c0d1759c3e6.png)
