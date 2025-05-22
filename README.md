# Data migration
Es importante entender que los beneficios que vienen con el uso del almacenamiento en la nube son la viabilidad, latencia, la auto orquestación, manejar coneccionse complicadas y escalar el tamaño, además de muchas cosas más pero estos suelen ser los principales problemas con los que hay que lidiar con un storage on-premise. 
Primeramente tenemos la relocalización de aplicaciones a una máquina virtual dentro de la nube, a través de lift-and-shift.
Pero generalmente hay más complejos teniendo que realizar re-estructuraciones en la arquitectura de las data stores.<br>
Cuando se realiza una migraciones de datos no hay que perder de vista la **seguridad**, **cumplimiento**, **disponibilidad** e **integridad**. Requiere un esfuerzo coordinado entre bases de datos, desarrollo de aplicaciones, data, DevOps y equipo de infraestructura.

## Lift and shift
*Lift-and-shift*, es una estrategia de migración de aplicaciones que primeramente los lleva offline antes de llevarlo a la nube, y una vez subido este método puede hacer uso de una estructura tipo servicio (IaaS), plataforma como servicio (Paas) o software como servicio (SaaS).
- Tiene el beneficio de ser efectivo en costos para las migraciones de aplicaciones a la nube.
- Permite a las compañías implementar el guardado en nube sin afectar a la data on-premise.
- Pero hay que tener cuidado con este método ya que se debería elegir una nube que permita una simple integración y migración sin tantas complicaciones.

*Proceso*: Es una alternativa a una migración completa y es bastante efectivo como concepto. 
1. Primeramente se debe hacer una preparación de los datos on-premise y del environment en la nube.
2. El proceso de migración se debe hacer el pasos sin sincronicidad porque puede generar problemas de conflicto en las aplicaciones on-premise. Seleccionar solamente ciertos trozos de dato para moverlos de una forma más rápida y eficiente para llevarlos a la nube.
3. Y una vez que esa migración se hizo se puede mover los demás trozos de data con normalidad, pero de todas formas debe ser suave y lento.

*Consideraciones para su utilización*: Hay una diferencia considerable entre shifting data y transfering data, los datos pueden ser shifted de tu sistema a la nube pero va a necesitar reengineering antes de poder ser usada.<br>
Los datos puede ser procesados y movidos por diferentes localizaciones antes de llegar al destino, y es sumamente necesario saber dónde está guardada y que se está guardando esa información luego de cada proceso.<br>
También es necesario saber que los datos puede ser vulnerables en todo el transito y procesamiento, así que hay que asegurar las medidas de seguridad previamente.

## More complex Data Migration
Al tener que trabajar con migraciones de datos más complejas, empezamos a tener que realizar muchas más correcciones en el sistema para que todo pueda seguir funcionando con normalidad. Primero para asegurar que esté integrado de la misma forma que en la version anterior y que todo funciona de forma perfecta, hay que asegurar principales mantenimientos y cuidados a tener en cuenta para que los datos no se vean perjudicados.
1. Seguridad y cumplimiento, los datos se tienen que mantener seguros y mantener un cumplimiento regulatorio y con políticas internas en cada estapa de la migración.
2. Disponibilidad del sistema, es muy relevante saber el tiempo en el que va a estar dado de baja el sistema por temas de la migración y cómo va a ser el nuevo horario. Pero generalmente por el tipo de migración suele no haber interrupción en la disponibilidad ya que se mantiene la base mientras se prepara la migración en otro sitio diferente. También el nuevo sistema se puede probar en solo una pequeña población para que funcionen como testers del funcionamiento de la nueva bbdd. Aún así se debe asegurar **mínimo** tiempo de caída.
3. Data loss, es muy importante evitar la pérdida de datos durante el período de migración, puede suceder que se escriba es un lugar y otro no o que simplemente no se esté escribiendo en ninguno.
4. Compatibilidad, para el correcto funcionamiento del sistema se debe asegurar que se mantenga la misma compatibilidad e integración con el sistema anterior a ser migrado. Eso se refiere tanto a la conectividad con aplicaciones, otras bases de datos e incluso integraciones específicas con otras pipelines
5. Sobrecoste, es importante elegir la nueva bbdd o almacenamiento teniendo en cuentas las previas necesidades de la bbdd anterior porque sino podemos pasar problemas de costos por el mantenimiento de una bbdd demasiado grande o demasiado pequeña para realmente lo necesario, además de tener en cuenta los costos de ampliación y escalado. Además de que la transferencia de datos también tienen un costo, no solo el mantenimiento de la bbdd.

Por eso los principales problemas con los que hay que lidiar son, el riesgo de pérdida de datos, los tiempos de caída y que los datos tengan integridad y precisión. <br>
Es esencial que en cualquier transferencia de datos se pueda mantener cuidado lo siguiente:
1. Data backup
2. Data profiling and analysis
3. Data migration assessment
4. Cleansing data
5. Migration tools

Al hacer un análisis más profundo en estos temas, se puede hablar de las mejores y más básicas prácticas que jamás pueden faltar sin importar qué en la migración de datos, ya sea on-premise to cloud o cloud to cloud.
1. Antes de empezar a pensar en la migración de los datos, es importante conocer los metadatos de la bbdd, además de conocer los propósitos para la que está armada ya que esto va a hablar muchísimo de su estructura y cómo se tiende a utilizar para poder conseguir la mejor eficiencia.
    - Asegurar la calidad de los datos, es muy necesario para que a la hora de realizar la migración, no se envíen datos con errores, incompletos o directamente equivocados a la nueba bbdd
    - Entender la complejidad de los datos, el análisis de la base de datos es fundamental para poder una mejor planeación y preparación a la hora de la migración, ya que esto permite conocer más a fondo cómo es el comportamiento que se debe replicar y no solo la forma
    - Mitigación de riesgos, al conocer la fuente de los datos se pueden evitar riesgos más allá de los datos dentro de la fuente, sino también del exterior, las dependencias e independencias de los datos que van a tener que volver a ser conectadas o asegurarse de que no estén conectadas.
2. Data backup, para asegurar la integridad de los datos es necesario que siempre haya un backup de los datos y sobre todo antes de cada cambio en caso de cometer errores. Esto genera mayor seguridad al trabajar con estos datos porque nunca se va a perder la integridad de los mismos, en caso de que los datos transferidos se hayan corrompido o no se movieran de la forma esperada aún así se mantiene un backup con los datos fuente, además de la integridad también evitamos un principal problema que es la pérdida de datos.
    - Asegurar la integridad de los datos, mantiene los datos íntegros y seguros luego de la migración para salvaguardar de pérdidas o corrupción
    - Mitigador de riesgos, se evitan muchos riesgos al tener backup ya que siempre se puede volver un paso atrás asegurado
    - Continuidad del negocio, esto también ayuda la negocio porque estos datos van a quedar guardados en el sistema y van a poder ser consultados cuando sea necesario
3. 