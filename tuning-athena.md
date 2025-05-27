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