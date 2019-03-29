#Práctica 2: Clonar la información de un sitio web

## Copia de archivos mediante ssh
Sabemos las direcciones IP de nuestras máquinas virtuales.
	- Máquina 1; 192.168.75.128
	- Máquina 2; 192.168.75.129


Con el siguiente comando copiamos un archivo por ssh, en este ejemplo un *tar.tgz*.
![imagen]( https://github.com/PepeWalker/SWAP_1819/blob/master/P2/img/01%20.png )

y ahora comprobamos que se ha copiado correctamente en la máquina 2.
![imagen]( https://github.com/PepeWalker/SWAP_1819/blob/master/P2/img/02.png )

Ahora instalaremos hacemos un clonado de directorio de la **MV 1** a la **MK 2**, en nuestro ejemplo es el directorio HOLA.
![imagen]( https://github.com/PepeWalker/SWAP_1819/blob/master/P2/img/03%20clonado%20de%20directorio%20de%20mv1%20a%20mv2%20HOLA.png )

Y comprobamos en la **MV 1** que se ha copiado correctamente.
![imagen]( https://github.com/PepeWalker/SWAP_1819/blob/master/P2/img/04%20comprobado%20del%20clonado%20del%20directorio%20HOLA.png )

## Conexión ssh sin contraseña

Ahora vamos a generar generar la ssh-key en la **MV 1** y copiamos la id en la **MV 2**, de forma que podemos acceder directamente desde la **MV 2** sin requerimiento de contraseña.
![imagen]( https://github.com/PepeWalker/SWAP_1819/blob/master/P2/img/05%20generada%20la%20ssh-key%20en%20mv1%2C%20copiamos%20la%20id%20en%20mv2.png )

## Tarea cron de sincronización

Primero debemos crear una tarea cron de sincronización para que se vaya ejecutando cada minuto.
Editamos el con crontab -e.
![imagen]( https://github.com/PepeWalker/SWAP_1819/blob/master/P2/img/06-a%20%20%20Llamar%20crontab%20-e%20para%20editar%20archivo%20crontab.png )

Aqui vemos como editamos y añadimos la rutina para que se ejecute cada minuto 1. 
![imagen]( https://github.com/PepeWalker/SWAP_1819/blob/master/P2/img/06-b%20%20Edicion%20a%C3%B1adido%20y%20guardado%20del%20crontab.png )






