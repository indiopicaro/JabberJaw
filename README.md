# JabberJaw
## Introducción
El JabberJaw es un proyecto que busca replicar las funcionalidades del Shark Jack, un conocido dispositivo diseñado y comercializado por [Hak5](https://hak5.org). Este gadget es ampliamente utilizado en pruebas de penetración, destacándose por su diseño compacto que lo hace ideal para llevar en la palma de la mano.

La inspiración detrás del JabberJaw radica en crear un dispositivo de pentesting eficiente y portátil, aprovechando la variedad de mini enrutadores compatibles con [openwrt](https://downloads.openwrt.org). Estos mini enrutadores cuentan con los componentes necesarios y un tamaño compacto, lo que los convierte en la base perfecta para implementar el firmware personalizado de JabberJaw.

![sharkjack](https://user-images.githubusercontent.com/103136876/200296239-2f6ecb3a-6c20-4fe4-8333-6b481b04b7f8.jpg)

Entre las diversas opciones de mini enrutadores compatibles con el firmware de JabberJaw, he optado por el modelo A5-V11 debido a su tamaño compacto y la facilidad para adquirirlo. Este modelo está disponible en plataformas como [Aliexpress](https://www.aliexpress.com/item/1005002095929256.html?spm=a2g0o.productlist.main.1.4b55f9c3ddVHvO&algo_pvid=e26461db-4af8-4fd7-a559-b984a821a1a3&algo_exp_id=e26461db-4af8-4fd7-a559-b984a821a1a3-0&pdp_ext_f=%7B%22sku_id%22%3A%2212000018726732998%22%7D&pdp_npi=2%40dis%21CLP%2113283.0%2110630.0%21%21%21%21%21%402122457116679311467201959d0732%2112000018726732998%21sea&curPageLogUid=oiqeHh0MjU80), lo que lo convierte en una opción accesible y práctica para este proyecto.

En el siguiente enlace, puedes encontrar la página de OpenWrt dedicada al mini enrutador A5-V11, donde se detallan sus especificaciones técnicas. Este dispositivo cuenta con solo 4 MB de memoria flash, una característica que no resulta favorable para nuestro propósito, ya que limita significativamente las capacidades del firmware de JabberJaw.

A5-V11 ---> https://openwrt.org/toh/unbranded/a5-v11

### Aumento de Memoria
Para superar la limitación de memoria del A5-V11, existen dos opciones viables:

Utilizar una memoria USB externa: Esta solución es más sencilla y permite ampliar las capacidades del dispositivo sin modificar su hardware interno.

Reemplazar el chip de memoria flash: Esta opción implica desoldar el chip original de 4 MB y reemplazarlo por uno de mayor capacidad, como un chip de 16 MB. Antes de realizar esta modificación, es fundamental clonar los datos del chip original al nuevo. Este proceso requiere herramientas específicas y habilidades avanzadas en soldadura y manejo de hardware.

He adjuntado un enlace a un video donde se muestra cómo llevar a cabo esta modificación. Aunque aún no he aplicado esta solución, considero que es una alternativa interesante para quienes buscan maximizar el potencial del mini enrutador.

https://www.youtube.com/watch?v=N96OUzJMcpM

## Descarga de implementos

### Repositorio Github
El primer paso consiste en obtener el repositorio que contiene los elementos clave para el desarrollo de este proyecto.
#
    root@linux:~# git clone github.com/indiopicaro/JabberJaw/
    root@linux:~# cd JabberJaw

### Image Builder
El segundo paso consiste en descargar el Image Builder, disponible en la página oficial de [openwrt](https://downloads.openwrt.org/releases/). En este sitio encontrarás diversas versiones, por lo que será necesario identificar la más compatible o estable para tu proyecto.

https://downloads.openwrt.org/releases/

Para ello, sigue estos pasos:

1. Accede a las versiones disponibles y dirígete a la carpeta "targets".
2. Dentro de "targets", selecciona la carpeta "ramips".
3. En "ramips", busca la subcarpeta "rt305x".
4. Localiza el archivo ".bin" correspondiente a tu mini enrutador, en este caso el A5-V11.

Este archivo será esencial para cargar el firmware adecuado al dispositivo.
#
    root@linux:~# wget https://downloads.openwrt.org/releases/17.01.7/targets/ramips/rt305x/lede-imagebuilder-17.01.7-ramips-rt305x.Linux-x86_64.tar.xz
    root@linux:~# tar -xVf lede-imagebuilder-17.01.7-ramips-rt305x.Linux-x86_64.tar.xz
    root@linux:~# cd lede-imagebuilder-17.01.7-ramips-rt305x.Linux-x86_64
    
#
    root@linux:~#

### Crear imagen
#
    root@kali:~#
Dentro del repositorio descargado con la version de openwrt correspondiente, se ejecutará el siguiente comando:
#
    root@kali:~# make image PROFILE=a5-v11 PACKAGES="block-mount kmod-usb-storage kmod-usb-core kmod-usb2 kmod-fs-ext4 coreutils-sleep swconfig -ppp-mod-pppoe -ip6tables -luci -ppp -odhcpd-ipv6only -kmod-ip6tables -libuci -ppp" FILES=../default/4MB/

Si ocurre algun tipo de problema relacionado con la creacion de la imagen referente a que no se encuentra el modulo mencionado "a5-v11" solo queda cambiar de minisculas a mayúsculas la indicación. quedando como "PROFILE=A5-V11".
