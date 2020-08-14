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

Définitions
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

Ma présentation rapide pratique
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

Quelques part c'est un peu frustrant au début. Exemple::

   docker run --interactive --tty ubuntu bash

On a alors un Ubuntu mais c'est une coquille vide. Les principales commandes n'y sont pas ! 
Il faut alors soit devenir un gourou des images du docker hub ou le roi des fichiers dockerfile

Après quelques temps je me rends compte que Docker c'est bien mais tout est éphémère !
Exemple ::

      docker run -it busybox sh
      puis on pass des commandes, on peut créer des fichier...
      exit
      et quand on revient il n'y a plus rien !
      Cela dit ce n'est pas un handicap, c'est même voulu mais c'est déroutant pour les novices

Grands principes
====================================================================================================

Tiré de `Docker Architecture dans la doc officielle`_

.. _`Docker Architecture dans la doc officielle` : https://docs.docker.com/get-started/overview/#docker-architecture

dockerd : docker deamon gère les images, container, réseaux et volumes

dockerapi : s'adresse à dockerd pour éxécuter les choses

dockercli ou docker client s'adresse à l'api qui s'adresse ...

docker registry : dépôt : docker hub est le registry par défaut mais on peut utiliser 
son propre registry

.. index::
    single: Docker;  layer

Les layers: chaque instructions d'un dockerfile constitue un layer, chaque layer sauf le tout
dernier est en read-only. Chaque nouveau layer est constitué d'un petit nombre de différences par 
rapport au précédent. Les layers sont empilés les uns au dessus des autres avec en plus au dessus
un layer dit container layer en lecture/écriture dans lequel sont fait les modifs.

La majeur différence en une images et un container est en fait représentée par ce dernier layer en
lecture écriture dont le contenu disparaît quand le container est arrêté.

Tiré de `Images and layers dans la doc officielle`_

.. _`Images and layers dans la doc officielle` : https://docs.docker.com/storage/storagedriver/#images-and-layers



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
Retour dans la doc officielle.
====================================================================================================

`Rappel du chemin vers la doc officielle`_

.. _`Rappel du chemin vers la doc officielle` : https://docs.docker.com/develop/ 


- Use multi-stage builds to keep your images lean : c'est déjà du Docker de haut vol !
- Manage application data using volumes and bind mounts
- Scale your app with Kubernetes
- Scale your app as a Swarm service
- General application development best practices

J'attaque le premier point mais c'est plus le deuxième qui m'intéresse

====================================================================================================
Commandes principales
====================================================================================================
Il y a des centaines de commandes docker (61 commandes principale en version 19.03).
Caractéristiques : elles commence toutes par docker.
Et même la plupart on des sous commandes. Au total, ça doit peut-être même faire des milliers avec
Chacune des dizaines d'options.

Voir sur `Note Docker Pierre`_ il y a tout ce qu'il faut !

Cheatsheet ?

::

    docker run -d -p 8080:80 nginx
    docker images <=> docker image ls
    docker ps : shows you all containers that are currently running
    docker ps -a : shows all containers
    docker rmi : efface une ou plusieurs images
    docker rm : efface un container
    docker start -i container_name
    docker restart
    docker build -t _nom .
    docker container prune <=> docker rm $(docker ps -a -q -f status=exited)
    docker run --interactive --tty ubuntu bash
    docker inspect container_name
    docker stop _nom
    docker volume create nomDuVolume
    docker volume ls
    docker volume inspect nomDuVolume
    docker create : comme run mais sans start

    
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
    
Il est bon aussi de bien lire : `Best practices for writing Dockerfiles`_ :

Mouais, *build through stdin* ou *Understand build context* sont plus des possibilités offertes 
qu'il faut connaître à mes yeux que des best practices. En revenche ensuite, 
`se trouve de vraies best practices`_

.. _`se trouve de vraies best practices` : https://docs.docker.com/develop/develop-images/dockerfile_best-practices/#dockerfile-instructions

comme : ne pas faire apt-get upgrade

Le build ne dispense pas de faire un run ensuite

.. _`Docker file ref` : https://docs.docker.com/engine/reference/builder/

.. _`Best practices for writing Dockerfiles` :  https://docs.docker.com/develop/develop-images/dockerfile_best-practices/

Les principale commandes::

    FROM
    RUN
    COPY / ADD
    WORKDIR
    EXPOSE
    VOLUME
    CMD

`Différence entre ADD et COPY`_

.. _`Différence entre ADD et COPY` : https://nickjanetakis.com/blog/docker-tip-2-the-difference-between-copy-and-add-in-a-dockerile


Un exercice
====================================================================================================

un ubuntu
installer nano 
copier un fichier texte
et se retrouver dans le prompt

Solution:

.. code:: cpp

   dockerfile
    FROM ubuntu

   RUN apt-get update -yq \
   && apt-get install nano -yq

   docker build -t mybuntu
   docker run -ti mybuntu

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
volumes et bind mounts
====================================================================================================
Ce sont 2 manières différentes d'avoir des données persistantes.

