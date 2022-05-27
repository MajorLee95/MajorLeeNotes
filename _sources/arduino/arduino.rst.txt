.. index::
    single: Arduino

++++++++++++++++++++++++++++++++
Arduino
++++++++++++++++++++++++++++++++

:Auteur: J.Soranzo
:Date: Janvier 2020
:MAJ: 21/05/2022
:Societe: VoRoBoTics
:Entity: VoLAB

.. contents::
    :backlinks: top

====================================================================================================
Library studies
====================================================================================================

remeber Xmind ! ???? (03/2022)

To be completed (01/2020)



====================================================================================================
Filter ? library (21/05/2022)
====================================================================================================

See IOT Esp project

====================================================================================================
Arduino sous Eclipse
====================================================================================================

Très bonne `vidéo Youtube de  Doug Schaefer`_

.. _`vidéo Youtube de  Doug Schaefer` : https://www.youtube.com/watch?v=TtPvkPpAx0E

====================================================================================================
Arduino hex dump
====================================================================================================
Pour ARDUINO DUE::

    C:\Users\jojo\AppData\Local\Arduino15\packages\arduino\tools\bossac\1.6.1-arduino/bossac.exe -i -d --port=COM10 -U false -e -w -v -b C:\Users\jojo\AppData\Local\Temp\arduino_build_369722/Blink.ino.bin -R

La commande ci-dessus n'est pas foncièrement utile vue qu'elle utilise le port de prog (si ce-dernier
est KC alors pas de communication possible)

Je n'ai pas encore fait la manip via le bus SPI avec un USBASP ou une sonde ATMEL.


Pour un UNO avec un USBASP::

    avrdude -p m328p -c usbasp -U flash:r:toto.hex:i

    avrdude: warning: cannot set sck period. please check for usbasp firmware update
    .
    avrdude: AVR device initialized and ready to accept instructions

    Reading | ################################################## | 100% 0.02s

    avrdude: Device signature = 0x1e950f
    avrdude: reading flash memory:

    Reading | ################################################## | 100% 13.04s

=========
Weblinks
=========

.. target-notes::
