++++++++++++++++++++++++++++++++
Hardware notes
++++++++++++++++++++++++++++++++

:Auteur: J.Soranzo
:Date: Novembre 2019
:Societe: VoLAB
:Entity: VoRoBoTics

.. toctree::
   :maxdepth: 2
   :caption: Sous-articles:

   merureDistance
   fpga/fpga
   raspberry/raspberry

.. contents:: Hardware tdm
    :backlinks: top

================================
Teensy (3.5)
================================
LED power : je pense qu'il n'y en a pas.
J'en ai pa vu sur le schéma et pas trouvé trace sur le forum.
Rien non plus dans les carac.

Température d'utilisation : à priori -40/+85°C seule inconnu : l'oscillateur.
ref : 6360 T8406 ? 16MHz 

================================
Connecteur Wifi
================================
IPEX ou IPX : petits connecteurs coaxiaux des cartes FriendlyArM nanoPC-T4 par exemple
MHF connecteur

SMA connecteur des antennes Wifi

----------------------------------------------------------------------------------------------------

.. index::
    single: ESP8266; pinout limite
    single: ESP8266; broches disponibles

================================
ESP8266
================================
Attention toutes les broches ne sont pas utilisables  pour faire ce qu'on veut!
Il y a des contrainte.

Voir sur le site `randomTutorial ESP8266 pinout`_

.. _`randomTutorial ESP8266 pinout` : https://randomnerdtutorials.com/esp8266-pinout-reference-gpios/

----------------------------------------------------------------------------------------------------

.. index::
    single: Hardware; Cable SATA to USB3
    
================================
SATA to USB3
================================    
Solution testée et maintes fois utilisées  `sur AMAZON SABERENT`_ à 9€90

.. _`sur AMAZON SABERENT` : https://www.amazon.fr/Sabrent-Adaptateur-Optimis%C3%A9-support-EC-SSHD/dp/B011M8YACM/ref=sr_1_8?keywords=Sabrent&qid=1581088661&sr=8-8

====================================================================================================
MIPI CSI prolangateur
====================================================================================================
`Pi Camera HDMI Cable Extension`_

.. _`Pi Camera HDMI Cable Extension` : https://www.tindie.com/products/freto/pi-camera-hdmi-cable-extension/

`Subtilitées sur Petit Studio`_

.. _`Subtilitées sur Petit Studio` : http://petitstudio.blogspot.com/2015/05/hdmi-cables-are-not-all-same.html

`Sur Amazon`_

.. _`Sur Amazon` : https://www.amazon.com/Arducam-Extension-Module-Raspberry-Specific/dp/B06XDNBM63

Et enfin `sur le site de BATC`_

.. _`sur le site de BATC` : https://wiki.batc.org.uk/CSI-2_to_HDMI


================================
Weblinks
================================


.. target-notes::