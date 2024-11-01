++++++++++++++++++++++++++++++++
Hardware notes
++++++++++++++++++++++++++++++++

:Auteur: J.Soranzo
:Date: Novembre 2019
:Societe: VoRoBoTics
:Entity: VoLAB

.. toctree::
   :maxdepth: 2
   :caption: Sous-articles:

   robotique/robotique
   fpga/fpga
   raspberry/raspberry
   nucleo/nucleo

.. contents:: Hardware tdm
    :backlinks: top

.. index::
    single: PCB

====================================================================================================
PCB data
====================================================================================================
A compléter 22/7/2021

.. image:: images/grilleVsMills.jpg 
   :width: 300 px


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

====================================================================================================
Teensy (3.5)
====================================================================================================
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


====================================================================================================
Connecteur Wifi
====================================================================================================
IPEX ou IPX : petits connecteurs coaxiaux des cartes FriendlyArM nanoPC-T4 par exemple
MHF connecteur

SMA connecteur des antennes Wifi

----------------------------------------------------------------------------------------------------

.. index::
    single: ESP8266; pinout limite
    single: ESP8266; broches disponibles
    single: ESP32

====================================================================================================
ESP boards
====================================================================================================
ESP8266
----------------------------------------------------------------------------------------------------


Attention toutes les broches ne sont pas utilisables  pour faire ce qu'on veut!
Il y a des contrainte.

Monoceur 32 bits 

Voir sur le site `randomTutorial ESP8266 pinout`_

.. _`randomTutorial ESP8266 pinout` : https://randomnerdtutorials.com/esp8266-pinout-reference-gpios/

ESP32
----------------------------------------------------------------------------------------------------
`DFRobot sort sa firebeetle`_ à 6.9$

.. _`DFRobot sort sa firebeetle` : https://www.dfrobot.com/product-1590.html

Existe en WeMOS qu'on trouve facilement sur Ebay, Aliexpress et Amazon pour environ 5€ livré.
Mais dans cette version la carte n'est pas vraiment breadboard frendly les 2 rangées côte à côte
c'est pas géant.

En dual in line on en trouve facilement même sur Amazon prime à 10€ lol ou `4.2€ livré sur Aliexpress`_

.. _`4.2€ livré sur Aliexpress` : https://fr.aliexpress.com/item/32959541446.html?albpd=fr32959541446&acnt=248-630-5778&aff_platform=aaf&albpg=539263010115&netw=u&albcp=10191220526&pvid=6da13e78-e411-4a07-8ba1-6ba1d5f3ebaf&sk=UneMJZVf&scm=1007.23534.123999.0&trgt=539263010115&terminal_id=dc405bfbfa4646238f25fa75bee476aa&needSmbHouyi=false&albbt=Google_7_shopping&src=google&crea=fr32959541446&aff_fcid=6b4f0e3a21d547fcb80dae3f14e7bcb4-1619075408988-07981-UneMJZVf&gclid=Cj0KCQjwvYSEBhDjARIsAJMn0lgXhfg6yLDy4jCB3HKIzpxUOGMqDdKdXSceSx8nPQWkjJ7Og46MOFsaAkKnEALw_wcB&albag=107473525328&aff_fsk=UneMJZVf&albch=shopping&albagn=888888&isSmbAutoCall=false&aff_trace_key=6b4f0e3a21d547fcb80dae3f14e7bcb4-1619075408988-07981-UneMJZVf&rmsg=do_not_replacement&device=c&gclsrc=aw.ds


ESP32 vs ESP8266
----------------------------------------------------------------------------------------------------
Sur `Arduinotutoriels`_

.. _`Arduinotutoriels` : https://arduinotutoriels.com/esp32-vs-esp8266/

En résumé, ESP32 ajoute **Dual core**, Bluetooth 4.0 LE, 2 SPI et 1 I2C, 2 canaux ADC 8 bits et 19 GPIO

