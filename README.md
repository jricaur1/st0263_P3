# st0263_P3
Análisis exploratorio de datos sobre datasets de COVID-19 usando Spark.

  1. Creación del bucket y cluster usando Amazon S3 y EMR.

Para poder trabajar inicialmente tenemos que crear un bucket y un cluster de datos, con estas herramientas podremos luego almacenar y analizar los datos de los datasets del COVID-19.
Bucket:
![](images/creating_bucket.jpg)
Cluster
![](images/creating_cluster1.jpg)
![](images/creating_cluster2.jpg)


  2. Ingesta de datos.

Descargamos los datos referentes al COVID-19 en https://data.humdata.org/dataset/novel-coronavirus-2019-ncov-cases, https://data.humdata.org/dataset/positive-cases-of-covid-19-in-colombia y https://data.humdata.org/ https://www.ins.gov.co/Paginas/Inicio.aspx https://www.who.int/data/gho. Posteriormente los agregamos a nuestro datalake en S3.
![](images/data_intake.jpg)

  3. Procesamiento: Análisis exploratorio de datos con pyspark

  3.1. Colombia
    Una vez se ingresan los datos al s3, se accede a los mismos y se realizan exploraciones generales de los datos, además de nuevas clasificaciones de los datos en colombia. Se clasifican los datos por fallecidos, y por recuperados. Una vez ejecutado este paso se almacenan los datos generados en archivos csv dentro de Amazon S3.

   Toda la exploración ejecutada de estos datos queda almacenada en el siguiente [cuaderno](../Colombia/Colombia.ipnb)

   Fallecidos:  s3://proyecto-bigdata-top-tel/COVID-19_data/Colombia/data_fallecidos.csv/part-00000-bcc9f339-37fb-4e00-b5a6-465e9f4fd8c1-c000.csv 
    Recuperados: s3://proyecto-bigdata-top-tel/COVID-19_data/Colombia/data_recuperados.csv/part-00000-525f09a0-29bb-41dd-a122-b648c4e3a663-c000.csv