Les volumes sont mieux que les binds mounts::

  - Volumes are easier to back up or migrate than bind mounts.
  - You can manage volumes using Docker CLI commands or the Docker API.
  - Volumes work on both Linux and Windows containers.
  - Volumes can be more safely shared among multiple containers.
  - Volume drivers let you store volumes on remote hosts or cloud providers, to encrypt the 
    contents of volumes, or to add other functionality.
  - New volumes can have their content pre-populated by a container.

Les volumes sont indépendants de la structure du filesystem de la machine hôte. 
``When you use a bind mount, a file or directory on the host machine is mounted into a container.``

Il y a 2 syntaxes possibles --mount ou --volume (abrégeable en -v). La syntaxe --mount est plus 
simple

Les volumes sont stockés quelque part dans le système Docker mais on ne sait pas trop bien où.
Non, on pourrait préciser un répertoire dans la commande -v mais ce n'est pas claire dans la doc
C'est sous-entendu sur le site de `AJDAINI Hatim article sur les volumes`_

.. _`AJDAINI Hatim article sur les volumes` : https://devopssec.fr/article/fonctionnement-manipulation-volumes-docker

.. warning::

   Les options de syntaxe -v ou --mount peuvent aussi bien être utilisées pour monter un volume 
   que pour faire du bind mount

On peut soit créer un volume avec des commandes Docker docker volume create ou directement quand 
on lance un container avec l'option -v de la commande run

``when you use a volume, a new directory is created within Docker’s storage directory on the host 
machine, and Docker manages that directory’s contents.``

`Doc officielle sur les volumes`_ et `référence officielle des commandes docker volume`_

.. _`Doc officielle sur les volumes` : https://docs.docker.com/storage/volumes/ 

.. _`référence officielle des commandes docker volume` : https://docs.docker.com/engine/reference/commandline/volume/