.. NOTE::

    Rappel : on peut faire tourner freeRTos sur un ESP.

----------------------------------------------------------------------------------------------------

.. index::
    single: Hardware; Cable SATA to USB3

====================================================================================================
SATA to USB3
====================================================================================================

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
----------------------------------------------------------------------------------------------------
`Analog TDS Sensor/Meter for Arduino`_ 26/02/2020

.. _`Analog TDS Sensor/Meter for Arduino` : https://www.dfrobot.com/product-1662.html

TDS (Total Dissolved Solids) indicates that how many milligrams of soluble solids dissolved in 
one liter of water.

`Example d'utilisation sur Hackster.io`_

.. _`Example d'utilisation sur Hackster.io` : https://www.hackster.io/robotics-bangladesh/portable-liquids-classification-device-d207a3?utm_campaign=new_projects&utm_content=3&utm_medium=email&utm_source=hackster&utm_term=project_name 

----------------------------------------------------------------------------------------------------

Air
----------------------------------------------------------------------------------------------------
A retranscrire ici projet 035-tempDataLogger document de conception 26/02/2020 ...


----------------------------------------------------------------------------------------------------

.. index::
    single: SBC

====================================================================================================
SBC
====================================================================================================
Single boards computer

Il y a les petites

- `Orange pi`_  (au 10/04/2021 : 27 modèles)
- `Friendly arm`_ (au 17/04/2021 : 23 cartes sur le site officiel)
- Raspberry pi

.. _`Orange pi` : http://www.orangepi.org/

.. _`Friendly arm` : https://www.friendlyarm.com/

Et il y a les grosses qui ressembles plus à des carte mère de PC, SBC Hautes performances.

Elles coûtent souvent plusieurs centaines d'Euro...

.. image:: images/thin-mini-itx.jpg
    :align: center
    :width: 500 px

Comme la NVIDIA Jetson Xavier ou encore :

.. figure:: images/QBiP-1605A.png
    :align: center
    :width: 500 px

    QBiP-1605A de GigaIPC

Les fabricants (de petites)
----------------------------------------------------------------------------------------------------
- Raspberry fondation
- Orange pi
- Banana pi
- NVida Jetson nano (65€, 77€ AMZPrime)
- RADXA
- DFROBOT/LATTEPANDA
- CUBIE
- Onion
- ASUS Tinker Board S
- Clockwork
- ROCK64
- ODROID
- LIBRE COMPUTER
- PIN64

Sous groupe PIN64
----------------------------------------------------------------------------------------------------
Ox64 : 8$
****************************************************************************************************


Détectée en 2023, SBC très petite.

`0x64 wiki`_

.. _`0x64 wiki` : https://wiki.pine64.org/wiki/Ox64

.. image:: images/400px-Ox64_board.jpg 
   :width: 300 px

ROCKPro64
****************************************************************************************************

`ROCKPro64 4GB Single Board Computer`_ 80$ en 4G et 60 en 2

.. _`ROCKPro64 4GB Single Board Computer` : https://pine64.com/product/rockpro64-4gb-single-board-computer/


SoC : RK3399

`ROCKPro64 wiki`_ je suis pas fan

.. _`ROCKPro64 wiki` : https://wiki.pine64.org/wiki/ROCKPro64



Raspberry pi Zero et concurrentes
----------------------------------------------------------------------------------------------------

On a (au 20/09/2021):

- Banana Pi BPI-M2-ZRO : 26.29€ sur AMAZON : 4x Cortex-A7 512Mo WF/BT4 miniHDMI, CSI, pas eMMC, USB2
- RADXA ZERO : de 15 à 90$ : 4x Cortex A53, 512M à 4G, de 0 à 128G eMMC, WF/BT5, pas de vid, USB3 (2Go, 8emmc 30$)

Question : y existe-il un carte avec du WF, du CSI, de l'emmc à moins de 30€

Autre question quelle celle qui a le meilleur rapport prix performances dans la gamme des 30€


