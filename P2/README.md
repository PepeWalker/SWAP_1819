#Práctica 2: Clonar la información de un sitio web

## Copia de archivos mediante ssh
Sabemos las direcciones IP de nuestras máquinas virtuales.
	- Máquina 1; 192.168.75.128
	- Máquina 2; 192.168.75.129


Con el siguiente comando copiamos un archivo por ssh, en este ejemplo un *tar.tgz*.
![imagen]( 01 )

y ahora comprobamos que se ha copiado correctamente en la máquina 2.
![imagen]( 02 )

Ahora instalaremos hacemos un clonado de directorio de la **MV 1** a la **MK 2**, en nuestro ejemplo es el directorio HOLA.
![imagen]( 03 )

Y comprobamos en la **MV 1** que se ha copiado correctamente.
![imagen]( 04 )

## Conexión ssh sin contraseña

Ahora vamos a generar generar la ssh-key en la **MV 1** y copiamos la id en la **MV 2**, de forma que podemos acceder directamente desde la **MV 2** sin requerimiento de contraseña.
![imagen]( 05 )

## Tarea cron de sincronización

Primero debemos crear una tarea cron de sincronización para que se vaya ejecutando cada minuto.
Editamos el con crontab -e.
![imagen]( 06-a )

Aqui vemos como editamos y añadimos la rutina para que se ejecute cada minuto 1. 
![imagen]( 06-b )






