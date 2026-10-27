# Inicialización a la virtualización
# Aarón Fuentes Casanova

## Instalación de Ubuntu en VirtualBox

Para instalar Ubuntu en VirtualBox, primero deberás dirigir a la página oficial de Ubuntu y descargarte una ISO de Ubuntu desktop en este [enlace](https://ubuntu.com/download)

Una vez que tienes descargada la ISO, tendrás que crear una máquina virtual con esa misma imagen. En este caso, las especificaciones de la máquina virtual que utilizo son las siguientes:

- 4GB de RAM
- Disco duro de 100GB (mínimo de 50GB)
- Tipo de red NAT

Una vez que hemos creado la máquina, vamos a ejecutar la máquina y proceder a instalar ubuntu.
En esta instalación no va a hacer falta realizar ninguna opción extraordinaria, básicamente con que le des a siguiente en la mayoria de pantallas va a ser suficientes, sin embargo hay algunas pantallas que te van a preguntar por ejemplo si quieres usar un proxy. Este tipo de opciones en las que no tengas muy claro, es mejor saltarlo debido a que es una configuración avanzada. En caso de que no sepas mucho acerca de instalaciones de sistemas operativos, también tienes una opción para que por ejemplo, el disco duro lo utilice completamente para ubuntu sin tener que configurar particiones ni nada por el estilo. Una vez que hayas terminado, procederá a instalarse ubuntu.

Una vez que ya tenemos descargado Ubuntu, podremos ver finalmente el escritorio de nuestra máquina:
![Imagen1](captura1.png)

## Pasos para instalar Docker Desktop
En este apartado vamos a ver los pasos a seguir para poder instalar Docker Desktop en nuestra máquina virtual.

El primer paso que vamos a realizar va a ser descargarnos el instalador de nuestro sistema operativo (en este caso ubuntu) con el siguiente comando:

_wget https://desktop.docker.com/linux/main/amd64/docker-desktop-amd64.deb_

Una vez que tenemos descargado el instalador, vamos a situarnos en la carpeta en la que se haya descargado y ejecutar el siguiente comando:

_sudo apt install ./docker-desktop-amd64.deb_

Y con eso, ya tendríamos instalado docker:

![Imagen2](captura2.png)

## Crear y ejecutar los contenedores

