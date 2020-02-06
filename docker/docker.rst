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

================================
Notes
================================
Par principe Docker ne doit faire tourner qu'un seul processus.

Ainsi, dans le cas d'une stack LAMP (Linux, Apache, MySQL, PHP), nous devons créer 3 conteneurs 
différents, un pour Apache, un pour MySQL et un dernier pour PHP.

Stateful et Stateless

Immutable

Ce que c'est ::

	Docker is a platform for developers and sysadmins to build, share, and run applications.
	
ça c'est la `définition officielle`_ . Cela ne dit pas développer de quelles applications. Le gros sous 
entendu c'est que ce sont des applications plutôt à forte propention WEB.

.. _`définition officielle` : https://docs.docker.com/get-started/

================================
Commandes principales
================================

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
	

=========
Weblinks
=========

.. target-notes::