.. warning::

   Fonctionne sous windows10: docker run -ti -v %cd%:/tmp mybuntu 
   (à condition d'être dans le bon répertoire)

La syntaxe powershell est différent ainsi que sous Linux 

`Syntaxe current dir sous Stackoverflow`_

.. _`Syntaxe current dir sous Stackoverflow` : https://stackoverflow.com/questions/41485217/mount-current-directory-as-a-volume-in-docker-on-windows-10

**Encore quelques informations tirées de la doc officielle sur les volumes:**

- Un volume peut être créé ou monté en read only, par plusieurs container en même temps.

- Les volumes drivers sont des plugin qui permettent de créer des volumes à l'extérieur du système
  Docker comme *vieux/sshfs plugin*

  `Doc sur les volumes drivers`_
  
  .. _`Doc sur les volumes drivers` : https://docs.docker.com/storage/volumes/#use-a-volume-driver 

====================================================================================================
Volume et sauvegarde
====================================================================================================

En parcourant la doc sur les volumes, après *start a container with volume*, je suis tombé sur :
*start a service with volumes* ! ? Qu'est-ce donc que cette histoire de service ? 
Voir `Docker services/Swarm`_

La sauvegarde :

En fait, l'idée est de monter un container avec un bind et un --volume-from un autre container nommé
et de faire un tar cvf du volume vers le bind !!

`Tout ceci expliqué dans la doc officielle`_

.. _`Tout ceci expliqué dans la doc officielle` : https://docs.docker.com/storage/volumes/#backup-a-container


Et pour la restauration, on procède de manière inverse.

====================================================================================================
Networks
====================================================================================================
`Doc officielle networking`_

.. _`Doc officielle networking` : https://docs.docker.com/network/

Tout d'abord, il faut savoir qu'il y a 5 type de driver de réseau dans Docker:


- **User-defined bridge** networks are best when you need multiple containers to communicate on 
  the same Docker host.
- **Host networks** are best when the network stack should not be isolated from the Docker host, 
  but you want other aspects of the container to be isolated.
- **Overlay networks** are best when you need containers running on different Docker hosts to 
  communicate, or when multiple applications work together using swarm services.
- **Macvlan networks** are best when you are migrating from a VM setup or need your containers 
  to look like physical hosts on your network, each with a unique MAC address.
- **Third-party network** plugins allow you to integrate Docker with specialized network stacks.

Pour mon usage, le driver par défaut semble suffisant. Les autres drivers sont surtout utile pour
des container fonctionnant sur des démon différents. Et surtout les user-define bridge apparemment.

Par défaut docker crée un bridge nommé bridge.

Il y a comme pour les volumes des commandes pour gérer les network::

   docker network ls
   docker network inspect avec un nom
   docker network create
   docker network connect et disconnect

`Doc officielle docker network bridge`_

.. _`Doc officielle docker network bridge` : https://docs.docker.com/network/bridge/

Et aussi `la référence de la ligne de commande docker network create`_

.. _`la référence de la ligne de commande docker network create` : https://docs.docker.com/engine/reference/commandline/network_create/


====================================================================================================
Docker services/Swarm
====================================================================================================
Notion de Swarm : Un Swarm est un groupe de machines exécutant le moteur Docker et faisant partie 
du même cluster. Docker swarm vous permet de lancer des commandes Docker auxquelles vous êtes 
habitué sur un cluster depuis une machine maître nommée manager/leader Swarm. Quand des machines 
rejoignent un Swarm, elles sont appelés nœuds.

`Page officielle de la documentation sur les service`_

.. _`Page officielle de la documentation sur les service` : https://docs.docker.com/engine/reference/commandline/service/


`Source ci-dessus sur devopssec.fr`_

.. _`Source ci-dessus sur devopssec.fr` : https://devopssec.fr/article/comprendre-gerer-manipuler-un-cluster-docker-swarm

====================================================================================================
General application development best practices
====================================================================================================

`Page officielle Docker development best practices`_

.. _`Page officielle Docker development best practices` : https://docs.docker.com/develop/dev-best-practices/

On this page::

    How to keep your images small
    Where and how to persist application data
    Use CI/CD for testing and deployment
    Differences in development and production environments

Il s'agit de règles de bon sens : commencer avec une image appropriée...

Un point intéressant dans la première partie *How to keep your images small* est ::

   To keep your production image lean but allow for debugging, consider using the production image as 
   the base image for the debug image. Additional testing or debugging tooling can be added on top 
   of the production image.

Dans la deuxième partie::

   Avoid storing application data in your container’s writable layer using storage drivers

Je ne savais même pas qu'on pouvait le faire !

One case where it is appropriate to use bind mounts is during development.
For production, use a volume instead,


====================================================================================================
Accéder aux données cachées de Docker sous Windows y compris les volumes
====================================================================================================

.. hint::

   If you have linux containers on a Windows 10 machine, containers are stored in 
   the MobyLinuxVM.vhdx file. You can't mount or explore that file AFAIK, but you can still list
   the containers inside that machine using this 'blue pill' trick
   blog.jongallant.com/2017/11/ssh-into-docker-vm-windows by default containers are stored 
   in the linux path /var/lib/docker in that virtual machine (you can confirm that linux path 
   from a docker info command)

Et effectivement j'ai testé::

   docker run --privileged -it -v /var/run/docker.sock:/var/run/docker.sock jongallant/ubuntu-docker-client 


On se retrouve alors dans un container (option -it) où on lance un deuxième container::

   docker run --net=host --ipc=host --uts=host --pid=host -it --security-opt=seccomp=unconfined --privileged --rm -v /:/host alpine /bin/sh

On a alors un prompt et on peut y taper chroot /host... Nouveau prompt mais d'aspect identique au 
précédent (seul un ls peut révéler qu'on a changé d'endroit).

Dans cet endroit un ls à la racine donne des choses bizarre ! Mais ce qui importe c'est ce qui
se trouve dans le dossier /var/lib/docker

La cession complète::

   docker run --privileged -it -v /var/run/docker.sock:/var/run/docker.sock jongallant/ubuntu-docker-client
   root@693563b5330f:/# ls
   bin  boot  dev  etc  home  lib  lib64  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
   root@693563b5330f:/# docker run --net=host --ipc=host --uts=host --pid=host -it --security-opt=seccomp=unconfined --privileged --rm -v /:/host alpine /bin/sh
   / # ls
   bin    dev    etc    home   host   lib    media  mnt    opt    proc   root   run    sbin   srv    sys    tmp    usr    var
   / # chroot /host
   / # pwd
   /
   / # ls
   A  C  E  G  I  K  M  O  Q  S  U  W  Y  a  bin  d    e    f  h     host_mnt  j  l    m      mnt  o    p     q  root  s     sendtohost  sys  tmp  usr  var  x  z
   B  D  F  H  J  L  N  P  R  T  V  X  Z  b  c    dev  etc  g  home  i         k  lib  media  n    opt  proc  r  run   sbin  srv         t    u    v    w    y
   / # cd /var/lib/docker
   /var/lib/docker # ls
   builder  buildkit  containerd  containers  image  network  overlay2  plugins  runtimes  swarm  tmp  trust  volumes

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

Docker port
====================================================================================================
Dans docker port container_name
L'affichage produit est ::

    container --> localhost:port

Alors que dans::

    docker run -p 8888:80 site

On a d'abord le port de l'hôte suivi du port de l'image !


Faire du python2 sans l'installer
====================================================================================================

::

    docker run -i -t python:2

docker run, start and restart
====================================================================================================
run créé un nouveau container avec un nouveau top layer vierge.

start permet de relancer un container arrêté sans perdre les données temporaire

restart fair un stop puis un start !

Savoir si une image a été montée avec un volume ou un bind
====================================================================================================
docker inspect container_name

Docker run --name --rm
====================================================================================================
Tout est dans le titre, on peut donner un titre à container ! ne s'abrège pas.

--rm le supprime quand on sort, très pratique pour les tests de la commande run elle-même


.. index::
    single: Docker; Samples

====================================================================================================
Voir Docker à l'oeuvre
====================================================================================================
L'`exemple de prakhar1989 catnip`_ dont le fichier dockerfile est accessible sous github.

.. _`exemple de prakhar1989 catnip` : https://hub.docker.com/r/prakhar1989/catnip

`Docker sample home`_

.. _`Docker sample home` : https://docs.docker.com/samples/

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

Swarm mode

=========
Weblinks
=========

.. target-notes::
