.. index:: Linux

++++++++++++++++++++++++++++++++
LINUX *
++++++++++++++++++++++++++++++++

:Auteur: J.Soranzo
:Date: Octobre 2019
:Societe: VoLAB
:Entity: VoRoBoTics

.. contents:: TdM LINUX
    :backlinks: top


Ci dessous mes notes personnelles concernat Linux. Comme je n'ai pas de mémoire, 
il s'agit principalement ici de lignes commandes que j'ai trouvé intéressantes.
(Reprise carte Heurisitque en cours...)

================================
Doc
================================
Avant que de n'aller plus loin, jeter un oeil au `journal de manip de Pierre partie Linux`_ . 
Dans la suite abrégé JdMdP

`Un cours complets sur Linux France.org`_

.. _`journal de manip de Pierre partie Linux` : https://poltergeist42.github.io/JDM/Linux.html

.. _`Un cours complets sur Linux France.org` : http://www.linux-france.org/prj/edu/archinet/systeme/index.html 

----------------------------------------------------------------------------------------------------

.. index ::
   pair: Linux; Shells
   
================================
Shell programming
================================

Les différents shell
======================================
Les différents shell:

 - sh : Bourne Shell. L'ancêtre de tous les shells.
 - bash : Bourne Again Shell. Une amélioration du Bourne Shell, disponible par défaut sous Linux et Mac OS X.
 - ksh : Korn Shell. Un shell puissant assez présent sur les Unix propriétaires, mais aussi disponible en version libre, compatible avec bash.
 - csh : C Shell. Un shell utilisant une syntaxe proche du langage C.
 - tcsh : Tenex C Shell. Amélioration du C Shell.
 - zsh : Z Shell. Shell assez récent reprenant les meilleures idées de bash, ksh et tcsh.

- En début de script : #!/bin/bash

----------------------------------------------------------------------------------------------------

================================
Mes commandes interressantes
================================

.. index ::
   pair: Linux; Commandes system
   
System
===========

- Liste des ports USB : lsusb
   cette commande ne dit pas par exemple sur quoi est mappé le périphérique
   
   Par exemple lsusb tty.
- List des port com : ls /dev/tty*
- Lister les disque:

 - lshw -C disk
 - fdisk -l
 - sfdisk -l -uM
 - df : only mounted file systems
 - parted -l list les partitions

- @ : ctrl+shift+u + 0040
- \ :              + 005c

- gestionnaire de pacquet synaptique

.. index:: Réseau

- connaître les interfaces réseau : ifconfig

.. index:: apt update, apt upgrade, apt-get update, apt-get upgrade

- apt-get update versus upgrade : update met à jour les dépots, upgrade met à jour les packets installés


- nom de la machine et autre info cat /proc/cpuinfo
- list repo : grep ^[^#] /etc/apt/sources.list /etc/apt/sources.list.d/*
- Quel os ?

.. index ::
   single: Linux; version OS

.. code::

		cat /proc/version
			Version du noyau Linux
		cat /etc/issue
			Nom et version de la distribution
		cat /etc/os-release
		cat /proc/cpuinfo

.. index ::
   single: Linux; Redémarrer

- rebooter en ligne de commande: 
 
   - sudo reboot
   - sudo shutdown -r  

- Savoir si un commande est instaléé : dpkg -l | grep le_nom_du_paquet		
 
.. index ::
   single: Linux; Commandes utilisateur
 
Pour les utilisateurs
======================================

- list des group d'un utilisateur : groups nom

----------------------------------------------------------------------------------------------------

.. index::
    single: Linux; cron
	single: Linux; Tâches planifiées

================================
Cron
================================
Il s'agit ici de lancer un programm de manière cyclique sans intervention évidement.

Dans le journal de manip de Pierre, `créer une tâche planifiée`_

.. _`créer une tâche planifiée` : https://poltergeist42.github.io/JDM/Linux.html#creer-une-tache-planifie-cron

====================================================================================================
Comment lancer une appli au boot
====================================================================================================
Là c'est différent l'appli n'est lancée qu'une seule fois au démarrage.

`JdMdP partie lancer une appli au boot`_

.. _`JdMdP partie lancer une appli au boot` : https://poltergeist42.github.io/JDM/Linux.html#pour-creer-un-script-qui-sexecute-au-demarrage-du-systeme 


:Liens_Web:
	
	https://poltergeist42.github.io/JDM/Linux.html#pour-creer-un-script-qui-s-execute-au-demarrage-du-syteme

::

		etc/init.d/skeleton
		un script quelque part
		rc.local
			méthode Djamel
		méthode Adafruit
			sudo update-rc.d hostapd enable 
			sudo update-rc.d isc-dhcp-server enable
		systemd
			vise à remplacer init.d pour la gestion des services
				source : livre : Linux Embarqué page 20
			Il a pour but d'offrir un meilleur cadre pour la gestion des dépendances entre services, de permettre le chargement en parallèle des services au démarrage, et de réduire les appels aux scripts shell.
				src wikipedia

================================
Samba
================================
Tout est dit dans le `JdMdP rubrique SAMBA`_

.. _`JdMdP rubrique SAMBA` : https://poltergeist42.github.io/JDM/Linux.html#creer-un-dossier-partage-avec-samba


.. WARNING::
    Ne pas taper smbpasswd sans rien !
	
La `doc officielle Samba`_ mais n'apporte pas grand chose ! Trop complexe.

.. _`doc officielle Samba` : https://wiki.samba.org/index.php/Main_Page

Même si samba gère des mdp différents du système il n'empêcha que l'utilisateur samba doit existé en
 tant qu'utilisateur système. Par défaut Samba partage le home dir de l'utlisateur en read only. 

----------------------------------------------------------------------------------------------------

.. index::
    pair: Linux; Partage

====================================================================================================
LINUX Partage de répertoire
====================================================================================================
Ou monter un répertoire d'une autre machine

.. code::

    mkdir /mnt/partage_nfs
    # Montage d'un partage en NFS
    mount -t nfs 192.168.1.12:/dossier/partage /mnt/partage_nfs

----------------------------------------------------------------------------------------------------

=========
Weblinks
=========

.. target-notes::