++++++++++++++++++++++++++++++++
Hardware notes
++++++++++++++++++++++++++++++++

:Auteur: J.Soranzo
:Date: Novembre 2019
:Societe: VoRoBoTics
:Entity: VoLAB

.. toctree::
   :maxdepth: 3
   :caption: Sous-articles:

   robotique/robotique
   fpga/fpga
   raspberry/raspberry
   nucleo/nucleo

.. contents:: Hardware tdm
    :backlinks: top

----------------------------------------------------------------------------------------------------    
    
.. index::
    pair: CPU Architecture; Harvard
    pair: CPU Architecture; Von Neumann
    
====================================================================================================
CPU Architecture
====================================================================================================
Harvard et Von Neumann

Harvard :  computer architecture with separate storage and signal pathways for instructions and data

En général, aujourd'hui on est plus souvent confronté à Modified Harvard architecture dans le sens
où les données et les instructions partage souvent les mêmes memoires mais sont traités dans des 
caches différents.

Von Neumann architecture, where program instructions and data share the same memory and pathways.

Source `wikipedia Harvard Archi`_

.. _`wikipedia Harvard Archi` :  https://en.wikipedia.org/wiki/Harvard_architecture

================================
Teensy (3.5)
================================
`Site officiel Teensy`_

LED power : je pense qu'il n'y en a pas.
J'en ai pa vu sur le schéma et pas trouvé trace sur le forum.
Rien non plus dans les carac.

Température d'utilisation : à priori -40/+85°C seule inconnu : l'oscillateur.
ref : 6360 T8406 ? 16MHz

Processeur : MK64FX512VMD12 120 MHz Cortex-M4F

3.3V signals, 5V tolerant

512K FLASH, 256K RAM, 4K EEPROM, 17 timer

.. _`Site officiel Teensy` : https://www.pjrc.com/teensy/


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


====================================================================================================
LES CAPTEURS
====================================================================================================
Eau 
====================================================================================================
`Analog TDS Sensor/Meter for Arduino`_ 26/02/2020

.. _`Analog TDS Sensor/Meter for Arduino` : https://www.dfrobot.com/product-1662.html

TDS (Total Dissolved Solids) indicates that how many milligrams of soluble solids dissolved in 
one liter of water.

`Example d'utilisation sur Hackster.io`_

.. _`Example d'utilisation sur Hackster.io` : https://www.hackster.io/robotics-bangladesh/portable-liquids-classification-device-d207a3?utm_campaign=new_projects&utm_content=3&utm_medium=email&utm_source=hackster&utm_term=project_name 

----------------------------------------------------------------------------------------------------

Air
====================================================================================================
A retranscrire ici projet 035-tempDataLogger document de conception 26/02/2020 ...

================================
Weblinks
================================


.. target-notes::
