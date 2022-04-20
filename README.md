## Windows and Powershell


### NTFS Alternate Data Stream ADS

Hoy vas a ver NTFS Alternate Data Stream (ADS), técnica utilizada para ocultar información y programas dentro de un sistema.

Pero ¿para qué sirve ocultar archivos dentro de otros? pues para proteger archivos que quieras que permanezcan ocultos, evitando así que herramientas como los antivirus o anti-malware puedan detectarlos, aislarlos y/o eliminarlo.

### ADS (Alternate Data Stream)

Es la capacidad de bifurcar los datos en los archivos existentes sin cambiar o alterar su funcionalidad, tamaño o visualización a las utilidades de navegación del archivo. Esto permite inyectar código malicioso en los archivos de un sistema y ejecutarlo sin ser detectado. También permite la ocultación de rootkits o herramientas de hacking en un sistema comprometido, permitiendo ejecutarlas mientras permanecen ocultas del usuario.

### Detectar Archivos ocultos

>dir /r

Fuente:https://www.hackbysecurity.com/blog/ntfs-alternate-data-stream-ads


# Comandos (no powershell)

>csript "textfile.txt:script.vbs" //ejecutar un script .vbs

Ejemplo:
```script.vbs
msgbox "Este es un script simple"
```

>dir /r // Mostrar archivos ocultos incluso muesta la ADS bifurcacion de datos