Sous groupe Friendlyarm
----------------------------------------------------------------------------------------------------
A noter qu'il ont leur propre boutique vs Orangepi sur aliexpress.

Je les trouve mieu documenté à l'iimage de ce site `nanopi.io`_

.. _`nanopi.io` : http://nanopi.io/index.html

::

    NanoPi
        M1 Plus: Allwinner H3, 1G DDR3,       8Gemmc,     WifiBT,             2USB2,              HDMI, GEth, mSD, 60x64, 38$
        M4 :     RK3399,       2G DDR3, PCIe, eMMCsocket, WIFI 2et 5G, BT4.1, 3USB3.0, MIPI, CSI, HDMI, GEth, mSD, 56x85, 50$
            B: 70$, 2USB2, 2USB3, 1 seul prise antmSD, 
            V2 : RK3399,       4G DDR4, PCIe, eMMCsocket, WIFI 2et 5G, BT4.1, 3USB3.0, MIPI, CSI, HDMI, GEth, mSD, 56x85, 80$
        Neo
            LTS: Allwinner H3, 256/512 DDR3,                                , 1 usb2.0+2,          10/100Eth, mSD, 40x40, 16$, 24pinGPIO
            Air-LTS: H3,       512M DDR3,   **eMMC8G**,   wifiBT,                      DVP cam,               mSD, 40x40, 19.99$,24pinGPIO
            Core-LTS: GPIO 2x 24 +10 (tout est dans des GPIO) Allwinner H3, 256/512DDR3, emmc 4/8G,           mSD, 40x40, 20$
            NEO4:      RK3399, 1G DDR3, emmc socket, 1USB2+1USB3.0, miniCSI, WIFI4G, BT4.0,             GEth, mSD, 45x60, 50$
            NEO3-LTS:  RK3328,1G/2G DDR4,            1USB3.0, 1USB2.0 header,                           GEth, mSD, 48x48, 39$, 26pin GPIO
        DUO2:    Allwinner H3, 512M DDR3,                 WIFI 2G, BT4.0, USB2et 3 host exposed, CSI,       **25.4x55** , 19.99$
            Carrier board
        R- à on avis pour Router
            R1:  Allwinner H3, 512/1G DDR3,   8GeMMc, WIFI, BT4.0, prise SMA, Eth 10/100, GEth, pas de vid, 2USB2.0, mSD,50.5x60, 32$   
            R1S: pas compris boitier jaune ??? 27$
            R2S: RK3328, 1G DDR4,                                         USB2.0, pas de vid,Eth 10/100, GEth, mSD, 66x66, 48$
            R4S: RK3399, 1/4G DDR4,                                    2USB3.0, pas de vid, Native GEth+ GEth, mSD, 66x66, 55$, pas de GPIO
        Fire
            2A-LTS S5P4418 (4xA9), 512M DDR3,                      1 usb2.0, RGB LCD port, Cam, mcriHDMI, GEth, mSD, 75x40, 24.99$, 40pin GPIO (cRPi)
            3-LTS: S5P6818 (8xA53), 1GDDR3,                        1 usb2.0, RGB LCD port, Cam, microHDMI, GEth, mSD, 75x40, 45$, 40pin GPIO (cRPi)

    nanoPC
        T2: S5P4418, 1G DDR3, 8Gemmc, Wifi /n, BT4.0,  4xUSB2.0, DVP/CSI cam, microHDMI, GEth, 60x100, 30pin GPIO ,65$  
        T3 Plus:  S5P6818, 2GDDR3, 16Gemmc, Wifi /n, BT4.0, 4USB2.0, HDMI, DVP, 2CSI, GEth, mSD, 64x100, 30pin GPIO, 85$
        T4: RK3399, 4G DDR3, emmc, USB3.0, USBC/DP, HDMI2.0, M2.M (NVME), CS1, CS2, eDP, DSI1, GEth, mSD, 64x100, 139$
    
    Core
        4418: S5P4418, 1GDDR3, 8Gemmc, Wifi /n, BT4.0, RGB LCD port, LVDS, GEth, mSD, 45x78, 49$ 50pin GPIO
        6818: S5P6818, 1GDDR3, 8Gemmc, Wifi /n, BT4.0, RGB LCD port, LVDS, GEth, mSD, 45x78, 45$ 50pin GPIO
    Zero Pi : Allwinner H3, 512MB DDR3, USB2.0GEth,  17$

