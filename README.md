# JabberJaw
## Introducción
El JabberJaw es un intento de clon del shark jack. Conocido artefacto creado y comercializado por la empresa de [Hak5](https://hak5.org)

![s-l500](https://user-images.githubusercontent.com/103136876/200192669-73cf2821-b5cb-43b6-97fc-d6e4e6e7033a.jpg)

![HTB1lIWuHXXXXXXZXpXXq6xXFXXXD](https://user-images.githubusercontent.com/103136876/200201614-5086b1c1-cf90-41b4-a5b9-f1f2b603878f.jpg)


A5-V11 ---> https://openwrt.org/toh/unbranded/a5-v11



## Descargar implementos

### Repositorio Github
El primer paso será hacerse del repositorio contenedor de la parte mas importante de este proyecto.
#
    root@kali:~# git clone github.com/indiopicaro/JabberJaw/
    root@kali:~# cd JabberJaw

### Image Builder
ya como segundo paso se tendra que descargar el image builder que se puede encontrar en la pagina de [openwrt](https://downloads.openwrt.org/releases/).
En donde se encontrara una variedad de versiones, entre estas deben de buscar entre cada una y escoger la version mas compatible o estable. solo tiene que entrar a las versiones. ir a a "targets" y entrar a "ramips". dentro de esta carpeta tiene que encontrarse la carpeta de "rt305x" y ahi mismo buscar el ".bin" de nuestro mini enrutador "A5-V11".
#
    root@kali:~# wget https://downloads.openwrt.org/releases/17.01.7/targets/ramips/rt305x/lede-imagebuilder-17.01.7-ramips-rt305x.Linux-x86_64.tar.xz
    root@kali:~# tar -xVf lede-imagebuilder-17.01.7-ramips-rt305x.Linux-x86_64.tar.xz
    root@kali:~# cd lede-imagebuilder-17.01.7-ramips-rt305x.Linux-x86_64
    
#
    root@kali:~#

### Crear imagen
#
    root@kali:~#
Dentro del repositorio descargado con la version de openwrt correspondiente, se ejecutara el siguiente comando:
#
    root@kali:~# make image PROFILE=a5-v11 PACKAGES="block-mount kmod-usb-storage kmod-usb-core kmod-usb2 kmod-fs-ext4 coreutils-sleep swconfig -ppp-mod-pppoe -ip6tables -luci -ppp -odhcpd-ipv6only -kmod-ip6tables -libuci -ppp" FILES=../default/4MB/

Si ocurre algun tipo de problema relacionado con la creacion de la imagen referente a que no se encuentra el modulo mencionado "a5-v11" solo queda cambiar de minisculas a mayúsculas la indicación. quedando como "PROFILE=A5-V11".
