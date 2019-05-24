##Configuración

Para la configuracion de Heartbeat, lo primero que necesitaremos es la instalacion de dos maquinas virtuales, en nuestro caso...… 

```
Host u1
    User swap
    HostName 192.168.56.101

Host u2
    User swap
    HostName 192.168.56.102

Host nginx Active
    User swap
    HostName 192.168.56.121

Host nginx Pasive
    User swap
    HostName 192.168.56.122
```

Instalacion; `# apt-get install heartbeat-2`

Vamos a usar una arquitectura de alta disponibilidad a través de dos nodos, pero primero debemos asignar el nombre de los host y sus direcciones para poder hacer posible que se puedan comunicar entre ellos. Para ello accedemos a los siguientes archivos `/etc/hosts` y `/etc/hostname` de cada uno de nuestro nodos y les añadimos lo siguiente:

En ambos nodos:
```
#cat /etc/hosts
 ...
192.168.56.121 SwapNginxActive
192.168.56.122 SwapNginxPassive
```

Para el nodo 1 Activo:

```
#cat /etc/hostname
SwapNginxActive
```

Para el nodo 2 Pasivo:

```
#cat /etc/hostname
SwapNginxPassive
```

Asique comprobamos que puedan comunicarse haciendo ping de un nodo a otro.

(captura  ping_u2_to_u1)

Ahora vamos a instalar Heartbeat:

```bash
sudo apt-get install heartbeat -y
```

Despues de intalar vamos a habilitarlos para que se inicien con el sistema.

```bash
sudo systemctl start heartbeat
systemctl enable heartbeat
```

Para acceder a la configuración principal de Heartbeat accedemos al archivo ha.cf alojado en ‘/etc/ha.d/ha.cf’ y debemos añadir en ambos nodos lo siguiente:

```
#cat /
use_logd on  
keepalive 2
deadtime 30
warntime 10
initdead 120
udpport 694
ucast enp0s8 192.168.56.121
ucast enp0s8 192.168.56.122
# bcast eth0
auto_failback on
node nodo1
node nodo2
```

Cada directiva:
`use-log` espeficica si queremos un servicio demonio de registro de mensajes entre maquinas y solicitudes.
`keepalive` especifica el numero de segundos entre dos heartbeats.
`deadtime` especifica el numero de segundos despues de que el host se considera muerto si no responde.
`warntime` especifica el numero de segundos despues de que el ultimo Hearbeat avise de cualquier posible problema.
`initdead` el número de segundos de espera para otro host depsues de empezar Hearbeat, antes se considera muerto.
`udpport` es el numero de puesto usado por comunicaciones *ucast*. Por defecto es el puerto UDP 694.
`ucast` es la interfaz en la que se hará el *unicast*.

A continuación necesitamos indicar a Heartbeat cuales son los recursos que va a administrar.










### Referencias
https://www.howtoforge.com/tutorial/ubuntu-drbd-heartbeat-high-availability/
