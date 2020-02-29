++++++++++++++++++++++++++++++++
Docker
++++++++++++++++++++++++++++++++

:Auteur: J.Soranzo
:Date: Janvier 2020 2019
:Societe: VoLAB
:Entity: VoRoBoTics

.. contents::
    :backlinks: top

================================
Start-up
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

Stateful et Stateless

Immutable

Ce que c'est ::

    Docker is a platform for developers and sysadmins to build, share, and run applications.
    
ça c'est la `définition officielle`_ . Cela ne dit pas développer de quelles applications. Le gros
sous entendu c'est que ce sont des applications plutôt à forte propention WEB.

.. _`définition officielle` : https://docs.docker.com/get-started/


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
    docker ps -a
    docker rmi : remove specific image
    docker restart
    docker build -t _nom .
    docker container prune
    docker run --interactive --tty ubuntu bash
    docker stop _nom

    
On ne le dira jamais assez :

Do not use PowerShell ISE

Interactive terminals do not work in PowerShell ISE (but they do in PowerShell).
See docker/for-win/issues/223.

====================================================================================================
Créer une images
====================================================================================================
Dans un répertoire vierge créer un fichier nommer Dosckerfile

Lancer la commande docker build (éventuellement avec -t pour préciser un nom d'image)

Syntaxe des fichiers Dockerfile 
===========================================================

`Docker file ref`_

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

Docker dashboard : gestion interractive graphique des container/appli compose 
**en cours d'éxécution**


================================
Vocabullaire
================================
Statefull

Stateless

Images : 

    **Base images** are images that have no parent image, usually images with an OS like ubuntu, busybox or debian.

    **Child images** are images that build on base images and add additional functionality.

Then there are official and user images, which can be both base and child images.

    **Official images** are images that are officially maintained and supported by the folks at Docker. These are typically one word long. In the list of images above, the python, ubuntu, busybox and hello-world images are official images.

    **User images** are images created and shared by users like you and me. They build on base images and ad

=========
Weblinks
=========

.. target-notes::
