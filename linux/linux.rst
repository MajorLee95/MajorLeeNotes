.. index:: Linux

++++++++++++++++++++++++++++++++
LINUX *
++++++++++++++++++++++++++++++++

:Auteur: J.Soranzo
:Date: Octobre 2019
:Societe: VoRoBoTics
:Entity: VoLAB

.. contents:: TdM LINUX
    :backlinks: top


Ci dessous mes notes personnelles concernant Linux. Comme je n'ai pas de mémoire, 
il s'agit principalement ici de lignes commandes que j'ai trouvé intéressantes.
(Reprise carte Heuristique en cours...)

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
   

====================================================================================================
Programmation shell
====================================================================================================
`Sur Paristech`_

.. _`Sur Paristech` : https://perso.telecom-paristech.fr/dax/polys/tp-c-shell/

http://www.gecif.net/articles/linux/gcc.html

Man référence en français sur `manpagesfr.free.fr`_

.. _`manpagesfr.free.fr` : http://manpagesfr.free.fr/man/man3/Index.3.html

Les différents shell
======================================
Les différents shell:

 - sh : Bourne Shell. L'ancêtre de tous les shells.
 - bash : Bourne Again Shell. Une amélioration du Bourne Shell, disponible par défaut sous Linux et Mac OS X.
 - ksh : Korn Shell. Un shell puissant assez présent sur les Unix propriétaires, mais aussi disponible en version libre, compatible avec bash.
 - csh : C Shell. Un shell utilisant une syntaxe proche du langage C.
 - tcsh : Tenex C Shell. Amélioration du C Shell.
 - zsh : Z Shell. Shell assez récent reprenant les meilleures idées de bash, ksh et tcsh.


.. index::
    pair: Linux; Shebang

Le fameux shebang qu'on met au début des scripts::

- En début de script ::

    #!/bin/sh -x
    #!/bin/bash
    #!/usr/bin/perl
    #!/usr/bin/tcl
    #!/bin/sed -f
    #!/usr/awk -f
    #!/usr/bin/python

Connaître son shell : tout simplement help !

----------------------------------------------------------------------------------------------------

================================
Mes commandes intéressantes
================================

.. index ::
   pair: Linux; Commandes system
   
System
===========

- répéter la dernière commande en sudo : ``sudo !!``

- Liste des ports USB : lsusb
   cette commande ne dit pas par exemple sur quoi est mappé le périphérique
   
   Par exemple lsusb tty.
- List des port com : ``ls /dev/tty*``
- Lister les disque:

 - lshw -C disk
 - sudo fdisk -l : list les disk avec info technique et fdisk seul
 - sfdisk -l -uM
 - df : only mounted file systems
 - parted -l list les partitions

- @ : ctrl+shift+u + 0040
- \ :              + 005c

- gestionnaire de packet synaptique

.. index:: Réseau

- connaître les interfaces réseau : ifconfig

.. index:: apt update, apt upgrade, apt-get update, apt-get upgrade

- ``apt-get update`` versus ``upgrade`` : update met à jour les dépots, upgrade met à jour les packets installés


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

- rebooter en ligne de commande: ``sudo reboot`` ou ``sudo shutdown -r``  

- Savoir si un commande est installée : ``dpkg -l | grep le_nom_du_paquet`` ou ``command -v command`` 
  ou encore ``which cmd``
 
.. index ::
   single: Linux; Commandes utilisateur
   
- les appli installées ``dpkg -l``

- Qui écoute quel port : ``sudo lsof -i -P -n | grep LISTEN``

- voir les dernière info hardware ``dmesg`` 


 
Pour les utilisateurs
======================================

- list des group d'un utilisateur : groups nom
- changer d'utilisateur : su nom
- se mettre root pour éviter de taper sudo sudo -s
- Liste des utilisateurs dans un système: ``cut -d: -f1 /etc/passwd``
- lister tous les groups : ``less /etc/groups``
- lister tous les utilisateurs d'un groupe
- lister tous les groupes d'un utilisateur : ``groups username``
- ajouter un utilisateur a un group : ``usermod -a -G examplegroup exampleusername``

----------------------------------------------------------------------------------------------------

.. index::
    single: Linux; cron
	single: Linux; Tâches planifiées

================================
Cron
================================
Il s'agit ici de lancer un programme de manière cyclique sans intervention évidement.

Dans le journal de manip de Pierre, `créer une tâche planifiée`_, il n'y a vraiment que la base 
de la base ! 

.. _`créer une tâche planifiée` : https://poltergeist42.github.io/JDM/Linux.html#creer-une-tache-planifie-cron

====================================================================================================
Comment lancer une appli au boot
====================================================================================================
Là c'est différent l'appli n'est lancée qu'une seule fois au démarrage.

`JdMdP partie lancer une appli au boot`_

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


