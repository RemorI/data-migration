# Buenas prácticas para Athen

## Storage
Primeramente lo mejor es particionar la data, generalmente esto ya estará hecho porque tienden a hacerlo por día u horario, y como son datos que van a ser separados por tiempo, localización o similares es mejor que eso lo deje hecho alguien que sabe la estructura general para que todo sea similar.
De igual forma al particionar los datos, es mucho más fácil o más liviano realizar consultas SQL ya que se ve reducida en millones de veces la cuantía de las bases, ya que si de por sí son miles las ingestas diarias de datos, si solo se tuviera una base de datos sin particiones podría tener miles de millones de datos en unas pocas semanas. <br>
Esto también, una vez hecho luego queda como una claúsula que lo hace automáticamente, con menos razón es una preocupación para mí, solo curiosamente, esto se hace con AWS Glue. <br>
Pero conociendo cómo se ha particionado también es importante de tener en cuenta, ya que cuando se vaya a hacer un query se debe conocer cómo llamar a cada partición.
> SELECT dest, origin FROM flights WHERE year="1991"
Esto significa que solo la data que va ser leída es
> s3://athena-examples/flight/parquet/year=1991/
Pero realmente el particionamiento puede ser en base a varias especificaciones, por ejemplo fehca y región, o elementos o cualquier cosa que sea un dato común y repetible.<br>
<br><br><br>

## Bucket
Con bucketing se refiere a separar tablas de datos basada en los datos de una única columna, esto hace que los mismos datos estén en el mismo archivo, esto es muy relevante realizarlo cuando los datos de una columna sean tan importantes. En Athena se puede especificar la apertura de estos buckets además de que se podrán crear desde Athena como CTAS.
> CREATE TABLE CLUSTERED BY (<bucketed columns>) INTO <number of buckets> BUCKETS

## Compresión
Cuanto más pequeño es el tamaño del archivo (MB,GB,TB) más rápido es el análisis en Amazon S3. Athena puede soportar una variedad de formatos comprimidos como gzip, Snappy, zstd, pero hay una gran lista.<br>
El lado negativo es que la mayoría de formatos comprimidos no puede ser dividido así que se terminará leyendo entero, por eso tiene que haber un equilibrio entre cantidad de datos y el tamaño del archivo. Parquet y OCR pueden ser divididos porque la forma en que se comprime es en secciones y contiene la metadata para saber dónde ubica todo lo buscado.<br>
El formato **gzip** tiene buenos ratios de compresión y un largo soporte a través de otras herramientas. El **zstd** es relativamente nuevo, con un buen balance entre compresión y rendimiento. El **bzip2** y **LZO** son formatos dividibles, pero no son recomendables si se busca comprensión y compatibilidad.