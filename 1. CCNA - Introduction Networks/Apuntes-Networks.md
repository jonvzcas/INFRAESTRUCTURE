# APUNTES DE REDES Y CONFIGURACIÓN DE DISPOSITIVOS CISCO

# Contenido

[Modos de Ejecución](#modos-de-ejecución)  
[Modos de subconfiguración](#modos-de-subconfiguración)  
[Comandos básicos](#comandos-básicos)  
[Configuración básica de dispositivos](#configuración-básica-de-dispositivos)

# Modos de Ejecución

**Modo Usuario `>`**

Se utiliza para monitoreo y ningún cambio de configuración en el dispositivo.

**Modo Privilegiado `#`**

Permite realizar configuraciones en el dispositivo.

- **Modo de Configuración `global(config)`**

Se accede al modo de configuración global desde el **Modo Privilegiado `#`**

## Modos de subconfiguración

### Modo de subconfiguración`(config-line)`:

**Modos de configuración de lineas de comandos:**

- Consola
- SSH
- Acceso Auxiliar

### Modo de configuración de interfaz`(config-if)`:

para configurar un puerto del switch o una interfaz de red del router.

### Cambio de modos

🪄 `enable`: Este comando habilita el ingreso al Modo Privilegiado.

🖥️ `configure terminal`: Ingresa al modo de configuración global.

🏁 `exit`: De Configuración Global a ➡️ Modo Privilegiado.

🚫 `disable`: Regresa a ➡️ Modo Privilegiado.

🔚 `end`: De cualquier Modo de Subconfiguración a ➡️ Modo Privilegiado.

↩️`ctrl+Z`: De cualquier Modo de subconfiguración a ➡️ Modo Privilegiado.

### Cambiar de entre modos de subconfiguración

    	Switch(config)#line console 0
    	Switch(config-line)#interface FastEthernet 0/1
    	Switch(config-if)#line console 0
    	Switch(config-line)#

[☝️](#contenido)

<hr>

# Comandos básicos

**Comando `?`**

- Permite obtener información de sobre los comandos en cada modo y modos de subconfiguración.

- Muestra una lista de comandos o instrucciones disponibles.

- Muestra la sintaxis del argumento que se espera despues de escribir el comando.

**_Ejemplo de sintaxis:_**

> `com?`

_Al ingresar parte del comando y el signo de ayuda sin incluir un espacio, se muestra la lista de comandos que coinciden con la búsqueda._

## Algúnos comandos útiles

`Ctrl+R ó Ctrl+I ó Ctrl+L` : Vuelve a mostrar el indicador del sistema y la línea de comando después de que se muestra un mensaje de consola recibido.

`Ctrl+C` : Cuando está en cualquier modo de configuración, finaliza el modo de configuración y regresa al modo EXEC privilegiado.

Cuando está en modo de configuración, aborta de nuevo al comando como indicador de comandos.

`Ctrl+Z` : Cuando está en cualquier modo de configuración, finaliza el modo de configuración y regresa al modo EXEC privilegiado

`Ctrl+Shift+6` : Secuencia de interrupción multipropósito utilizada para anular búsquedas DNS, traceroutes, pings, etc.

`clock` : Permite configurar la fecha y la hora del dispositivo.

**_Ejemplo:_**

> `clock set 18:55:40 03 April 2023`

`show version` : Muestra versión del IOS.

[☝️](#contenido)

<hr>

# Configuración básica de dispositivos

## Nombres de los dispositivos

    	Switch# configure terminal
    	Switch(config)# hostname Sw-Floor-1
    	Sw-Floor-1(config)#

> [!NOTE]
>
> `no hostname`
>
> En configuración global devuelve al switch al indicador predeterminado.

## Configuración de contraseñas

**Modo de usuario**

Se protege configurando line console 0. El cero se utiliza para representar la primera (y en la mayoria de los casos la unica) interfaz de consola.

        Sw-Floor-1# configure terminal
        Sw-Floor-1(config)# line console 0
        Sw-Floor-1(config-line)# password cisco
        Sw-Floor-1(config-line)# login
        SW-Floor-1(config-line)# end
        Sw-Floor-1#

**Modo acceso privilegiado**

En configuración global se asegura utilizando el comando `'enable secret'`.

    	Sw-Floor-1# configure terminal
    	Sw-Floor-1(config)# enable secret class
    	Sw-Floor-1(config)# exit
    	Sw-Floor-1#

**Lineas de terminal virtual (VTY)**

Permiten el acceso remoto mediante Telnet o SSH al dispositivo. En configuración global se escribe el comando line vty 0 15

    	Sw-Floor-1# configure terminal
    	Sw-Floor-1(config)# line vty 0 15
    	Sw-Floor-1(config-line)# password cisco
    	Sw-Floor-1(config-line)# login
    	SW-Floor-1(config-line)# end
    	Sw-Floor-1#

## Encriptación de contraseñas

Los archivos `startup-config` y `running-config` muestran la mayoría de las contraseñas en texto simple.

Esta es una amenaza de seguridad porque cualquiera puede descubrir las contraseñas si tiene acceso a estos archivos.

Esta encriptación solo se aplica a las contraseñas del archivo de configuración, no a las contraseñas mientras se envían a través de los medios.

    	Sw-Floor-1(config)# service password-encryption
    	Sw-Floor-1(config)#

> [!NOTE]
>
> El propósito de este comando es evitar que individuos no autorizados vean las contraseñas en el archivo de configuración.
>
> `show running-config`
>
> Use el comando para verificar que las contraseñas estén ahora encriptadas.

## Mensajes de aviso

      Sw-Floor-1# configure terminal
      Sw-Floor-1(config)# banner motd #Authorized Access Only#

## Gestión del archivo de configuración

<hr>

**Visualizar configuraciones del dispositivo**

`show running-config`

Permite ver la configuración en ejecución.

`Sw-Floor-1# show startup-config`

Ver el archivo de configuración de inicio.

<hr>

**Guardar cambios de configuración**

`Sw-Floor-1# copy running-config startup-config` : Guardar cambios de configuración.

<hr>

**Regresar el dispositivo a la configuración anterior**

`Sw-Floor-1# reload` : Volver a cargar el dispositivo con la configuración anterior.

<hr>

**Eliminar la configuración de inicio del dispositivo**

**Pasos:**

1.Eliminar configuración de inicio.

> `Sw-Floor-1# erase startup-config`

2.Recarga el dispositivo para eliminar el archivo de configuración actual:

> `Sw-Floor-1# reload`

[☝️](#contenido)

<hr>
