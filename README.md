# JabberJaw
Introducción

![s-l500](https://user-images.githubusercontent.com/103136876/200192669-73cf2821-b5cb-43b6-97fc-d6e4e6e7033a.jpg)

A5-V11 ---> https://openwrt.org/toh/unbranded/a5-v11

## Descargar implementos
#
    root@kali:


### Crear imagen
#
    root@kali:
Dentro del repositorio descargado con la version de openwrt correspondiente, se ejecutara el siguiente comando:
#
    make image PROFILE=a5-v11 PACKAGES="block-mount kmod-usb-storage kmod-usb-core kmod-usb2 kmod-fs-ext4 coreutils-sleep swconfig -ppp-mod-pppoe -ip6tables -luci -ppp -odhcpd-ipv6only -kmod-ip6tables -libuci -ppp" FILES=../default/4MB/

Si ocurre algun tipo de problema relacionado con la creacion de la imagen referente a que no se encuentra el modulo mencionado "a5-v11" solo queda cambiar de minisculas a mayúsculas la indicación. quedando como "PROFILE=A5-V11".
