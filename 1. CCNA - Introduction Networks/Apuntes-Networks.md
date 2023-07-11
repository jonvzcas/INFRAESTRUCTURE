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

`Ctrl+6` : Secuencia de interrupción multipropósito utilizada para anular búsquedas DNS, traceroutes, pings, etc.

`clock` : Permite configurar la fecha y la hora del dispositivo.

**_Ejemplo:_**

> En `>` ó `#` `show set` Muestra la fecha y la hora

> `#clock set 18:55:40 03 April 2023`

> `#show version` : Muestra versión del IOS.

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
Esto permite descartar cambios en el dispositivo si seleccionamos [yes/no]: no

<hr>

**Eliminar la configuración de inicio del dispositivo**

**Pasos:**

1.Eliminar configuración de inicio.

> `Sw-Floor-1# erase startup-config`

2.Recarga el dispositivo para eliminar el archivo de configuración actual:

> `Sw-Floor-1# reload`

[☝️](#contenido)

---

# Interfaces

## SVI (VLAN1)

La interfaz virtual le permite administrar de forma remota un switch a través de una red utilizando IPv4 e IPv6.

La SVI predeterminada es interfaz VLAN1.

Un switch de capa 2 no necesita una dirección IP. La dirección IP asignada a la SVI se utiliza para acceder al switch de forma remota.

### CONFIGURACIÓN DE INTERFAZ VIRTUAL DEL SWICH

> `#configure terminal`
>
> `(config)# interface vlan 1`
>
> `(config-if)# ip address 192.168.1.20 255.255.255.0`
>
> `(config-if)# no shutdown`
>
> `(config-if)# exit`
>
> `(config)# ip default-gateway 192.168.1.1`

## Verificar dirección IP interfaces y estado de puertos (show ip interface brief)

> `# show ip interface brief`

Seguir en 3.0.1 protocolos y modelos

[☝️](#contenido)

---

# Protocolos de comunicación

El envío de este mensaje, ya sea mediante comunicación cara a cara o a través de una red, está regido por reglas llamadas “protocolos”.

Los protocolos deben tener en cuenta los siguientes requisitos para entregar correctamente un mensaje que sea comprendido por el receptor:

- Un emisior y un receptor indentificados
- Idioma y gramatica común
- Velocidad y momento de entrega
- Requisitos de confirmación o acuse de recibo

## Requisitos del protocolo de red

- **Codificación de los mensajes**

  La codificación entre hosts debe tener el formato adecuado para el medio. El host emisor, primero convierte en bits los mensajes enviados a través de la red. Cada bit está codificado en un patrón de voltajes en cables de cobre, luz infrarroja en fibras ópticas o microondas para sistemas inalámbricos. El host de destino recibe y decodifica las señales para interpretar el mensaje.

- **Formato y encapsulamiento del mensaje**

  Un mensaje que se envía a través de una red de computadoras sigue reglas de formato específicas para que pueda ser entregado y procesado.

- **Tamaño del mensaje**

  Las restricciones de tamaño de las tramas requieren que el host de origen divida un mensaje largo en fragmentos individuales que cumplan los requisitos de tamaño mínimo y máximo. El mensaje largo se enviará en tramas independientes, cada trama contendrá una parte del mensaje original. Cada trama también tendrá su propia información de direccionamiento. En el host receptor, las partes individuales del mensaje se vuelven a unir para reconstruir el mensaje original.

- Sincronización del mensaje

  - **Control de flujo -** Este es el proceso de gestión de la velocidad de transmisión de datos. La sincronización también afecta la cantidad de información que se puede enviar y la velocidad con la que puede entregarse.

- Opciones de entrega el mensaje

  - **Tiempo de espera de respuesta (Response Timeout) -** Los hosts de las redes tienen reglas que especifican cuánto tiempo deben esperar una respuesta y qué deben hacer si se agota el tiempo de espera para la respuesta.

  - **El método de acceso-** Determina en qué momento alguien puede enviar un mensaje. Haga clic en Reproducir en la figura para ver una animación de dos personas hablando al mismo tiempo, luego se produce una "colisión de información" y es necesario que las dos retrocedan y comiencen de nuevo. Del mismo modo, cuando un dispositivo desea transmitir en una LAN inalámbrica, es necesario que la tarjeta de interfaz de red (NIC) WLAN determine si el medio inalámbrico está disponible.

## Tipos de comunicaciones de datos

- **Unicast -** La información se transmite a un único dispositivo final.

- **Multicast -** La información se transmite a uno o varios dispositivos finales.

- **Transmisión -** La información se transmite a todos los dispositivos finales.

# Funciones del protocolo de red

![protocolo-red](./Img/protocolo-red.png)

Los equipos y dispositivos de red utilizan protocolos acordados para comunicarse.

| Función                | Descripción                                                                                                                                                                                                                                                                                                   |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Direccionamiento       | Esto identifica al remitente y al destinatario previsto del mensaje utilizando un esquema de direccionamiento definido. IPV4 IPV6                                                                                                                                                                             |
| Confiabilidad          | Esta función proporciona mecanismos de entrega garantizados en caso de mensajes se pierden o se corrompen en tránsito. TCP proporciona entrega garantizada.                                                                                                                                                   |
| Control de flujo       | Esta función asegura que los datos fluyan a una velocidad eficiente entre dos dispositivos de comunicación. TCP proporciona servicios de control de flujo.                                                                                                                                                    |
| Secuenciación          | Esta función etiqueta de forma única cada segmento de datos transmitido. La utiliza la información de secuenciación para volver a ensamblar la información correctamente. Esto es útil si se pierdan los segmentos de dato, retrasado o recibido fuera de pedido. TCP proporciona servicios de secuenciación. |
| Detección de errores   | Esta función se utiliza para determinar si los datos se dañaron durante de la voz. Varios protocolos que proporcionan detección de errores incluyen Ethernet, IPv4, IPv6 y TCP.                                                                                                                               |
| Interfaz de aplicación | Esta función contiene información utilizada para proceso a proceso comunicaciones entre aplicaciones de red. Por ejemplo, al acceder a una página web, los protocolos HTTP o HTTPS se utilizan para comunicarse entre el cliente y servidor web.                                                              |

[☝️](#contenido)

---

Seguir en 3.3.1 Conjuntos de protocolos de red
