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
======================================
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

 
=========
Weblinks
=========

.. target-notes::