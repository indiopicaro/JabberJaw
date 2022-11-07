# JabberJaw
## Introducción
El JabberJaw es un intento de clon del shark jack. Conocido artefacto creado y comercializado por la empresa de [Hak5](https://hak5.org)

![sharkjack](https://user-images.githubusercontent.com/103136876/200296239-2f6ecb3a-6c20-4fe4-8333-6b481b04b7f8.jpg)



A5-V11 ---> https://openwrt.org/toh/unbranded/a5-v11



## Descarga de implementos

### Repositorio Github
El primer paso será hacerse del repositorio contenedor de la parte más importante de este proyecto.
#
    root@kali:~# git clone github.com/indiopicaro/JabberJaw/
    root@kali:~# cd JabberJaw

### Image Builder
ya como segundo paso se tendra que descargar el image builder que se puede encontrar en la página de [openwrt](https://downloads.openwrt.org/releases/).
En dónde se encontrará una variedad de versiones, entre estas deben de buscar entre cáda una y escoger la versión mas compatible o estable. solo tienen que entrar a las versiones. ir a a "targets" y entrar a "ramips". déntro de esta carpeta tiene que encontrarse la carpeta de "rt305x" y ahi mismo buscar el ".bin" de nuestro mini enrutador "A5-V11".
#
    root@kali:~# wget https://downloads.openwrt.org/releases/17.01.7/targets/ramips/rt305x/lede-imagebuilder-17.01.7-ramips-rt305x.Linux-x86_64.tar.xz
    root@kali:~# tar -xVf lede-imagebuilder-17.01.7-ramips-rt305x.Linux-x86_64.tar.xz
    root@kali:~# cd lede-imagebuilder-17.01.7-ramips-rt305x.Linux-x86_64
    
#
    root@kali:~#

### Crear imagen
#
    root@kali:~#
Dentro del repositorio descargado con la version de openwrt correspondiente, se ejecutará el siguiente comando:
#
    root@kali:~# make image PROFILE=a5-v11 PACKAGES="block-mount kmod-usb-storage kmod-usb-core kmod-usb2 kmod-fs-ext4 coreutils-sleep swconfig -ppp-mod-pppoe -ip6tables -luci -ppp -odhcpd-ipv6only -kmod-ip6tables -libuci -ppp" FILES=../default/4MB/

Si ocurre algun tipo de problema relacionado con la creacion de la imagen referente a que no se encuentra el modulo mencionado "a5-v11" solo queda cambiar de minisculas a mayúsculas la indicación. quedando como "PROFILE=A5-V11".
