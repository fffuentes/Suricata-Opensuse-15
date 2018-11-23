# Suricata-Opensuse-15

<p align="center">
  <img src="https://i.imgur.com/306CJ0d.jpg">
</p>

### El documento con la configuracion del archivo "suricata.yaml" esta en el repositorio con el nombre : Instalar y configurar Suricata IDS en Opensuse Leap 15.docx
### Puedes ver un video demostrativo de su funcionamiento aqui.
___

### OpenSuse Instalacion
Esta guia de instalacion a sido probada con:

    OpenSuse Leap 15
___
# Requerimientos Pre-Installation:
- ejecutar todos los comandos con privilegios de administador(root)

Antes de poder construir Suricata, ejecute el siguiente comando para asegurarse de que todas las dependencias estén instaladas:

`
zypper install -n wget tar gcc pkg-config pcre-devel libyaml-devel \
    libpcap-devel zlib-devel file-devel make libnetfilter_queue-devel \
    libjansson-devel mozilla-nss-devel libcap-ng-devel lua53-devel
`
___
# Suricata 4

- Descargamos suricata

ejecutar:      
`wget https://www.openinfosecfoundation.org/download/suricata-4.0.5.tar.gz`

- Descomprimimos

ejecutar:       
`tar -xvf suricata-4.0.5.tar.gz`

- Creamos el volumen

ejecutar:       
`cd suricata-4.0.5`
___
### Para Leap 15

ejecutamos :

`
CPPFLAGS="-I/usr/include/libnetfilter_queue/ -I/usr/include/libnfnetlink/" ./configure \
    --prefix=/usr --sysconfdir=/etc --localstatedir=/var --enable-nfqueue --enable-lua
 `
___
# Make

- Ahora compilarlo e instalarlo. 

Ejecutamos :

`make install`

`ldconfig`
___
# Configuración automática

- También puede utilizar las funciones de configuración automática disponibles de Suricata:

ex:

    make install-conf

make install-conf
hará el "make install" regular y luego creará / configurará automáticamente todos los directorios necesarios y suricata.yaml para usted.

    make install-rules

make install-rules
hará el "make install" regular y luego se descargará y configurará automáticamente el último conjunto de reglas de Emerging Threats disponible para Suricata

    make install-full

make install-full
combinará todo lo mencionado anteriormente (install-conf y install-rules) - y le presentará una lista para ejecutar (configurada y configurada) Suricata
