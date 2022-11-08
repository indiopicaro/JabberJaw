# JabberJaw
## Introducción
El JabberJaw es un intento de clon del shark jack.Siendo este un conocido artefacto creado y comercializado por la empresa de [Hak5](https://hak5.org). Utilizado y pensado como un artefacto de pentesting de bolsillo que cabe en la palma de la mano. este siendo un punto importante para buscar el clon perfecto para realizar. existiendo una variedad de mini enrutadores de [openwrt](https://downloads.openwrt.org) que tienen los componentes necesarios y el tamaño compacto para ser implementados con el firmware de JabberJaw.

![sharkjack](https://user-images.githubusercontent.com/103136876/200296239-2f6ecb3a-6c20-4fe4-8333-6b481b04b7f8.jpg)

Entre todas las variedadas existentes de mini enrutadores compatibles con un firmware de JabberJaw. he escogido el A5-V11 por su tamaño y facil acceso a ser comprado, encontrandolo en [aliexpress](https://www.aliexpress.com/item/1005002095929256.html?spm=a2g0o.productlist.main.1.4b55f9c3ddVHvO&algo_pvid=e26461db-4af8-4fd7-a559-b984a821a1a3&algo_exp_id=e26461db-4af8-4fd7-a559-b984a821a1a3-0&pdp_ext_f=%7B%22sku_id%22%3A%2212000018726732998%22%7D&pdp_npi=2%40dis%21CLP%2113283.0%2110630.0%21%21%21%21%21%402122457116679311467201959d0732%2112000018726732998%21sea&curPageLogUid=oiqeHh0MjU80) por un valor de mas o menos 10 dolares.

A un asi aparte de este mini enrutador existen varios otros de los cuales se puede trabajar pero este ha sido el de mas facil acceso que he conseguido. En el siguiente link he dejado la pagina de openwrt referente al mini enrutador de a5-v11. Donde se pueden visualizar las especifaciónes tecnicas de este mismo teniendo una cantidad de 4MB memoria ram, lo cual no nos favorece en lo absoluto.

A5-V11 ---> https://openwrt.org/toh/unbranded/a5-v11

### Opción de aumento de memoria RAM
existe la posibilidad de utilizar una memoria USB externa. O ya entrando a mas detalle, esta la opción de comprar un chip que contenga mas memoria ram, para desoldar el que contiene el mini enrutador y aumentarlo a 16MB. Es una opción la cual aun no he aplicado pero dejo el link adjuntado de un video en el que ya ha sido aplicado. para esto es necesario tener en cuenta que antes de soldar el nuevo chip hay que cargarle los datos del anterior.

https://www.youtube.com/watch?v=N96OUzJMcpM

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
