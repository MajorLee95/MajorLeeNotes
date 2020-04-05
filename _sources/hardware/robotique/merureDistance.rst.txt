++++++++++++++++++++++++++++++++
Robotique : mesure de distance
++++++++++++++++++++++++++++++++
:Auteur: J.Soranzo
:Date: Novembre 2019
:Societe: VoRoBoTics
:Entity: VoLAB

.. contents:: Table des matières Mesure de distance
    :backlinks: top

================================
Vocablaire
================================
TOF = Time Of Flight

SLAM = Simultaneous Localization and Mapping

================================
Lidar 
================================

LIDAR tournant 
======================================

Chez DF-Robot : 99$ (prix au 2/3/20) `A1-M8 DF ROBOT`_

.. _`A1-M8 DF ROBOT` : https://www.dfrobot.com/product-1125.html

`YDLIDAR`_ à moins de 100€ sur ALiexpress

.. _`YDLIDAR` : https://fr.aliexpress.com/item/4000393240317.html?src=google&src=google&albch=shopping&acnt=494-037-6276&isdl=y&slnk=&plac=&mtctp=&albbt=Google_7_shopping&aff_platform=google&aff_short_key=UneMJZVf&&albagn=888888&albcp=6459793138&albag=77316928277&trgt=743612850714&crea=fr4000393240317&netw=u&device=c&gclid=Cj0KCQiApt_xBRDxARIsAAMUMu8TlG0-RCEyXrrduUi5lkIxgdoq5SNSeYpcCNwFAwR4xSERS6RbwkgaAlOsEALw_wcB&gclsrc=aw.ds


LIDAR tournant Home made
======================================

`Homemade LIDAR sensor with Arduino`_ & Processing sur Youtube

`Le site qui va avec la vidéo`_

Lidar HOMEMADE Tournant à partir d'un VL53LX0, ARDUINO UNO, connecteur tournant et capteur 
à effet HALL

Une autre vidéo sur un lidar tournant home made

`Open Simple Lidar`_ : Making map of the rooms

`Hakaday.io`_ et `github`_ dans les commentaires de la vidéo

Application PC développée en C# dans le code est foruni sous github ! Merci à lui.

Utilise un capteur TSL1401 assez original ! Full instruction provided !!!!


.. _`LIDAR lite v3HP` : https://www.sparkfun.com/products/14599

.. _`Go-Tronic` :  https://www.gotronic.fr/art-capteur-de-distance-lidar-lite-v3-25437.htm#complte_desc

.. _`Homemade LIDAR sensor with Arduino` : https://www.youtube.com/watch?v=fQ2iB7qkrUg&t=59s

.. _`Le site qui va avec la vidéo` : https://electronoobs.io/tutorial/48#

.. _`Open Simple Lidar` : https://www.youtube.com/watch?v=RW57MEIpBHI

.. _`Hakaday.io` : https://hackaday.io/project/20628-open-simple-lidar#menu-description

.. _`github` : https://github.com/iliasam/OpenSimpleLidar




Les fixes (Plus près des TOF)
======================================
`LIDAR lite v3HP`_ 150USD sans les frais de port 216€ chez ali - interface I2C

LIDAR-Lite V3 179€ chez `Go-Tronic`_

Range 4cm à 40m !

Spread of the beam:
Distance/100 = beam diameter at that distance
Environ 1/2 ° ou 8 milliradian

----------------------------------------------------------------------------------------------------

La série des TF de chez Benewake

`TF mini : 27.33€ Banggood`_ (en promo): FOV 2.3° max 12m

.. image:: images/tfminiSize.jpg
   :width: 400 px
   :alt: Benewake TF mini dimensions
   :align: center

.. _`TF mini : 27.33€ Banggood` : https://www.banggood.com/fr/TOF-Mini-TFmini-Lidar-Range-Finder-Sensor-Module-Single-Point-Micro-Ranging-for-Arduino-Pixhawk-Drone-UART-Version-p-1561172.html?gmcCountry=FR&currency=EUR&createTmp=1&utm_source=googleshopping&utm_medium=cpc_union&utm_content=frank&utm_campaign=ssc-fr-all-0508-13anv&ad_id=347288687735&gclid=Cj0KCQiAz53vBRCpARIsAPPsz8VNiq_KRyU9POU-jqng6P97bfjub5p5roLcQGiGpMccDrCMAc5ao6kaAjByEALw_wcB&cur_warehouse=CN

TF-mini plus: 41.16€ chez ali FOV 3.6° 0.1 à 12m

.. image:: images/tfminiplusSize.jpg
   :width: 400 px
   :alt: Benewake TF mini plus dimensions
   :align: center

TF-03 : 0.1 à 100m FOV 0.5° Prix 408.76€ banggood et 190€ chez `Robotshop`_ ...

