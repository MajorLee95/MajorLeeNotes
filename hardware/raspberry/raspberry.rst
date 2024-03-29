.. index::
    single: Raspberry

++++++++++++++++++++++++++++++++
Raspberry pi*
++++++++++++++++++++++++++++++++

:Auteur: J.Soranzo
:Date: Janvier 2020
:mise à jour: 13/10/2021
:Societe: VoRoBoTics
:Entity: VoLAB

.. contents::
    :backlinks: top

====================================================================================================
Différentes cartes
====================================================================================================
Très bon comparatif sur `socialcompare.com`_

.. _`socialcompare.com` : https://socialcompare.com/fr/comparison/raspberrypi-models-comparison

====================================================================================================
Processeurs
====================================================================================================
- RPi3 model B  BCM2837 à 1.2MHz cortex A53
- RPI3 model B+ BCM2837 à 1.4MHz
- Rpi4 : BCM2711 4 coeurs CORTEX A72 version 2Go, 4Go, 8Go

Tous les modèles ci-dessus ont le même facteur de forme. Seuls le RPi 1 A+ et le RPi3 A+ ont 
un facteur de forme différent

Description complète sur `Wikipédia Raspberry pi`_

.. _`Wikipédia Raspberry pi` : https://en.wikipedia.org/wiki/Raspberry_Pi

A titre de comparaison la carte Friendly arm NEO-PC T4 RK3399 2 A72 4 A53 : ARMV8-A (un peu plus 
de 110€ sur aliexpress au 7/4/2021)

====================================================================================================
Les caméras
====================================================================================================
Greens
====================================================================================================
- V1 : OmniVision OV5647 5 Mp
- v2 : Sony IMX219, 8 Megapixels
- HQ : Sony IMXZ477 12.3 Megapixels

Black
====================================================================================================
V2: Sans le filtre infrarouge !


====================================================================================================
I2C : état des lieux (13/10/2021)
====================================================================================================
`Wiring pi`_ Wiring pi is  deprecated… C'est directement dans les news du site de Gordon. 
Donc merci à lui pour ces 10 ans passées au service des autres.

.. _`Wiring pi` : http://wiringpi.com/

::

    gpio -v

i2c-tools::

    sudo apt-get install -y i2c-tools

- i2c-detect

::

    pip3 install smbus2

en C (safeAir)::

    pigpio.h

`pigpio`_

.. _`pigpio` : https://github.com/joan2937/pigpio

================================
Boîtiers
================================

.. image:: images/ArgonPiCase.jpg
   :width: 200 px
   :alt: Argon pi case
   :align: center

Boîtier vraiment spécial `Argon ONE Raspberry`_

Disponible `aussi sur Aliexpress`_


.. _`Argon ONE Raspberry` : https://www.amazon.com/gp/product/B07WP8WC3V/ref=as_li_qf_asin_il_tl?ie=UTF8&tag=andreassspies-20&creative=9325&linkCode=as2&creativeASIN=B07WP8WC3V&linkId=5f33cb45ff5d861b244b7646a9304c6e

.. _`aussi sur Aliexpress` : https://fr.aliexpress.com/item/4000379064637.html?spm=a2g0o.productlist.0.0.7c9b14aeJTUktf&algo_pvid=3db7baeb-ea60-4b8d-8aa5-877a2ea400e2&algo_expid=3db7baeb-ea60-4b8d-8aa5-877a2ea400e2-9&btsid=b5a432b2-6dcd-44d1-9553-6b95a39eda98&ws_ab_test=searchweb0_0,searchweb201602_3,searchweb201603_53

Autres boîtier avec écrou photo 
====================================================================================================

`LABISTS Raspberry Pi 4 Boitier`_

.. _`LABISTS Raspberry Pi 4 Boitier` : https://www.amazon.fr/LABISTS-Alimentation-Interrupteur-Ventilateur-Dissipateurs/dp/B082XYTTZX/ref=asc_df_B082XYTTZX/?tag=googshopfr-21&linkCode=df0&hvadid=411537567752&hvpos=&hvnetw=g&hvrand=769575774449413025&hvpone=&hvptwo=&hvqmt=&hvdev=c&hvdvcmdl=&hvlocint=&hvlocphy=9056230&hvtargid=pla-873617557431&psc=1&tag=&ref=&adgrpid=89565690397&hvpone=&hvptwo=&hvadid=411537567752&hvpos=&hvnetw=g&hvrand=769575774449413025&hvqmt=&hvdev=c&hvdvcmdl=&hvlocint=&hvlocphy=9056230&hvtargid=pla-873617557431

Avec alim 5V/3A, cable HDMI, hublo pour caméra, ventilateur et dissipateurs...

17€ sur AMZON

================================
Disque dur sympa
================================
`SSD de petite taille sur Aliexpress`_

.. _`SSD de petite taille sur Aliexpress` : https://fr.aliexpress.com/item/32848432283.html


====================================================================================================
Graver une images
====================================================================================================
Très simple avec la commande dd rien à installer::

    dd if=nomDeLImage of=/dev/sda(b ou c) status=progress bs=4M


.. index::
    single: Raspberry; SSD HDD boot

====================================================================================================
Comment booter sur SSD
====================================================================================================

`Vidéo du gaz avec l'accent Suisse`_

.. _`Vidéo du gaz avec l'accent Suisse` : https://www.youtube.com/watch?v=gp6XW-fGVjo

`Puis le site de James A. Chambers`_ Legandary Technology Blog moi j'ai eu des pb de certificats 
pour visiter ce site

.. _`Puis le site de James A. Chambers` : https://jamesachambers.com

----------------------------------------------------------------------------------------------------

.. index::
    pair: Raspberry; install ext hdd

================================
Boot from external HDD
================================

`Un tuto qui m'a l'air facile`_

.. _`Un tuto qui m'a l'air facile` : https://www.maketecheasier.com/boot-up-raspberry-pi-3-external-hard-disk/



.. index::
    pair: Raspberry; Shutwodn


====================================================================================================
Rappel éteindre
====================================================================================================
En sudo évidement:

- shutdown -h now (en sudo)
- poweroff

====================================================================================================
Essais écran 
====================================================================================================
KeDei v1.1

Utilisation des données du forum rpi [Review] KeDei 3.5" `HDMI display with touch for Raspberry Pi`_

.. _`HDMI display with touch for Raspberry Pi` : https://forums.raspberrypi.com/viewtopic.php?t=175616&sid=9d9f602c3792e2cb54f6e7485cc114d1

Une petite erreur s'est glissée ::

    hdmi_cvt 480 320 60 6 0 0 0
    
    au lieu de 

    hdmi_cvt=480 320 60 6 0 0 0


Testé sur RPI3 model B+ avec rapsbian Buster (finalement pas certain) sur un RPI 1 pas réussi à
faire fonctionner. Sur le 3 même sans paramètrer le hdmi dans le config.txt cela fonctionne.

Le RPI1 utilisé fonctionne très bien en hdmi sur un écran classique. Essayé 720x780 et 480x320 sans
succès 

Sur RPI1, l'écran s'obstine à afficher no signal quelque soit les config essayées.

`Autre procédure non testée sur Projetsdiy.fr`_

.. _`Autre procédure non testée sur Projetsdiy.fr` : https://projetsdiy.fr/test-ecran-lcd-35-480x320-pixels-hdmi-tactile-via-gpio-boitier-acrylique-raspberry-pi-3-raspbian/

`site officiel KeDei`_

.. _`site officiel KeDei` : http://en.kedei.net/


=========
Weblinks
=========

.. target-notes::
