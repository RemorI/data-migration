# Data migration

Primeramente tenemos la relocalización de aplicaciones a una máquina virtual dentro de la nube, a través de lift-and-shift.


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
Los datos puede ser procesados y movidos por diferentes localizaciones antes de llegar al destino, y es sumamente necesario saber dónde está guardada y que se está guardando esa información luego de cada proceso.
