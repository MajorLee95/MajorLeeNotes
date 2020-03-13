.. index::
    single: NUCLEO; Board
    
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
NUCLEO board
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

:Auteur: J.Soranzo
:Date: Mars 2020
:Societe: VoLAB
:Entity: VoRoBoTics

.. contents::
    :backlinks: top

.. _refNucleoBoard:

====================================================================================================
Présentation
====================================================================================================
3 type de cartes 32, 64, 144 : fonction de la taille du boîtier du composant utiliés!

LQFP64 package, LQFP144 package

`NUCLEO-overview`_

.. _`NUCLEO-overview` : https://www.st.com/en/evaluation-tools/stm32-nucleo-boards.html#overview

`NUCLEO-144_MOUSER`_

.. _`NUCLEO-144_MOUSER` : https://www.mouser.fr/new/stmicroelectronics/stm-stm32-nucleo-144-dev-boards/


====================================================================================================
Mes manips
====================================================================================================
Décembre 2015, journal de manip en version OpenOffice, aidé du `livre de Carmine Noviello`_

.. _`livre de Carmine Noviello` :  http://leanpub.com/mastering-stm32

Dans son livre Carmine porpose d'installer un chaine de développement basée sur Eclipse et GCC
et s'en explique...

Installation des outils::

    Install dans c:\STM32Toolchaine comme décrit dans le livre pour ne pas être emmerdé 
    dans un premier temps.
    Dézippe versin 64bits => une ereur à propos des plug in
    dl java mais passage de la page it à fr.
    Premier lancement d'Eclipse => error java
    installjava => toujours la même erreur.
    Recommencer avec version 32 bits, ça marche.
    Install ECLIPSE + Plugin : OK
    Install GCC-arm avec le conseil sur le PATH suivi.
    Install Build Tools :
    Dl version 32 bits
    Installation sans problème
    openocd : pas d'install, juste un unzip et un rennommage
    ST Tools
    STM32CubeMX => ok
    ST-LINK Utility => ok
    Install Nucleo drivers: dl sous forme de zip, renommage du fichier en NucleoDriver.zip
    Upgrade ST-LINK firmware OK
    Temps pour installer tout ça 3 heures
    Next stage hello word
    
    à suivre...


Manip micro Python cf journal au 25/12/2015 (à récupérer pour mettre ici)

====================================================================================================
FreeRTOS sur NUCLEO
====================================================================================================

Voir dans: :ref:`FreeRTOS on STM32 NUCLEO<refFreeRtosStm32>`

====================================================================================================
Weblinks
====================================================================================================

.. target-notes::
