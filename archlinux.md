##### Initial config
loadkeys es
loadkeys la-latin1

##### Init partition
 cfdisk

>/boot: La particion contiene el kernel del sistema operativo (el cual permite a su sistema arrancar)
junto con archivos utilizados durante el proceso de arranque. Para la mayoría de los usuarios, una partición boot de 100 – 150 Mb es suficiente.

>/(root): Aquí es donde “/” (el directorio raíz) se encuentra. En esta configuración, todos los archivos
(excepto aquellos almacenados en / boot) están en la partición raíz, con lo que es conveniente que la capacidad mínima no sea inferior a 10-15 Gb.

>/home: Donde se almacenarán nuestras configuraciones personales, las configuraciones de las aplicaciones (y tus perfiles en ellas), y tradicionalmente nuestros datos (documentos, fotos, vídeos, etc), por lo que se recomienda asignarle el mayor tamaño.

>Swap: Esta partición es necesaria para manejar la memoria “virtual” que no cabe en nuestra memoria RAM “física” y que no estamos utilizando en este momento.

> New » Primary | Logical » Size (en MB) » Beginning.

####### Two details:

> - En el caso de la partición elegida como Swap, ir a la opción “Type” y seleccionar 82 (Linux Swap) de la lista.
  - En el caso de la partición elegida como /boot, seleccionar la opción “Bootable“


sda1 = boot, sda2 = /, sda3 = home y sda4 = swap


###### En /boot se utilizará ext2:
mkfs -t ext2 /dev/sda1

###### En /, se utilizará ext4:
mkfs -t ext4 /dev/sda2

###### En /home, se utilizará ext4:
mkfs -t ext4 /dev/sda3

###### En swap, se utilizará mkswap:
mkswap /dev/sda4

###### Activamos la partición (swap):
swapon /dev/sda4

###### Organización de particiones
###### Montamos la partición / (root) en /mnt:
mount /dev/sda2 /mnt

###### Creamos los directorios de las otras particiones:
mkdir /mnt/boot
mkdir /mnt/home

###### Montamos las particiones correspondientes:
mount /dev/sda1 /mnt/boot
mount /dev/sda3 /mnt/home

###### DHCP is automatic

###### Para conectarnos a una red inalámbrica:
wifi-menu

###### Comprobar conexión:
ping -c 3 www.google.com

###### Instalamos los paquetes básicos:
pacstrap /mnt base base-devel

###### En este caso como gestor de arranque instalaremos GRUB:

pacstrap /mnt grub-bios
###### Para un mejor soporte en conexiones a Internet, instalamos NetworkManager:
pacstrap /mnt networkmanager

pacstrap /mnt xf86-input-synaptics

###### Configuración principal
###### Generar el archivo fstab:
genfstab -U -p /mnt >> /mnt/etc/fstab

###### Efectuar Chroot y configurar el sistema base:

arch-chroot /mnt

###### Establecer nombre de equipo, para esto tenemos que editar el archivo /etc/hostname:

nano /etc/hostname


ln -s /usr/share/zoneinfo/America/Mexico_City /etc/localtime

nano /etc/locale.conf

LANG=es_MX.UTF-8

nano /etc/locale.gen

locale-gen

###### Establecer la distribución de nuestro teclado:

###### Creamos el archivo /etc/vconsole.conf

nano /etc/vconsole.conf

###### Colocamos nuestra distribución de teclado.

KEYMAP=es
KEYMAP=la-latin1

###### Instalación de Grub:

grub-install /dev/sda

###### Creamos el archivo grub.cfg:

 grub-mkconfig -o /boot/grub/grub.cfg

###### ramdisk:

mkinitcpio -p linux

###### Establecer contraseña de root:

passwd


###### Cerrar chroot:

exit



###### Desmontar particiones:

umount /mnt/{boot,home,}

umout -a   

###### Reiniciar sistema:
reboot
