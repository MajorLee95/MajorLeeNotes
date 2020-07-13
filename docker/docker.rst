++++++++++++++++++++++++++++++++
Docker*
++++++++++++++++++++++++++++++++

:Auteur: J.Soranzo
:Date: Janvier 2020 2019
:Societe: VoRoBoTics
:Entity: VoLAB

.. contents::
    :backlinks: top

================================
Start-up /install
================================
Pas la même install qu'il s'agisse de Windwos10pro d'un côté et Windwos10 family ou 7 de l'autre

`Note Docker Pierre`_

.. _`Note Docker Pierre` : https://poltergeist42.github.io/JDM/Docker.html

`Docker sur Openclassroom`_

.. _`Docker sur Openclassroom` : https://openclassrooms.com/fr/courses/2035766-optimisez-votre-deploiement-en-creant-des-conteneurs-avec-docker/6211306-decouvrez-les-conteneurs

Je me permet un petit commentaire sur ce cours. Il n'est vraiment pas terrible !

Une pauvre recette de cuisine sur dockerfile et sur compose très incomplète.

Par exemple on y évoque pas le partage de volume.

L'exercice de fin de chapitre sur nginx est juste une blague ! Attention tips, on ne demande pas
de démarrer le serveur nginx ni même de la paraméter, juste de l'installer ! Faites au plus 
simple

- Docker Community Edition (Linux seulement) ;
- Docker Desktop (Mac ou Windows) ;
- Docker Enterprise (Linux seulement).
- Docker toolbox (Pour wondows 7 par exemple)

Un bon tut, je crois : `docker-curriculum`_

.. _`docker-curriculum` : https://docker-curriculum.com/

Au cours de ce tutoriel en englais on apprends à déployer une apppli web static et 
2 appli dynamiques

Dockerhub
====================================================================================================

Le `site docker hub`_ directement sur la page de recherche/exploration

3 702 709 available images le 06/07/2020. 

.. _`site docker hub` : https://hub.docker.com/search?q=&type=image

on y trouve par exemple une image nommée gcc, gitlab, nextcloud, owncloud, mongo-express, drupal...

