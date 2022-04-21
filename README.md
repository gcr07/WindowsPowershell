## Windows and Powershell

# Protecciones de windows

## User Account Control (UAC)

¿Cómo funciona UAC? Cuando un usuario con un tipo de cuenta de administrador inicia sesión en un sistema, la sesión actual no se ejecuta con permisos elevados. Cuando se necesita ejecutar una operación que requiere privilegios de nivel superior, se le pedirá al usuario que confirme si permite que se ejecute la operación.

# Management 

## Configuracion 

>msconfig // configuraciones 

>taskmsg // Ctrl alt supr procesos y ahora mas 

>control.exe // Abre el panel de control

>  Computer Management (compmgmt) utility has three primary sections: System Tools, Storage, and Services and Applications.

## Visor de eventos 

Existen 5 tipos de eventos diferentes https://docs.microsoft.com/en-us/windows/win32/eventlog/event-types

## Windows Logs (Registros de Windows)

Existen 5 tipos de Logs https://docs.microsoft.com/en-us/windows/win32/eventlog/eventlog-key

## Informacion del sistema

>msinfo32 
>resmon 


## Local User and Group Management

Maneja usuarios y grupos

>lusrmgr.msc

## Windows Management Instrumentation (WMI) service

La herramienta WMIC está obsoleta en Windows 10, versión 21H1 y la versión 21H1 del canal de disponibilidad general de Windows Server. Esta herramienta es reemplazada por Windows PowerShell para WMI. Nota: Esta obsolescencia solo se aplica a la herramienta de administración de línea de comandos. WMI en sí no se ve afectado.

### NTFS Alternate Data Stream ADS

Hoy vas a ver NTFS Alternate Data Stream (ADS), técnica utilizada para ocultar información y programas dentro de un sistema.

Pero ¿para qué sirve ocultar archivos dentro de otros? pues para proteger archivos que quieras que permanezcan ocultos, evitando así que herramientas como los antivirus o anti-malware puedan detectarlos, aislarlos y/o eliminarlo.

### ADS (Alternate Data Stream)

Es la capacidad de bifurcar los datos en los archivos existentes sin cambiar o alterar su funcionalidad, tamaño o visualización a las utilidades de navegación del archivo. Esto permite inyectar código malicioso en los archivos de un sistema y ejecutarlo sin ser detectado. También permite la ocultación de rootkits o herramientas de hacking en un sistema comprometido, permitiendo ejecutarlas mientras permanecen ocultas del usuario.

### Detectar Archivos ocultos

>dir /r

Fuente:https://www.hackbysecurity.com/blog/ntfs-alternate-data-stream-ads


# Comandos cmd.exe (no powershell)

>csript "textfile.txt:script.vbs" //ejecutar un script .vbs

Ejemplo:
```script.vbs
msgbox "Este es un script simple"
```

>dir /r // Mostrar archivos ocultos incluso muesta la ADS bifurcacion de datos

cmd.exe /k ejecuta el comando y deja abierto Run Command and then remain open, at the CMD prompt.
          This is useful for testing, e.g. to examine variables 
cmd.exe /C     Run Command and then terminate

>C:\WINDOWS\System32\cmd.exe /k %windir%\system32\ipconfig.exe


# Registro de Windows

El Registro de Windows (según Microsoft) es una base de datos jerárquica central que se utiliza para almacenar la información necesaria para configurar el sistema para uno o más usuarios, aplicaciones y dispositivos de hardware.





















