# Contenido

1. [ARCHIVOS](#archivos)
   - [Listamiento de archivos y carpetas](#listamiento-de-archivos-y-carpetas)
   - [Combinaciones y variaciones](#combinaciones-y-variaciones)
   - [Mostrar donde estoy parado](#combinaciones-y-variaciones)
   - [Ordenar archivos](#ordenar-archivos)
1. [ACCESO ADMINISTRATIVO](#acceso-administrativo)
   - [Especificar el inicio de sesión en la shell como root](#especificar-el-inicio-de-sesión-en-la-shell-como-root)
   - [SUDO](#sudo)
1. [PERMISOS DE LOS ARCHIVOS](#permisos-de-los-archivos)
   - [Conjunto de Permisos](#conjunto-de-permisos)
   - [Acción](#acción)
   - [Permisos](#permisos)
   - [TEMA APARTE, NO TAN APARTE](#tema-aparte-no-tan-aparte)
   - [Cambiar el propietario de un archivo](#cambiar-el-propietario-de-un-archivo)
1. [VISUALIZACIÓN DE ARCHIVOS](#visualización-de-archivos)
   - [cat](#cat)
   - [head](#head)
   - [tail](#tail)
1. [COPIAR ARCHIVOS](#copiar-archivos)
1. [CLONAR UN DISCO](#clonar-un-disco)
1. [MOVER ARCHIVOS](#mover-archivos)
   - [Forma de cambiar el nombre a un archivo](#forma-de-cambiar-el-nombre-a-un-archivo)
1. [ELIMINAR ARCHIVOS](#eliminar-archivos)
1. [APAGAR](#apagar)
1. [CONFIGURACIÓN DE REDES](#configuración-de-redes)
1. [VISUALIZACIÓN DE PROCESOS](#visualización-de-procesos)
1. [ADMINISTRACIÓN DE PAQUETES](#administración-de-paquetes)
   - [Instalación de paquetes](#instalación-de-paquetes)
   - [Actualización de paquetes](#actualización-de-paquetes)
   - [Eliminación de paquetes](#eliminación-de-paquetes)
1. [ACTUALIZACIÓN DE CONTRASEÑAS DE USUARIO](#actualización-de-contraseñas-de-usuario)
1. [REDIRECCIÓN](#redirección)
1. [EDITOR DE TEXTO](#editor-de-texto)  
   [Modo de comando: Movimiento](#modo-de-comando-movimiento)
   - [Eliminar](#eliminar)
   - [Cambiar](#cambiar)
   - [Sacar](#sacar)
   - [Poner](#poner)
   - [Buscar en vi](#buscar-en-vi)
   - [Modo Insertar](#modo-insertar)

<hr>

# ARCHIVOS

## Listamiento de archivos y carpetas

> `ls -l` _lista archivos y muestra atributos._

> `ls -r` _lista los archivos en orden Z A._

> `ls -l` _Documents lista directamente el contenido de una carpeta._

## Combinaciones y variaciones

> `ls -l -r`

> `ls -rl`

> `ls -lr`

## Mostrar donde estoy parado

> `pwd` _muestra donde estoy parado._

> `cd ..` _retroceder un directorio._

> `cd ~` _directorio principal del usuario._

## Ordenar archivos

> `ls -l -t /ruta-directorio` _ordena archivos por sello de tiempo._

> `ls -l -S /ruta-directorio` _ordena archivos por tamaño._

> `ls -lSr /ruta-directorio` _invierte el orden de cualquier tipo de ordenación._

> `ls -r /ruta-directorio` _invierte los archivos por orden alfabético._

[☝️](#contenido)

<hr>

# ACCESO ADMINISTRATIVO

<!-- La contraseña de práctica es: netlab123 -->

## Especificar el inicio de sesión en la shell como root

> `su -` _inicia sesión como root._

> `su -l` _inicia sesión como root._

> `su --login` _inicia sesión como root._

> `logout` _cierra sesion como root._

> `exit` _vover al usuario previo al root._

## SUDO

Permite ejecutar comandos como otro usuario sin tener que crear un nuevo shell
sudo -u también se utiliza para cambiar a otras cuentas de usuario.

**_Ejemplo:_**

> `sudo sl` _muestra la locomotora en la CLI._

[☝️](#contenido)

<hr>

# PERMISOS DE LOS ARCHIVOS

**Método simbólico**

`chmod [<CONJUNTO DE PERMISOS><ACCIÓN><PERMISOS>]... ARCHIVO`

## Conjunto de Permisos

> `u` _Usuario propietario del archivo._
>
> `g` _Grupo propietario del archivo._
>
> `o` _Otros._
>
> `a` _Todos._

## Acción

> `-` _añadir permiso, si es necesario._
>
> `=` _especificar el permiso exacto._
>
> `*` _eliminar el permiso, si es necesario._

## Permisos

> `r` _leer (read)._
>
> `w` _escribir (write)._
>
> `x` _ejecutar (execute)._

## ... ARCHIVO

Ruta y nombre para los archivos a los que se quiere asignar los permisos.

<hr>

### **_TEMA APARTE, NO TAN APARTE_**

> `./` Esto indica que el “comando” debe ejecutarse desde el directorio actual.
>
> `./hello.sh` _ejecutar un script (ejemplo)._

<hr>

**_Ejemplo:_**

> Dando permiso de ejecución al usuario actual.
>
> `chmod u+x hello.sh`

## Cambiar el propietario de un archivo

Puede ser realizado por el usuario root o el propietario del archivo.

> `chown` _cambia el propietario de los archivos y directorios._

**SINTAXIS de chown**

`chown [PROPIETARIO] ARCHIVO`

El primer argumento especifica al usuario que debe ser el nuevo propietario del archivo.

El segundo argumento especifica a cual archivo se esta cambiando de propietario.

**_Ejemplo:_**

> `sudo chown root hello.sh`

[☝️](#contenido)

<hr>

# VISUALIZACIÓN DE ARCHIVOS

## cat

> `cat` _Permite ver el contenido de archivos pequeños._

SINTAXIS de cat:

> `cat [ARCHIVO]`

**_Ejemplo:_**

> `cat animals.txt`

## head

> `head [ARCHIVO]` _Permite visualizar las primeras lineas de un archivo._

> `head -n 3 [ARCHIVO]` _Especifica la cantidad de lineas a mostrar._

## tail

> `tail [ARCHIVO]` _Permite visualizar las últimas lineas de un archivo._

> `tail -n 3 [ARCHIVO]` _Especifica la cantidad de lineas a mostrar_

[☝️](#contenido)

<hr>

# COPIAR ARCHIVOS

> `cp [OPCIONES] ORIGEN DESTINO` _copiar archivos._

**_Ejemplo:_**

> `(.)` El punto significa el directorio actual. En este ejemplo se esta copiando un archivo al directorio actual:
>
> `cp /etc/passwd .`

> [!NOTE]
>
> **_A tener en cuenta:_**
>
> Los permisos pueden afectar a los comandos de administración de archivos, como el comando `cp`. Para copiar un archivo, es necesario tener permiso de ejecución para acceder al directorio donde se encuentra el archivo y permiso de lectura para el archivo que se está copiando.

[☝️](#contenido)

<hr>

# CLONAR UN DISCO

> `dd` El comando dd se utiliza para copiar archivos o particiones enteras al nivel de bits.
>
> Se puede usar para copiar datos no procesados (raw) a dispositivos extraíbles como dispositivos USB o CD ROMS.
>
> `dd if=/dev/sda of=/dev/sdb` clonar de un disco duro **(/dev/sda)** a otro **(/dev/sdb)**
>
> | Comando                    | Disco Origen | Disco Destino |
> | -------------------------- | ------------ | ------------- |
> | dd if=/dev/sda of=/dev/sdb | /dev/sda     | /dev/sdb      |

[☝️](#contenido)

<hr>

# MOVER ARCHIVOS

> `mv ORIGEN DESTINO`

**_Ejemplo:_**

> `mv people.csv Work`
>
> _Moviendo un archivo a un directorio conservando su nombre._

**_Ejemplo:_**

_Moviendo varios archivos a un directorio._

> `mv Apuntes-Linux.md Apuntes-Networks.md /home/jonvzcas/Documents`
>
> El último argumento es el destino.

## Forma de cambiar el nombre a un archivo

> `mv animals.txt zoo.txt` _Si se mueve dentro del mismo directorio es una forma de cambiarle de nombre._

> [!NOTE]
>
> **_A tener en cuenta:_**
>
> Los permisos pueden afectar comandos de administración de archivos, incluyendo el comando mv. Mover un archivo requiere tener permisos de escritura y ejecución tanto en los directorios de origen como de destino.

[☝️](#contenido)

<hr>

# ELIMINAR ARCHIVOS

> `rm [OPCIONES] ARCHIVO` _Sin ninguna opción el comando se utiliza para eliminar archivos ordinarios._

**_Ejemplo:_**

> `rm linux.txt`
>
> `rm -r o -R DIRECTORIO` _Elimina de forma recursiva a todos los subdirectorios y archivos contenidos en el DIRECTORIO_

> [!NOTE]
>
> **_A tener en cuenta:_**
>
> Los permisos pueden afectar a los comandos de administración de archivos, como el comando rm.
> Para eliminar un archivo dentro de un directorio, el usuario debe tener permiso de escritura y ejecución en
> ese directorio. Normalmente, los usuarios ordinarios solo tienen este tipo de permiso en su directorio principal
> y subdirectorios correspondientes.

[☝️](#contenido)

<hr>

# FILTRADO DE ENTRADAS

## grep

El comando `grep` es un filtro de texto que busca líneas en una entrada y devolverá aquellas que coincidan con un patrón determinado.

> `grep [OPCIONES] PATRÓN [ARCHIVO]`

**_Ejemplo:_**

> `grep sysadmin passwd`

## Expresiones regulares

Son una de las formas con que se pueden utilizar expresiones regulares para limitar los resultados de una búsqueda.

Por ejemplo el patrón root aparece muchas veces en el archivo "`/etc/passwd`".

> `grep 'root' passwd`
>
> El patrón se escribe en comillas sólidas para evitar que el shell malinterprete como caracteres especiales.

### **_Caracteres de anclaje_**

**Caracter de anclaje ^**

Se utiliza para indicar que el patrón debe de aparecer al principio de la linea.

**_Ejemplo:_**

> `grep '^root' /etc/passwd`
>
> ---
>
> Output: `root:x:0:0:root:/root:/bin/bash`

**Caracter de anclaje $**

Se utiliza para indicar que el patrón debe aparecer al final de la linea.

**_Ejemplo:_**

> Encontrar las lineas que terminan en "r" en el archivo `alpha-first.txt`
>
> `grep 'r$' alpha-first.txt`
>
> ---
>
> Output:
>
> `B is for Bear`
>
> `F is for Flower`

**Caracter Punto (.)**

Representa cualquier carácter excepto el carácter de nueva línea.

**_Ejemplo:_**

> `grep r..f red.txt`
>
> ---
>
> Output:
>
> `reed`
>
> `read`

**_Ejemplo:_**

> `grep '.....' red.txt`
>
> Output:
>
> `reeed`
>
> _Encuentra todas las palabras de al menos cuatro caracteres._

**Expresión [0-9] ó [0123456789]**

Encuentra todas las líneas que contengan un número.

**_Ejemplo:_**

> `grep [0-9] profile.txt`
>
> ---
>
> Output:
>
> Hello my name is Joe.
>
> I am **37** years old.
>
> **3121991**
>
> My favorite food is avocados.
>
> I have **2** dogs.
>
> **123456789101112**

**Expresión [^0-9]**

Encuentra líneas con caracteres no numéricos.

**_Ejemplo:_**

> `grep [^0-9] texto-prueba1.txt`
>
> ---
>
> Output:
>
> `Lorem Ipsum is simply dummy`
>
> `text of the printing and`
>
> _Contenido original del archivo:_
>
> `123`
>
> `Lorem Ipsum is simply dummy`
>
> `456`
>
> `text of the printing and`

**Expresión [.]**

Solo las líneas que contienen el carácter adentro de los corchetes `[.]` se mostraran en el resultado.

Cuando otros caracteres de expresión regular se colocan dentro de corchetes, se tratan como carácteres
literales.

El carácter `[.]` normalmente indica cualquier carácter, pero si se coloca dentro de corchetes
simplemente se referirá al carácter `. (punto)`. En el siguiente ejemplo, sólo las líneas que contienen el carácter `[.]` se mostrarán en el resultado.

**_Ejemplo:_**

> `grep '[.]' profile.txt`
>
> ---
>
> Output:
>
> `Hello my name is Joe🫴.`  
> `I am 37 years old🫴.`  
> `My favorite food is avocados.`  
> `I have 2 dogs🫴.`

**El carácter de expresión regular `*`**

El carácter de expresión regular `*` se utiliza para indicar la ausencia o la presencia una o más veces del carácter o patrón que lo precede.

**_Ejemplo:_**

Tenemos el siguiente archivo

> `cat texto-prueba2.txt`
>
> Output:
>
> zooarqueología  
> zoófago  
> zoofili  
> zoófito  
> zooftirio
>
> ---
>
> _Se pretende encontrar las palabras que inicien con `'z'` y que contengan almenos una `'ó'`_
>
> `grep z*ó texto-prueba2.txt`
>
> Output:
>
> zo`ó`fago  
> zo`ó`fito

También es posible indicar la presencia de una o más veces de una lista de caracteres utilizando los corchetes.

**_Ejemplo:_**

El patrón [ft] en el archivo texto-prueba2.txt

> `grep 'z*[ft]' texto-prueba2.txt`
>
> Output:
>
> zoó`f`ago  
> zoo`f`ili  
> zoó`f`ito  
> zoo`ft`irio

[☝️](#contenido)

<hr>

# APAGAR

`shutdown [OPCIONES] HORA [MENSAJE]`

El comando `shutdown` prepara el sistema para un apagado seguro. Todos los usuarios que han iniciado una sesión reciben la notificación de que el sistema se esta apagando y se evitan nuevos inicios de sesión en lso cinco minutos previos al apagado completo del sistema.

> ![NOTE]
>
> El comando `shutdown` requiere acceso administrativo.

**_Ejemplo:_**

> `root@localhost:~# shutdown now`

A diferencia de otros comandos utilizados para apagar el sistema, el comando `shutdown`requiere un argumento de tiempopara especificar cuándo debe comenzar el apagado. Los formatos de este argumento de tiempo pueden ser la palabra `now` (ahora), una hora del día en el formato `hh:mm` o el número de minutos de retraso utilizando el formato +_minutos_ .

El reloj de nuestro sistema puede estar configurado en una zona horaria diferente a la que uno se encuentra. Para verificar la hora en la terminal, use el comando `date`. En nuestras maquinas, el formato predeterminado de la salida del comando `date`es el siguiente:

`dia_de_la_semana mes hora:minuto:segundo UTC año`

> `Wed Jun 7 03:07:37 UTC 2023`

Las letras UTC presentes en la salida indican que la hora se muestra de acuerdo con el Horario Coordinado Universal.

> `shutdown 03:08`

El comando `shutdown`también posee la opción de añadir un mensaje como argumento. Este mensaje aparecerá en las terminales de todos los usuarios.

**_Ejemplo:_**

> `shutdown +1 "Goodbye World"`

[☝️](#contenido)

<hr>

# CONFIGURACIÓN DE REDES

El comando ifconfig significa "configuración de interfaz" _(interface configuration)_ y se utiliza para mostrar información sobre la configuración de red.

> `ifconfig [OPCIONES]`

> ![NOTE]
>
> El comando `iwconfig` es similar al comando `ifconfig`, pero se refiere a interfaces de redes inalámbricas (_wireless_).

**_Ejemplo:_**

En el siguiente ejemplo la dirección IPv4 del dispositivo de red principal eth0 es 192.168.1.2 y el dispositivo esta activo (UP):

> `ifconfig`
>
> Output:

    eth0      Link encap:Ethernet  HWaddr 02:42:c0:a8:01:02
              inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
              UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
              RX packets:36 errors:0 dropped:0 overruns:0 frame:0
              TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:1000
              RX bytes:2736 (2.7 KB)  TX bytes:2060 (2.0 KB)

El comando `ifconfig` también se puede utilizar para modificar temporalmente la configuración de red. Normalmente estos cambios deben ser permanentes, por lo que raramente se usa el comando `ifconfig`para realizar dichos cambios.

El comando `ping` se utiliza para verificar la conectividad entre dos equipos. Para hacer esto, envía paquetes a otra maquina a través de una red. Para que los paquetes encuentren la otra computadora, necesitan una dirección. El comando `ping` utiliza direcciones IP para identificar un equipo en la red al que desea conectarse.

De forma predeterminada, el comano `ping`continuará enviando paquetes hasta que se introduzca el comando break (**CTL+C**) en la consola. Para limitar el número de pings que se desea enviar, utilizar la siguiente forma:

> `ping direccion-ip -c numero-de-veces`

**_Ejemplo:_**

> `ping 192.168.1.2 -c 5`
>
> Output:
>
> ---
>
> PING 192.168.1.2 (192.168.1.2) 56(84) bytes of data.  
> 64 bytes from 192.168.1.2: icmp_seq=1 ttl=64 time=0.060 ms  
> 64 bytes from 192.168.1.2: icmp_seq=2 ttl=64 time=0.037 ms  
> 64 bytes from 192.168.1.2: icmp_seq=3 ttl=64 time=0.037 ms  
> 64 bytes from 192.168.1.2: icmp_seq=4 ttl=64 time=0.038 ms  
> 64 bytes from 192.168.1.2: icmp_seq=5 ttl=64 time=0.037 ms
>
> --- 192.168.1.2 ping statistics ---  
> 5 packets transmitted, 5 received, 0% packet loss, time 4085ms  
> rtt min/avg/max/mdev = 0.037/0.041/0.060/0.012 ms

Si el comando `ping` falla, recibirá un mensaje indicando que no se encontró el computador de destino o máquina remota ( Destination Host Unreachable ):

**_Ejemplo:_**

> `ping 192.168.1.3 -c 5`
>
> Output:
>
> ---
>
> PING 192.168.1.3 (192.168.1.3) 56(84) bytes of data.  
> From 192.168.1.2 icmp_seq=1 Destination Host Unreachable  
> From 192.168.1.2 icmp_seq=2 Destination Host Unreachable  
> From 192.168.1.2 icmp_seq=3 Destination Host Unreachable  
> From 192.168.1.2 icmp_seq=4 Destination Host Unreachable  
> From 192.168.1.2 icmp_seq=5 Destination Host Unreachable  
> --- 192.168.1.3 ping statistics ---  
> 5 packets transmitted, 0 received, +5 errors, 100% packet loss, time 4091ms  
> pipe 4

El comando `ping` puede fallar aunque la máquina remota esté conectada a la red. Esto se debe a que, como medida de seguridad, algunos administradores configuran sus equipos, o incluso redes enteras, para que no respondan a solicitudes `ping`. El comando `ping` tambièn funciona con un nombre de host, o con un nombre de dominio como yahoo.com. Usar esto primero puede ahorrar tiempo, ya que si ese comando `ping` tiene éxito, indica que hay una resolución de nombre adecuada Y que la dirección IP también funciona correctamente.

[☝️](#contenido)

<hr>

# VISUALIZACIÓN DE PROCESOS

Ejecutar un comando da como resultado algo llamado _proceso_. En el sistema operativo Linux, los procesos se ejecutan en función de los privilegios del usuario que ejecuta el comando. Esto permite que los procesos se limiten a ciertas funciones dependiendo de la identidad del usuario.

Aunque hay excepciones, generalmente el sistema operativo diferenciará entre los usuarios en función de si son o no el administrador. Normalmente, los usuarios habituales, como el usuario sysadmin, no pueden controlar los procesos de otro usuario. Los usuarios que tienen privilegios administrativos, como la cuenta root, pueden controlar cualquier proceso de cualquier usuario, incluyendo la detención de cualquier proceso.

El comando `ps`se puede utilizar para enumerar procesos.

`ps [OPCIONES]`

`ps`

Output:

    PID TTY          TIME CMD
     87 pts/0    00:00:00 bash
    104 pts/0    00:00:00 ps

Por defecto, el comando `ps` mostrará los procesos que se están ejecutando en la terminal actual. En el ejemplo anterior, la última línea corresponde al proceso generado al ejecutar el comando `ps`. La salida incluye las siguientes columnas de información:

- PID : El identificador para el procesos (_process identifier_), el cual es único para cada proceso. Esta información es útil cuando necesitamos controlar los procesos según su número indentificador (_ID_).

- TTY : El nombre de la terminal en la que está funcionando el proceso. Esta información es útil para distinguir entre diferentes procesos que tienen el mismo nombre.

- TIME : La cantidad total de tiempo de procesado que utiliza un proceso.

- CMD : El comando que inició el proceso.

En lugar de ver sólo los procesos que se están ejecutando en la terminal actual, los usuarios pueden querer ver todos los procesos que se están ejecutando en el sistema. La opción `-e`muestra todos estos procesos:

`ps -e`

Output:

    PID TTY           TIME CMD
     1  pts/0     00:00:00 init
    33  ?         00:00:00 rsyslogd
    37  ?         00:00:00 cron
    39  ?         00:00:00 sshd
    56  ?         00:00:00 named
    77  pts/0     00:00:00 login
    87  pts/0     00:00:00 bash
    105 pts/0     00:00:00 ps

Muchas veces se puede utilizar la opción `-f` proporcionar un resultado más detallado que incluya las opciones y los argumentos de cada proceso.

**_Ejemplo:_**

Localice el comando `ps` en la última línea, la columna CMD ahora incluye las opciones utilizadas con el comando:

`ps -ef`

Output:

    UID        PID  PPID  C STIME TTY          TIME CMD
    root         1     0  0 19:16 pts/0        00:00:00 /sbin??? /init
    syslog      33     1  0 19:16 ?            00:00:00 /usr/sbin/rsyslogd
    root        37     1  0 19:16 ?            00:00:00 /usr/sbin/cron
    root        39     1  0 19:16 ?            00:00:00 /usr/sbin/sshd
    bind        56     1  0 19:16 ?            00:00:00 /usr/sbin/named -u bind
    root        69     1  0 19:16 pts/0        00:00:00 /bin/login -f
    sysadmin    79    69  0 19:16 pts/0        00:00:00 -bash
    sysadmin    95    79  0 19:43 pts/0        00:00:00 ps -ef

[☝️](#contenido)

<hr>

# ADMINISTRACIÓN DE PAQUETES

La administración de paquetes es un sistema mediante el cual un software puede ser instalado, actualizado, consultado o eliminado de un sistema de archivos. En linux, hay muchos sistemas de gestión de paquetes de software diferentes, pero los dos más populares son Debian y Red Hat.

En el nivel más bajo del sistema administración de paquetes Debian se encuentra el comando `dpkg`.

La herramienta Advanced Package Tool, `apt-get`, un programa front-end para la herramienta dpkg, facilita la gestión de paquetes.

## Instalación de paquetes

Los paquetes de archivos normalmente se instalan por descarga directa desde repositorios ubicados en servidores de Internet. Los repositorios Debian contienen más de 65.000 paquetes de software diferentes. Antes de instalar un paquete, es recomendable actualizar la lista de paquetes disponibles usando el comando `apt-get update`.

> `sudo apt-get update`

Para buscar palabras clave (_keyword_) dentro de estos paquetes, puede utilizar el comando `apt-cache search`.

> `apt-cache search [keyword]`

La palabra clave que se utiliza debe conincidir con parte del nombre o descripción del paquete que se intenta localizar. Se pueden usar varias palabras claves para especificar aún más la búsqueda; por ejemplo, el termino de búsqueda web server proporcionará mejores resultados que web o server.

**_Ejemplo:_**

Para buscar paquetes asociados con la palabra clave cow :

> `apt-cache search cow`
>
> Output:
>
> `cowsay - configurable talking cow`

Una vez encontrado el paquete (_package_) que desea instalar, puede utilizar el comando apt-get install [_package_] para instalarlo:

> `sudo apt-get install [_package_]`

**_Ejemplo:_**

> `sudo apt-get install cowsay`

El comando `cowsay` es una vaca parlante configurable! Use una palabra o frase como argumento:

> `cowsay 'Hola Jonvzcas!'`
>
> Output:

---

< Hola Jonvzcas! >

---

        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||

> ![NOTE]
>
> Es recomendable incluir entre comillas simples el argumento para evitar que el shell interprete caracteres especiales.

## Actualización de paquetes

El comando `apt-get install` también puede actualizar un paquete, si ese paquete ya esta instalado y existe una versión más reciente disponible. Si el paquete aún no esta en el sistema, se instalará; si está en el sistema, se actualizará.

La actualización de todos los paquetes del sistema debe realizarse en dos pasos. Primero, actualice la cache de todos los paquetes disponibles utilizando `apt-get upgrade` para actualizar todos los paquetes y sus dependencias.

> `apt-get update` se actualiza la caché
>
> `apt-get upgrade` se actualizan todos los paquetes y sus dependencias

## Eliminación de paquetes

El comando `apt-get` puede eliminar o purgar un paquete. La diferencia entre los dos es que purgar suprime todos los archivos del paquete, mientras que eliminar suprime todos los archivos del paquete excepto los archivos de configuración.

Un administrador puede ejecutar el comando `apt-get remove` para eliminar un paquete o el comando `apt-get purge` para purgar un paquete completamente del sistema.

> `apt-get remove [package]`
>
> `apt-get purge [package]`

**_Por ejemplo:_**

Para purgar `cowsay` por ejemplo, ejecute el siguiente comando.

Escriba **Y** cuando se le solicite:

[☝️](#contenido)

<hr>

# ACTUALIZACIÓN DE CONTRASEÑAS DE USUARIO

El comando `passwd` se utiliza para actualizar la contraseña de un usuario.

> `passwd [OPCIONES] [USUARIO]`

**_Ejemplo:_**

    sysadmin@localhost:~$ passwd
    Changing password for sysadmin.
    (current) UNIX password: netlab123
    Enter new UNIX password:
    Retype new UNIX password:
    passwd: password updated successfully

`passwd -S nombre_usuario` : Permite ver información sobre la contraseña.

**_Ejemplo:_**

    sysadmin@localhost:~$ passwd -S sysadmin
    sysadmin P 12/20/2017 0 99999 7 -1

Los campos de salida se explican a continuación:

| Campo                   | Ejemplo    | Significado                                                                                                                    |
| ----------------------- | ---------- | ------------------------------------------------------------------------------------------------------------------------------ |
| Nombre del usuario      | sysadmin   | El nombre del usuario                                                                                                          |
| Estado de la contraseña | P          | P indica que es una contraseña utilizable.<br> L indica que la contraseña esta bloqueada.<br> NP indica que no hay contraseña. |
| Fecha de actualización  | 12/20/2017 | La fecha en que la contraseña fue actualizada por última vez.                                                                  |
| Mínimo                  | 0          | El número mínimo de días que deben pasar antes de que el usuario pueda cambiar la contraseña actual.                           |
| Máximo                  | 99999      | El máximo número de días que restan hasta que expire la contraseña.                                                            |
| Aviso                   | 7          | El número de días precedentes a la contraseña para que el usuario reciba el aviso.                                             |
| Inactividad             | -1         | El número de días después de la expiración de la contraseña que la cuenta del usuario se mantendrá activa.                     |

El usuario root puede cambiar la contraseña de otro usuario.

    root@localhost:~# passwd sysadmin
    Enter new UNIX password:
    Retype new UNIX password:
    passwd: password updated successfully

[☝️](#contenido)

<hr>

# REDIRECCIÓN

En Linux, se puede agregar contenido a un archivo rápidamente usando una función de línea de comandos llamada redirección de entrada/salida (E/S) (input/output; I/O).

> ![NOTE]
>
> La redirección E/S (I/O) permite enviar la información de la línea de comandos a archivos, dispositivos y otros comandos.

La entrada o salida de un comando se redirige desde su destino predeterminado a una ubicación diferente. La redirección E/S es como una serie de vías de tren, donde se puede habilitar un conmutador para dirigir la salida de un comando a una vía diferente que vaya a otro lugar en el shell.

Cuando se trata de comandos de entrada y salida, existen tres rutas, o “vías”. Estas rutas se denominan descriptores de archivos.

**El primer descriptor** de archivo es la entrada estándar, abreviada como STDIN (standard input). La entrada estándar es la información que el comando recibe y procesa cuando se ejecuta, esencialmente lo que un usuario escribe en el teclado.

**El segundo descriptor** de archivo es la salida estándar, abreviada como STDOUT (standard output). La salida estándar es la información que muestra el comando, la salida del comando. El último descriptor de archivo es el error estándar, abreviado como STDERR (standard error). STDERR, son los mensajes de error generados por comandos que no se ejecutan correctamente. Los siguientes son ejemplos de cómo aparecerán los descriptores de archivos en la terminal:

**Entrada estándar (STDIN)**

    sysadmin@localhost:~$ ls ~/Documents
    School           alpha-second.txt  food.txt     linux.txt     os.csv
    Work             alpha-third.txt   hello.sh     longfile.txt  people.csv
    adjectives.txt   alpha.txt         hidden.txt   newhome.txt   profile.txt
    alpha-first.txt  animals.txt       letters.txt  numbers.txt   red.txt

**Salida estándar (STDOUT)**

    sysadmin@localhost:~$ ls
    Desktop  Documents  Downloads  Music  Pictures  Public  Templates  Videos

**Error stándar (STDERR)**

    sysadmin@localhost:~$ ls fakefile
    ls: cannot access fakefile: No such file or directory

Esta sección cubrirá uno de los tres descriptores de archivos, STDOUT, y cómo redirigir STDOUT desde donde normalmente aparece en el terminal, a un archivo en el sistema de archivos. Para ejecutar la redirección, simplemente use el símbolo “mayor que” `>` junto al nombre del archivo:

> `[COMANDO] > [ARCHIVO]`

Para demostrar cómo funciona la redirección, usaremos la salida del comando cat. Sin redirección, la salida del comando cat se mostrará en el terminal:

    sysadmin@localhost:~/Documents$ cat food.txt
    Food is good.

Ahora utilice el carácter > para redirigir el STDOUT del comando `cat food.txt` anterior a un nuevo archivo llamado `newfile1.txt`:

    sysadmin@localhost:~/Documents$ cat food.txt > newfile1.txt

Como puede ver, no se muestra ninguna salida ya que el STDOUT se ha redirigido al archivo `newfile1.txt`. Compruebe que el STDOUT del comando `cat food.txt` se encuentra en `newfile1.txt`:

    sysadmin@localhost:~/Documents$ cat newfile1.txt
    Food is good.

> ![NOTE]
>
> Esta función es útil si necesita copiar contenido de un archivo importante a otro archivo para editar su contenido sin modificar el archivo original.

Sin embargo, ¿qué sucede si desea **agregar un comentario** o una nota a un archivo ya existente? Para hacer esto, puede usar el comando `echo`. El comando `echo` se utiliza para imprimir una salida en la terminal:

    sysadmin@localhost:~/Documents$ echo "Hello"
    Hello

Imprimir comentarios en la pantalla es una función curiosa, pero el comando `echo` puede ser más útil cuando se usa con la redirección. Mediante el comando `echo`, puede agregar contenido al archivo `newfile1.txt`:

    sysadmin@localhost:~/Documents$ cat newfile1.txt
    Food is good.

>

    sysadmin@localhost:~/Documents$ echo "I like food." > newfile1.txt

>

    sysadmin@localhost:~/Documents$ cat newfile1.txt
    I like food.

> ![Observe]
>
> que el STDOUT del comando echo ha reemplazado el contenido original del archivo. Esto se debe a que **el carácter > sobrescribe cualquier contenido de un archivo existente**.
>
> Para añadir contenido a un archivo, en lugar de sobrescribir, utilice el símbolo “mayor que” dos veces `>>`:

    sysadmin@localhost:~/Documents$ echo "And I want to eat now" >> newfile1.txt

>

    sysadmin@localhost:~/Documents$ cat newfile1.txt
    I like food.
    And I want to eat now

> ![Importante]
>
> Para redirigir la información a un archivo existente, el usuario debe tener permisos de escritura para ese archivo.

[☝️](#contenido)

<hr>

# EDITOR DE TEXTO

Se recomienda instalar `vim` ya que quizas no este instalado en la distribución.

> `sudo apt-get update`
>
> `sudo apt install vim`

El principal editor de texto para Linux y UNIX es un programa llamado `vi`. Si bien hay numerosos editores disponibles para Linux incluyendo desde el pequeño editor nano hasta el editor masivo emacs, el editor `vi` tiene varias ventajas:

El editor `vi` está disponible en todas las distribuciones Linux del mundo. Esto no ocurre con ningún otro editor.

El editor `vi` se puede ejecutar tanto en una CLI (interfaz de línea de comandos) como en una GUI (interfaz gráfica de usuario).

Aunque se han añadido nuevas características al editor `vi`, las funciones principales han existido durante décadas. Esto significa que si alguien aprendió a usar el editor `vi` en la década de 1970, podrá usar la versión moderna sin ningún problema. Aunque eso pueda parecer trivial, puede que dentro de veinte años no sea tan trivial.

> ![A tener en cuenta]
>
> La forma correcta de pronunciar el nombre del editor `vi` es vi-ay. Las letras `vi`representan visual, pero nunca se pronunció de esta manera. En su lugar se pronuncia la letra v (vi) seguida de la letra i (ay) en inglés.

En realidad, la mayoría de los sistemas Linux no incluyen el editor `vi` original, sino una versión mejorada del mismo conocida como `vim` (vi mejorada) (vi improved). Este hecho puede estar oculto en la mayoría de las distribuciones de Linux. En su mayor parte, `vim` funciona igual que vi, pero presenta funciones adicionales. Para los temas que se tratan en este curso, tanto vi como `vim` funcionarán perfectamente

Para comenzar a usar `vi`, simplemente escriba el comando seguido del nombre de ruta del archivo que quiere editar o crear:

> sysadmin@localhost:~$ `vi newfile.txt`

Los tres modos utilizados en vi son los siguientes:

- Modo de Comando
- Modo de Inserción
- Modo Ex

## Modo de comando: Movimiento

Inicialmente, el programa empieza en modo de comando. El modo de comando se utiliza para escribir comandos, como los utilizados para desplazarse por un documento, manipular texto o acceder a los otros dos modos. Para volver al modo de comando en cualquier momento, presione la tecla **Esc**.

Una vez haya agregado texto a un documento, deberá presionar la tecla **Esc** para volver al modo de comando y realizar acciones como mover el cursor.

![cap-one](./Image/Writting-on-vim.png "Escribiendo en vim")

Los comandos de movimiento en vi tienen dos aspectos, el movimiento (_motion_) y un prefijo numérico opcional (_count_) que indica cuántas veces se debe repetir ese movimiento. El formato general es el siguiente:

> `[numero] movimiento`

En la siguiente tabla se resumen las teclas de movimiento disponibles:

| Movimiento | Resultado                 |
| ---------- | ------------------------- |
| h          | Un caráter a la izquierda |
| j          | A la línea siguiente      |
| k          | A la línea anterior       |
| l          | Un carácter a la derecha  |
| w          | Una palabra adelante      |
| b          | Una palabra hacia atrás   |
| ^          | Al principio de la línea  |
| $          | Al final de la línea      |

> ![Nota]
>
> En la actualización vim también es posible usar las teclas de flecha ← ↓ ↑ → en lugar de los caracteres h j k l respectivamente.

Estos movimientos se pueden anteponer con un número para indicar cuántas veces se debe realizar el movimiento. Por ejemplo, `5h` moverá el cursor cinco caracteres a la izquierda y `3w` moverá el cursor tres palabras a la derecha.

Para mover el cursor a un número de línea específico, escriba ese número de línea seguido del carácter `G`. Por ejemplo, para llegar a la quinta línea del archivo, escriba `5G`. Puede usar `1G` o `gg` para moverse a la primera línea del archivo, mientras que una `G` única le llevará a la última línea.
Para averiguar en qué línea se encuentra el cursor, utilice **CTRL+G**.

## Modo de comando: Acciones

La convención estándar para editar contenido con procesadores de texto es usando copiar, cortar y pegar. El programa vi no tiene ninguno de estos. En su lugar, vi utiliza los tres comandos siguientes:

| Estándar | Vi   | Significado         |
| -------- | ---- | ------------------- |
| cortar   | d    | eliminar (_delete_) |
| copiar   | y    | sacar (_yank_)      |
| pegar    | P\|p | poner (_put_)       |

> ![A tener en cuenta]
>
> Los movimientos aprendidos en la página anterior se utilizan para especificar **_dónde se llevará a cabo la acción_ ⚓**, comenzando siempre con la ubicación actual del cursor. Cualquiera de los siguientes formatos generales es aceptable para comandos de acción:
>
> `accion [número] movimiento`  
> `[número] acción movimiento`

### Eliminar

Eliminar (_delete_) suprime el texto indicado de la página y lo guarda en el búfer, siendo el búfer el equivalente al “portapapeles” (_clipboard_) utilizado en Windows o Mac OSX. En la siguiente tabla se proporcionan algunos ejemplos de uso comunes:

| Acción | Resultado                                    |
| ------ | -------------------------------------------- |
| dd     | Elimina la línea actual                      |
| 3dd    | Elimina las tres líneas siguientes           |
| dw     | Elimina la palabra actual                    |
| d3w    | Elimina las tres palabras siguientes         |
| d4h    | Elimina cuatro carácteres hacia la izquierda |

### Cambiar

La función cambiar (_change_) es muy similar a la de eliminar; el texto se elimina y se guarda en el búfer. Sin embargo, el programa cambia a modo de inserción y permite la introducción de cambios inmediatos en el texto. En la siguiente tabla se proporcionan algunos ejemplos de uso comunes:

| Acción | Resultado                                   |
| ------ | ------------------------------------------- |
| cc     | Cambiar la línea actual                     |
| cw     | Cambiar la palabra actual                   |
| c3w    | Cambiar las tres palabras siguientes        |
| c5h    | Cambiar cinco caracteres hacia la izquierda |

### Sacar

Sacar (_yank_) coloca el contenido en el búfer sin eliminarlo. En la siguiente tabla se proporcionan algunos ejemplos de uso comunes:

| Acción | Resultado                                                            |
| ------ | -------------------------------------------------------------------- |
| yy     | Sacar la línea actual                                                |
| 3yy    | Sacar las tres líneas siguientes                                     |
| yw     | Sacar la palabra actual                                              |
| y$     | Sacar el fragmento desde el cursor hasta el final de la línea actual |

### Poner

Poner (_put_) coloca el texto guardado en el búfer antes o después de la posición del cursor. Tenga en cuenta que estas son las dos únicas opciones, poner no utiliza movimientos como los comandos de acción anteriores.

| Acción | Resultado                        |
| ------ | -------------------------------- |
| p      | Poner o pegar después del cursos |
| P      | Poner antes del cursor           |

### Buscar en vi

Otra función estándar que ofrecen los procesadores de texto es la función de búsqueda (_find_). A menudo, las personas usan **CTRL+F** o miran en el menú de edición. El programa `vi` utiliza la búsqueda. La función de búsqueda es más potente que la función find porque admite patrones de texto literales y expresiones regulares.

Para buscar hacia adelante desde la posición actual del cursor, use la `/` para iniciar la búsqueda, escriba un término de búsqueda y, a continuación, presione la tecla **Enter** para iniciar la búsqueda. El cursor se moverá al primer resultado que coincida con su término de búsqueda.

Para proceder al siguiente resultado coincidente usando el mismo patrón, presione la tecla `n`. Para volver al resultado anterior, presione la tecla `N`. Si se alcanza el final o el comienzo del documento, la búsqueda se ajustará automáticamente para continuar con el resto del documento.

Para empezar a buscar desde la posición del cursor hacia atrás, empiece por escribir `?`, entonces escriba el patrón de búsqueda y presione la tecla Enter.

### Modo Insertar

El modo Insertar se utiliza para agregar texto a un documento. Hay algunas maneras de entrar en el modo de inserción desde el modo de comando, cada una diferenciada por donde comienza la inserción de texto. La siguiente tabla presenta los más comunes:

| Entrada | Función                                                   |
| ------- | --------------------------------------------------------- |
| a       | Comenzar a insertar justo despues del cursor              |
| A       | Comenzar a insertar al final de la linea                  |
| I       | Comenzar a insertar justo antes del cursor                |
| I       | Comenzar a insertar al principio de la línea              |
| o       | Comenzar a insertar en una nueva línea después del cursor |
| O       | Comenzar a insertar en una nueva línea antes del cursor   |

## Modo Ex

Originalmente, el editor `vi` se llamaba editor `ex`. El nombre `vi` era la abreviatura del comando visual en el editor `ex` que cambiaba el editor al modo “visual”.

| Entrada                 | Función                                                                    |
| ----------------------- | -------------------------------------------------------------------------- |
| :w                      | Escribir el documento actual al sistema de archivos                        |
| :w _nombre_del_archivo_ | Guardar una copia del documento actual bajo el nombre _nombre_del_archivo_ |
| :w!                     | Forzar escritura al documento actual                                       |
| :1                      | Ir a la primera línea (o otra línea indicada por el número)                |
| :e _nombre_del_archivo_ | Abrir _nombre_del_archivo_                                                 |
| :q                      | Suspender (salir) (_quit_) si no se han realizado cambios al documento     |
| :q!                     | Suspender sin guardar los cambios realizados al documento                  |

[☝️](#contenido)

<hr>

> ![Autores]
>
> Esto ha sido una recopilación de los apuntes más importantes del curso **NDG** Linux Unhatched contenido en **CISCO Network Academy** - 2023. Todos los derechos de autor pertenecen a estas compañías.