================================
Notes
================================
J'aime bien cette définition :
Quand une application tourne dans un conteneur, elle a l’illusion d’être la seule à avoir accès 
au **système** (sous-entendu l'OS). Ceci n’est pas sans rappeler la virtualisation, où un OS invité
a l’illusion d’être le seul à exploiter le **hardware** sous-jacent.

Par principe Docker ne doit faire tourner qu'un seul processus.

Ainsi, dans le cas d'une stack LAMP (Linux, Apache, MySQL, PHP), nous devons créer 3 conteneurs 
différents, un pour Apache, un pour MySQL et un dernier pour PHP.


Immutable

Ce que c'est ::

    Docker is a platform for developers and sysadmins to build, share, and run applications.
    
ça c'est la `définition officielle`_ . Cela ne dit pas "développer" de quelles applications. Le gros
sous entendu c'est que ce sont des applications plutôt à forte propension WEB.

.. _`définition officielle` : https://docs.docker.com/get-started/

Article très intéressant  `Docker est mort, vive Docker`_ sur le fonctionnement de docker (2019)

.. _`Docker est mort, vive Docker` :  https://blog.engineering.publicissapient.fr/2019/12/23/docker-est-mort-vive-docker/

Ma Rapide présentation pratique
====================================================================================================

Docker ça fait tourner des images que l'on peut récupérer sur dockerhub ou dans un autre dépôt.
Ok c'est cool mais ce qui est encore plus cool c'est qu'on peut construire de nouvelles images
basées sur des images existantes à la façon des poupées russes (c'est le rôle des 
dockerfiles voir `Créer une image`_  ). ça c'est déjà pas mal mais ce n'est pas suffisant.

En effet, comme docker ne fait tourner qu'une seule tâche, process... ou quelque soit le terme
utilisé, on pourrait dire aussi un seul truc, eh bien il faut en lancer plusieurs, le cas type est
le **serveur web** qui utilise une **base de données** au travers de **php** pour cela il faut 
lancer 3 images. C'est la qu'intervient docker compose voir `Syntaxe des fichiers Docker compose`_

Une images n'est pas un container et inversement. Donc, il faut apprendre à manipuler les 2.
On peut créer une image sans pour autant la lancer et on peut lancer une image sans la créer.
On peut également effacer des images et des container de son système, on peut lister les 2 mais 
pas avec les mêmes commandes !

====================================================================================================
Documentation
====================================================================================================
Officiellement c'est là : `Docker's documentation`_


Mais c'est mieux de commencer par l'`onglet Product manual`_ et plus particulièrement avec les 

`docker for Windows`_, `docker for Mac`_

La référence pour les options et commandes de la ligne de commande est:
`Use the Docker command line`_

.. _`Docker's documentation` : https://docs.docker.com/

.. _`onglet Product manual` : https://docs.docker.com/install/

.. _`docker for Windows` : https://docs.docker.com/docker-for-windows/

.. _`docker for Mac` : https://docs.docker.com/docker-for-mac/

.. _`Use the Docker command line` : https://docs.docker.com/engine/reference/commandline/cli/


====================================================================================================
Commandes principales
====================================================================================================


Voir sur `Note Docker Pierre`_ il y a tout ce qu'il faut !

Cheatsheet ?

::

    docker run -d -p 8080:80 nginx
    docker images <=> docker image ls
    docker ps : shows you all containers that are currently running
    docker ps -a : shows all containers
    docker rmi : efface une ou plusieurs images
    docker rm : efface un container
    docker restart
    docker build -t _nom .
    docker container prune <=> docker rm $(docker ps -a -q -f status=exited)
    docker run --interactive --tty ubuntu bash
    docker stop _nom
    

    
On ne le dira jamais assez :

.. DANGER::
    Do not use PowerShell ISE


Interactive terminals do not work in PowerShell ISE (but they do in PowerShell).
See docker/for-win/issues/223.

====================================================================================================
Créer une image
====================================================================================================
Dans un répertoire vierge créer un fichier nommer dockerfile

Lancer la commande docker build (éventuellement avec -t pour préciser un nom d'image)

Syntaxe des fichiers Dockerfile 
===========================================================

`Docker file ref`_

Les commandes dans les dockerfile ne sont pas sensibles à la casse mais par convention on les met
en majuscules pour les distinguer des arguments.

Les lignes de commentaire COMMENCE par un #

La commande pour compiler, la plus simple, est alors ::

    docker build .
    
Il est bon aussi de bien lire : `Best practices for writing Dockerfiles`_

Le build ne dispense pas de faire un run ensuite

.. _`Docker file ref` : https://docs.docker.com/engine/reference/builder/

.. _`Best practices for writing Dockerfiles` :  https://docs.docker.com/develop/develop-images/dockerfile_best-practices/

====================================================================================================
Syntaxe des fichiers Docker compose
====================================================================================================

Docker compose permet de lancer plusieurs images en même temps.

Dans un répertoire vide (conseillé) créer un fichier docker-compose.yml

`Compose file version 3 reference`_

.. _`Compose file version 3 reference` : https://docs.docker.com/compose/compose-file/

====================================================================================================
Piloter un port série de la machine hote
====================================================================================================

https://www.losant.com/blog/how-to-access-serial-devices-in-docker



====================================================================================================
My tips
====================================================================================================
.. index::
    single: Docker; Disk image locations tips

    
Disque image locations : peut-être configurer dans la fenêtre setting de docker onglet Ressources/
advanced

.. index::
    single: Docker; File sharing tips

Partage de données entre hôte et containers::

    File sharing is required for mounting volumes in Linux containers, not for Windows containers.
    For Linux containers, you need to share the drive where the Dockerfile and volume are located. 
    Otherwise, you get file not found or cannot start service errors at runtime. 
    See Volume mounting requires shared drives for Linux containers.

Docker dashboard : gestion intéractive graphique des container/appli compose 
**en cours d'éxécution**


Dans docker port container_name
L'affichage produit est ::

    container --> localhost:port

Alors que dans::

    docker run -p 8888:80 site

On a d'abord le port de l'hôte suivi du port de l'image !

Faire du python2 sans l'installer::

    docker run -i -t python:2




================================
Vocabulaire
================================

.. index::
    pair: Docker; Stateful
    pair: Docker; Stateless

Stateful vs Stateless : se dit à propos d'une application ou d'un service et par extension cela
s'applique aux container.

`Stateless vs Stateful article sur contino.io`_

.. _`Stateless vs Stateful article sur contino.io` : https://www.contino.io/insights/stateless-vs-stateful-containers-whats-the-difference-and-why-does-it-matter

A stateless application is one that neither reads nor stores information about its state from
one time that it is run to the next. 

Une `explication sur Publicis Sapiens`_

.. _`explication sur Publicis Sapiens` : https://blog.engineering.publicissapient.fr/2007/07/24/service-stateful-vs-service-stateless/

Un moyen de stockage est nécessaire pour une application, un service stateful.


Images : 

    **Base images** are images that have no parent image, usually images with an OS like ubuntu, busybox or debian.

    **Child images** are images that build on base images and add additional functionality.

Then there are official and user images, which can be both base and child images.

    **Official images** are images that are officially maintained and supported by the folks at 
    Docker. These are typically one word long. In the list of images above, the python, ubuntu, 
    busybox and hello-world images are official images.

    **User images** are images created and shared by users like you and me. They build on base 
    images and add additional functionality. Typically, these are formatted as user/image-name.

.. index::
    single: Docker; detach mode

**detached mode** mode détaché : à compléter le 6/07/2020, en gros c'est la même chose que & 
à la fin d'un commande Linux

=========
Weblinks
=========

.. target-notes::