.. _`JdMdP partie lancer une appli au boot` : https://poltergeist42.github.io/JDM/Linux.html#pour-creer-un-script-qui-sexecute-au-demarrage-du-systeme



.. index::
    pair: Linux; Samba

================================
Samba
================================
Tout est dit dans le `JdMdP rubrique SAMBA`_

.. _`JdMdP rubrique SAMBA` : https://poltergeist42.github.io/JDM/Linux.html#creer-un-dossier-partage-avec-samba

Par rapport à la doc de Pierre : smbpasswd crée l'utilisateur et demande la création du mdp dans la
foulée. Il est nécessaire que cet utilisateur existe au niveau Linux.

.. WARNING::
    Ne pas taper smbpasswd sans rien !
	
La `doc officielle Samba`_ mais n'apporte pas grand chose ! Trop complexe.

.. _`doc officielle Samba` : https://wiki.samba.org/index.php/Main_Page

Même si samba gère des mdp différents du système il n'empêcha que l'utilisateur samba doit existé en
 tant qu'utilisateur système. Par défaut Samba partage le home dir de l'utilisateur en read only. 

----------------------------------------------------------------------------------------------------

.. index::
    pair: Linux; Partage

.. _ref_linuxPartage:

====================================================================================================
LINUX Partage de répertoire
====================================================================================================
Ou monter un répertoire d'une autre machine

.. code::

    mkdir /mnt/partage_nfs
    # Montage d'un partage en NFS
    mount -t nfs 192.168.1.12:/dossier/partage /mnt/partage_nfs

----------------------------------------------------------------------------------------------------


.. index::
    single: Makefile

====================================================================================================
Les Makefile (en bref)
====================================================================================================
Mis ici en attendant d'avoir un emplacment dédié à la compilation

Commentaires : #

.PHONY : 


`ce mon lien`_

.. _`ce mon lien` : file:///C:/Users/F073258/Documents/jojoBag/taf/cocotier_2021/travauxPAD/documentation/build/html/home.html 

`make sur Wikipédia`_

.. _`make sur Wikipédia` : https://fr.wikipedia.org/wiki/Make

Et `sur l'Université Lyon1`_

.. _`sur l'Université Lyon1` : http://perso.univ-lyon1.fr/jean-claude.iehl/Public/educ/Makefile.html

Exemples détaillés `sur cs.colby.edu`_

.. _`sur cs.colby.edu` : https://www.cs.colby.edu/maxwell/courses/tutorials/maketutor/

Des cibles, des règles, des macro et eventuellement des suffixes.

Règles::

    cible [cible ...]: [composant ...]
    [tabulation] commande 1

    La « cible » est le plus souvent un fichier à construire, mais elle peut aussi définir 
    une action (effacer, compiler…).

    Les « composants » sont des pré-requis nécessaires à la réalisation de l'action définie 
    par la règle.

    Autrement dit, les « composants » sont les cibles d'autres règles qui doivent être réalisées 
    avant de pouvoir réaliser cette règle.

Macro::

    Les macros peuvent être composées de commandes shell en utilisant l'accent grave (`) :

    Il existe aussi des 'macros internes' à make :

        $@ : fait référence à la cible.
        $? : contient les noms de tous les composants plus récents que la cible.
        $< : contient le premier composant d'une règle.
        $^ : contient tous les composants d'une règle.

    our utiliser une macro, il faut procéder à son expansion en l'encapsulant dans $() ou ${}. 
    Par exemple, pour utiliser la macro CC, il faudra écrire $(CC)

    Il existe plusieurs manières de définir une macro :

        Le = est une affectation par référence (on parle d'expansion récursive)
        Le := est une affectation par valeur (on parle d'expansion simple)
        Le ?= est une affectation conditionnelle. Elle n'affecte la macro que si cette dernière n'est pas encore affectée.
        Le += est une affectation par concaténation. Elle suppose que la macro existe déjà.

Suffixe::

    '%.o : %.c' (où % signifie n'importe quel nom de fichier)
    La syntaxe pour définir la liste des suffixes est : .SUFFIXES: .suffixe_source .suffixe_cible
    La syntaxe pour utiliser une règle de double suffixes est : .suffixe_source.suffixe_cible :
    Exemple : .c.o:
    une règle de suffixe ne peut avoir de cible (autre après les :)


.. index::
    pair: Linux; Redirections

====================================================================================================
Redirections
====================================================================================================
::
    
    >> vers un fichier (append)
    > vers un nouveau fichier
    > /dev/null

    2>error.log redirige les erreurs vers un fihcier de log (2 désigne stderr tout simplement)
    ou 2>>err.log pour un append

    2>&1 : indique qu'il faut rediriger les erreurs vers la sortie standard




=========
Weblinks
=========

.. target-notes::