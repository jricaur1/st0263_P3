# st0263_P3
Análisis exploratorio de datos sobre datasets de COVID-19 usando Spark.

 ## 1. Creación del bucket y cluster usando Amazon S3 y EMR.

Para poder trabajar inicialmente tenemos que crear un bucket y un cluster de datos, con estas herramientas podremos luego almacenar y analizar los datos de los datasets del COVID-19.
Bucket:
![](images/creating_bucket.jpg)
Cluster
![](images/creating_cluster1.jpg)
![](images/creating_cluster2.jpg)


 ## 2. Ingesta de datos.

Descargamos los datos referentes al COVID-19 en https://data.humdata.org/dataset/novel-coronavirus-2019-ncov-cases, https://data.humdata.org/dataset/positive-cases-of-covid-19-in-colombia y https://data.humdata.org/ https://www.ins.gov.co/Paginas/Inicio.aspx https://www.who.int/data/gho. Posteriormente los agregamos a nuestro datalake en S3.
![](images/data_intake.jpg)

 ## 3. Procesamiento: Análisis exploratorio de datos con pyspark

 ### 3.1. Colombia
    Una vez se ingresan los datos al s3, se accede a los mismos y se realizan exploraciones generales de los datos, además de nuevas clasificaciones de los datos en colombia. Se clasifican los datos por fallecidos, y por recuperados. Una vez ejecutado este paso se almacenan los datos generados en archivos csv dentro de Amazon S3.

   Toda la exploración ejecutada de estos datos queda almacenada en el siguiente [cuaderno](https://github.com/jricaur1/st0263_P3/blob/master/Colombia/Colombia.ipynb)

   Fallecidos:  s3://proyecto-bigdata-top-tel/COVID-19_data/Colombia/data_fallecidos.csv/part-00000-bcc9f339-37fb-4e00-b5a6-465e9f4fd8c1-c000.csv 
    Recuperados: s3://proyecto-bigdata-top-tel/COVID-19_data/Colombia/data_recuperados.csv/part-00000-525f09a0-29bb-41dd-a122-b648c4e3a663-c000.csv

 ### 3.2 En el mundo
    Los datos del mundo están de la forma en la que se pueden ver la cantidad de infectados, recuperados y muertos hasta la fecha por país. Las exploraciones ejecutadas con estos datos estarán almacenadas en el siguiente [cuaderno](https://github.com/jricaur1/st0263_P3/blob/master/Nivel%20Mundial/Resto%20del%20mundo.ipynb).

 ### 3.3 Colombia VS. Mundo
    La idea sería la siguente: comparar a Colombia con otros países del mundo con el fin de ver las diferencias entre las cifras, adicionalmente podemos ver que tanto porcentaje de infectados, muertos y recuperados son de Colombia.

 ## 4. Visualización básica de datos

  Para la visualización de los datos se implementó una instancia EC2, con sistema operativo CentOS, y en esta se utilizaron contenedores tanto de elastic search como de kibana. el [docker-file](https://github.com/jricaur1/st0263_P3/blob/master/kibana/docker-compose.yml) se encuentra directamente en este repositorio.

  ![](images/kibana_docker.jpg)

  una vez se crea esta instancia se accede a la aplicación [kibana](http://ec2-3-88-24-197.compute-1.amazonaws.com:5601/) y en ella se importan los datos

  ![](images/kibana_import.jpg)

  ### 4.2. Situación Colombia

  En el caso de Colombia se importan los datos e inmediatamente estos presentan informes generales a través del data visualizer. Una vez importados se crea un esquema que permite el uso de estos datos dentro de las opciones Visualize y Dashboard

  Se crean múltiples gráficos para visualizar la información con respecto a Colombia y se muestran los mismos en el Dashboard de ese mismo nombre

  inserte pantallazos de dashboard

  Se presentaron dificultades al manejar un parámetro como la edad puesto que esta es tomada como String por la plataforma, limitando las posiblidades de conteos, rangos, etc.

  ![](images/kibana_dashboard_1.jpg)

  ![](images/kibana_dashboard_2.jpg)

  ![](images/kibana_dashboard_3.jpg)

  ![](images/kibana_dashboard_4.jpg)
