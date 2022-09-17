++++++++++++++++++++++++++++++++
Astuces informatiques
++++++++++++++++++++++++++++++++

:Auteur: J.Soranzo
:Date: Novembre 2019
:Societe: VoLAB
:Entity: VoRoBoTics

.. contents:: Table_name
    :backlinks: top


.. index::
    pair: Astuce; Microsoft


================================
Microsoft
================================

Connaître le type de licence Windows10 
===========================================================================

slmgr -dli

défaire des connexions réseau existantes 
==========================================
net use /DELETE *

Copier une arborescence 
======================================
Copy arbo :XCOPY source destination  /T /E


.. index:: Copier des fichiers

copy de fichiers plus rapide
======================================

Commande pour copier de fichiers plus rapidement qu'avec l'explorer de Windows.

.. code::

    robotcopy __soureDir __destDir /mir /r:1 /w:1 /v
    ou
    robotcopy __soureDir __destDir /mir /v

Copier des fichiers efficacement

Ou alors :index:`fastcopy` !

.. index::
    single: Virtual keyboard
    single: Clavier virtuel

Afficher le clavier virtuel
======================================
Dans la barre de recherche taper : **osk** (testé sous W7 & W10)

Identifier un driver
===============================
Pour identifier un :index:`driver`.


Site `driveridentifier.com`_

.. _`driveridentifier.com` : https://www.driveridentifier.com/

  Ne pas passer par le site mais taper directement dans google:
  driveridentifier lenomdudriver
  
.. index:: Gestionnaire de fichier, Barre des tâches

Gestionnaire de périphérique dans la barre des tâches 
======================================================= 
  
Le gestionnaire de fichier dans la barre des taches:
Créer tout simplement un lien vers le fichier suivant:

  dans Windows/system32 fichier devmgmt.msc

Sous Windows 10 ce n'est plus vraiment nécessaire puisque un clic droit sur l'icône démarrer
permet d'y accéder rapidement.

#####

.. index::
    single: Windows; Change variable - CLI
    single: Windows; set PATH


Modification d'une variable en mode console 
=============================================================
::

    set PATH=%PATH%;nouveau_chemin


Configuration réseau en cmd admmin 
====================================================================================================

utilisation de netsh.  `Une page web netsh utile`_

.. _`Une page web netsh utile` : https://www.malekal.com/comment-utiliser-ipconfig-et-netsh/

netsh peut être utilisé soit en ligne de commande full ou de manière interractive.

Ligne de commandes::

    netsh interface ip4 set address name="nomdelinterface" source=dhcp
    netsh interface ipv4 set address name="nomdelinterface" static IP netmask passerelle
    netsh interface ipv4 show config
    netsh interface show interface
    

En mode interractive, ce sont les même commandes (très appréciable mais qu'on retre petit à petit
et avec un prompt. Exemple: on tape d'abord netsh, on a alors le prompt::

    netsh>

Puis on saisie interface, et là, le prompt devient::

    netsh interface>

En quelque sorte, opn est descendu d'un cran et on paut alors utilisé toutes les commandes en lien
avec interface. Pour remonter d'un cran c'est .. et pour tout quitter bye. Dernier truc::

    netsh>help : le help fonctionne dans les différents niveaux

.. index::
    single: html; page minimale


Clear de la console
====================================================================================================
Sous Linux clear

Sous Windows cls !

====================================================================================================
HTML
====================================================================================================
une page html minimale: sur `Boostrap get started`_

.. _`Boostrap get started` : https://getbootstrap.com/docs/4.5/getting-started/introduction/

Ou dans Visual Studio Code : nouveau fichier, en bas à droite passer de ``plain text`` à ``html``
puis taper html (normalement provoque l'affichage du snippet html:5)


.. index::
    single: binaires; ordre de grandeurs

====================================================================================================
Les nombres en binaires, ordres de grandeur
====================================================================================================
- 1k = 1024 = 2^10
- 1 Méga = 1024 * 1024 = 2^20
- 1 Giga = 1024 * 1024 * 1024 = 2^30 = 1 073 741 824 un peu plus de 1 milliard
- 1 Téra = 2^40 = 1 099 511 627 776 un pleu plus de 1099 milliard

Il existe des unité au dessus:

- 1 Péta = 2^50
- 1 Exa = 2^60

- 2^8 : 256 
- 2^16 : 16356 soit 1k
- 2^32 = 4 294 967 296 soit un peu plus de 4 milliard  2^(32-20) = 2^12 Méga = 4096 Méga = 2^2 Giga !
- 2^64 = 18 446 744 073 709 551 616 un peu plus de 18 milliard de milliard ou encore 18*10^18 2^24 Téra

2^128:

- 2^(2^6) = 340 282 366 920 938 463 463 374 607 431 768 211 456 comme on prononce ce nombre ?
- 2^40 * 2^40 * 2^40 * 2^8 soit 256 Téra de Téra de Téra
- 3.4*10^38 vs 10^9 : 38/9 environ 4 donc 3.4 milliard de milliard de milliard de milliard


.. index::
    single: Taille écrans
    single: Format images

====================================================================================================
Taille des écrans
====================================================================================================
Source `wikipedia List of common resolutions`_

.. _`wikipedia List of common resolutions` : https://en.wikipedia.org/wiki/List_of_common_resolutions

.. image:: images/Vector_Video_Standards.svg 
   :width: 600 px



=========
Weblinks
=========

.. target-notes::