Prix indicatif au 17/04/2021


Chez Orange pi
----------------------------------------------------------------------------------------------------
::

    2G Iot: A5, 256 DDR2, SIM 2G, 512M Flash, Wifi BT, 1USB2.0, LCD, CSI, mSD, 42x67, 11.82$, 40pin GPIO
    3G-IOT-A: MT6572, 256 DDR2, SIM 3G, 512M emmc Flash, Wifi BT, 1USB2.0, LCD, CSI, mSD, 52x68, 20$, 40pin GPIO
    3G-IOT-B: MT6572, 512 DDR2, SIM 3G, 4G emmc Flash, 1USB2.0, LCD, CSI, mSD, 52x68, 23$, 40pin GPIO
    4G-IOT : MT6737 (4xA53), 1G DDR3, SIM 4G, 8Gemmc,  Wifi BT, 55x85,  40pin GPIO, pas dispo 20/9/21
    Lite
    Lite 2
    One
    One Plus
    OPI Win plus
    PC
    PC Plus
    PC2
    Pi I96
    Pi Prime
    PI3
    PI4
    PI4B
    PI5 RK3588S
    Plus 2E
    R1
    R1 Plus
    RK3399 EOL

    
    Zero LTS
    Zero Plus2
    Zero2 : H616 (4x A53) MaliG31, 512M DDR3, Wifi BT5.0, microHDMI 3USB2.0 : 28€ pas de vid, pas emmc

En général, difficile d'appro.

Chez Bananapi
----------------------------------------------------------------------------------------------------
::

    F2P
    F2S
    W2
    R2
    M2 pro 65€
    M2 Berry Allwiner V40 2x A7, XIFI, BT, SATA, CSI, MIPI, 1G DDR3 4xUSB2.0, FF RPi, 44.59€ AliE
    M2 Ultra Allwiner V40, XIFI, BT, SATA, CSI, MIPI, 2G DDR3 2xUSB2.0, 8G eMMC, FF RPi, 76€ AliE
    M3
    M4 
    M5 S905X3 4x CortexA55, Mali-G31, pas de CSI, 1 HDMI pas de wifi ni BT, 4G DDR4, 16G eMMC, 4x USB 75€ AliE
    ZERO

sous group LATTEPANDA
----------------------------------------------------------------------------------------------------
- LTP 2G/32G : 99$, 4xIntel W10, 2GDDR3 emmc32g, WF/BT4 pas de videoin usb3

====================================================================================================
Analog power switching
====================================================================================================

.. index::
    pair: Switching;  MOSFET

Low power MOSFET ON/OFF
----------------------------------------------------------------------------------------------------
On parle de high side switch

Sur `electronics.stackexchange.com`_

.. _`electronics.stackexchange.com` : https://electronics.stackexchange.com/questions/78223/3-3v-high-side-switch?rq=1

.. figure:: images/highSideRefDesign.png
    :width: 300 px
    :figwidth: 100%
    :align: left

    Ref design

.. image:: images/DMC2038LVT.jpg 
   :width: 200 px

.. image:: images/DMC2038LVT_2.jpg 
   :width: 200 px

:download:`NTD20N03<NTD20N03datasheet.pdf>` ne convient pas car canal N
   
Mon essai avec :download:`2N7000<2N7000.pdf>` et  
commandé par un `Digispark`_

.. _`Digispark` : http://digistump.com/products/1





================================
Weblinks
================================


.. target-notes::