.. _`Robotshop` : https://www.robotshop.com/eu/fr/scanner-laser-360-ydlidar-x2.html?gclid=Cj0KCQiA5dPuBRCrARIsAJL7oejQtDc9_YCCkfvmHWWn4Qu7373e6-FC7K3W6UB8-6410JZqWl3jM0EaAjoaEALw_wcB

76€

----------------------------------------------------------------------------------------------------

`Un Lidar à 30€`_ exemple d'utilisation très complet sur `le site de ROS`_


.. _`Un Lidar à 30€` : https://www.ebay.fr/itm/1-Stck-Laserradarscanner-mit-Kabel-Lidar-Sensor-Fur-HLS-LFCD2-360-2D-LiDAR/223683738247?_trkparms=aid%3D555018%26algo%3DPL.SIM%26ao%3D1%26asc%3D20131003132420%26meid%3D93c872e753aa4ccda528905f670152f8%26pid%3D100005%26rk%3D3%26rkt%3D12%26mehot%3Dco%26sd%3D254430082108%26itm%3D223683738247%26pmt%3D1%26noa%3D0%26pg%3D2047675&_trksid=p2047675.c100005.m1851

.. _`le site de ROS` : http://wiki.ros.org/hls_lfcd_lds_driver


================================
Capteur ToF
================================
`GY-530 VL53L0X Banggood`_ 9.27€

I2C : gros inconvénients : il faut fixer sons adresse par soft à chaque démarrage ! Si on en veut
plusieurs sur le bus.

FOV de 25°C

.. _`GY-530 VL53L0X Banggood` : https://www.banggood.com/GY-530-VL53L0X-Laser-Ranging-Sensor-Module-IIC-Communication-Ranging-Module-p-1201341.html?rmmds=search&cur_warehouse=CN


`TOF10120`_ 10.8€+3.91€ de FdP chez aliExpresse ou 8.19€ chez Banggood
ou encore 4.73€ `chez CDiscount`_ FdP ?


10 à 180cm, UART et I2C

`Un exemple d'utilisation sur Hackster.io`_

.. code:: cpp

    void SensorRead(unsigned char addr,unsigned char* datbuf,unsigned char cnt) 
    {
      unsigned short result=0;
      // step 1: instruct sensor to read echoes
      Wire.beginTransmission(82); // transmit to device #82 (0x52)
      // the address specified in the datasheet is 164 (0xa4)
      // but i2c adressing uses the high 7 bits so it's 82
      Wire.write(byte(addr));      // sets distance data address (addr)
      Wire.endTransmission();      // stop transmitting
      // step 2: wait for readings to happen
      delay(1);                   // datasheet suggests at least 30uS
      // step 3: request reading from sensor
      Wire.requestFrom(82, cnt);    // request cnt bytes from slave device #82 (0x52)
      // step 5: receive reading from sensor
      if (cnt <= Wire.available()) { // if two bytes were received
        *datbuf++ = Wire.read();  // receive high byte (overwrites previous reading)
        *datbuf++ = Wire.read(); // receive low byte as lower 8 bits
      }
    }

Le composant au dos est 3AQ20 : `Nuvoton 1T 8051-based Microcontroller N76E003`_ donc en fait on ne
sait pas les registres I2C mise à part cet exemple ci-dessus.

Malgrés tout mes efforts, je n'ai pas réussi à retrouver la datasheet du TOF10120 pour avoir la
doc complète de l'I2C `tout au plus un truc ressemblant`_ dans datasheet library :-(

 

.. _`TOF10120` : https://fr.aliexpress.com/item/32901237079.html 

.. _`chez CDiscount` : https://www.cdiscount.com/bricolage/outillage/module-de-capteur-de-distance-au-laser-tof10120-10/f-166010207-auc0719233329344.html?idOffre=429858924&ef_id=Cj0KCQiAz53vBRCpARIsAPPsz8Ur8SCVxJeb_TKG6BrvTKTvJ3cl7fCAk5JTl492WT9-ez9td0uH5mIaAtxDEALw_wcB:G:s&cid=search_pla&cm_mmc=PLA!COR!BRI!MP!985045426!m137249482_pAUC0719233329344-429858924_&gclid=Cj0KCQiAz53vBRCpARIsAPPsz8Ur8SCVxJeb_TKG6BrvTKTvJ3cl7fCAk5JTl492WT9-ez9td0uH5mIaAtxDEALw_wcB

.. _`Un exemple d'utilisation sur Hackster.io` : https://www.hackster.io/SurtrTech/tof-10120-laser-rangefinder-to-measure-distance-lcd-9e549a

.. _`Nuvoton 1T 8051-based Microcontroller N76E003` : https://datasheet.lcsc.com/szlcsc/Nuvoton-Tech-N76E003AQ20_C90832.pdf

.. _`tout au plus un truc ressemblant` : https://drive.google.com/file/d/1uaMZ421smI0FN40iJgn-ZKQG42KUvFfh/view

=========
Weblinks
=========

.. target-notes::









