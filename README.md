# Windows and Powershell

## Protecciones de windows

### User Account Control (UAC)

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



>ver // Checa la version de windows

>set L // el controlador de dominio al que estamos conectados

>whoami /all /fo list // Get current user information, SID, domain, ***groups the user belongs to***, security privs of the user GRUPOS

>whoami /groups 

>net group "Remote Desktop Users" // solo lo deja usar en un controlador de dominio

>ipconfig /all  // Ve el domino y los dns 

>net localgroup "Administrators" // Display the list of local administrator accounts on the workstation 

>net group "Domain Admins" /domain  //Display the list of domain administrator accounts

>echo %LOGONSERVER% // ver el servidor a donde se autentica

>nltest /dclist:MODELO // ver relaciones entre el host y la worstation

>nltest /DSGETDC: // VEER A QUE    dominio estoy conectado



# Registro de Windows

El Registro de Windows (según Microsoft) es una base de datos jerárquica central que se utiliza para almacenar la información necesaria para configurar el sistema para uno o más usuarios, aplicaciones y dispositivos de hardware.


# Powershell

NOTA:***Powershell es case insensitive*** no diferencia entre minisculas y mayusculas.

## Cmdlet de PowerShell (verbo-sustantivo y no en plural)

Un cmdlet que también es llamado Command let es un comando ligero usado en el entorno de la ventana base de PowerShell. PowerShell invoca estos cmdlets en la línea de comandos. Puedes crear e invocar los cmdlets usando APIS de PowerShell.

Un cmdlet siempre consiste en un verbo y un sustantivo, separados por un guión. Algunos de los verbos principales que se usan para PowerShell, son:

1. Get - conseguir algo.
2. Start - Para ejecutar algo.
3. Out - Para la salida de algo.
4. Stop - Para detener algo que está corriendo.
5. Set - Para definir algo.
6. New - Para crear algo.
7. Get Module: muestra paquetes de comandos.
8. Get Content: Este cmdlet puede tomar un archivo y procesar su contenido y hacer algo con él.
9. Get- get: Encuentra todos los cmdlets que empiezan con la palabra "get-".


Ejemplo:

>Get-Help Format-Table //Mostrar información de ayuda sobre el comando Format-Table.

>Get-Command //Para generar una lista de cmdlets, funciones instaladas en tu máquina

>Get-Service "vm*" //Encuentra todos los cmdlets con la palabra "servicio" en él.

>Get-Service "vm*" | ***Get-Member*** //Mostrar lo que se puede hacer con un objeto.

> New-Item -Path 'C:\ComoFriki' -ItemType Directory // crea un directorio


## Variables especiales 

> echo $Host

1. $Error   Un array de objetos de error que muestran los errores más recientes.
2. $Host Mostrar el nombre de la aplicación de hosting actual.
3. $Profile Almacena la ruta completa de un perfil de usuario para el shell por defecto.
4. $PID  Almacena el identificador del proceso.
5. $PSUICulture   Lleva el nombre de la UI Culture actual.
6. $NULL Contiene un valor vacío o NULL.
7. $False   Contiene el valor FALSO.
8. $True Contiene el valor VERDADERO.

## Scripts de PowerShell

Los Scripts de Powershell se almacenan en un archivo .ps1. De forma predeterminada, ***NO se puede ejecutar un script con sólo hacer doble clic en el archivo***. Esto protege tu sistema de daños accidentales. 

### política que restringe la ejecución del script ( que tampoco permite que se ejecuten scripts)

#### Restricted  
No se permiten los scripts. Esta es la configuración predeterminada, por lo que se mostrará por primera vez que ejecutes el comando.

#### AllSigned 
Puedes ejecutar scripts firmados por un desarrollador de confianza. Con la ayuda de esta configuración, un script te pedirá confirmación de que quieres ejecutarlo antes de hacerlo.

#### RemoteSigned
Puedes ejecutar tus scripts firmados por un desarrollador de confianza

#### Unrestricted 
Puedes ejecutar cualquier script que desees.

***Cambiar la Politica de Ejecucion***

1. Get-ExecutionPolicy.
2. Set-executionpolicy unrestricted .
3. Escriba "S" en el indicador.
4. Get-ExecutionPolicy

## First scritp

& is the call operator which allows you to execute a command, a script, or a function.

firstscript.ps1
```
Write-Host "Hola, ComoFriki!"
```

Para ejecutar

>& "C:\PrimerScript.ps1"

>.\firstscript.ps1

# PowerShell ISE ( Es un IDE para programar scripts de powershell como el visualstudio code cuando programas con nodejs)

El entorno de scripts integrados de Windows PowerShell (ISE) es el editor predeterminado de Windows PowerShell. En este ISE, puedes ejecutar comandos, pruebas de escritura y depuración de scripts en una ventana base del entorno GUI. Puedes hacer edición multilínea, coloración de sintaxis, finalización de pestañas, ejecución selectiva y muchas otras cosas.

Windows PowerShell ISE también te permite ejecutar comandos por consola. Sin embargo, también admite paneles que puedes usar para ver simultáneamente el código fuente de tu script y otras herramientas que puedes conectar al ISE.

## Variables

Las variables se declaran en la forma $ <variable>.
Las variables podrían ser usadas para mantener la salida de los comandos, objetos y valores.
No es necesario especificar el "tipo" de una variable.
          





