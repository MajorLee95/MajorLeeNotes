++++++++++++++++++++++++++++++++
Réseaux et Internet
++++++++++++++++++++++++++++++++

:Auteur: J.Soranzo
:Date: Février 2020 2019
:Societe: VoLAB
:Entity: VoRoBoTics

.. contents::
    :backlinks: top
    
    
.. index::
    single: OVH; Redirection
    
================================
OVH rediection
================================
Cela se passe dans l'onglet Redirection du domaine concerné

.. image:: images/ongletsovh.jpg
   :width: 300 px

Ne pas oublier de cocher la case mettre à jour aussi www.

Comme il est dit cela ajoute également une entrée dans l'onglet ZoneDNS.

La mise à jour peut prendre jusqu'à 72h.

====================================================================================================
Développement web en 2020
====================================================================================================

Vue d'ensemble

La question est simple : que signifie développer une appli web en 2020?

Ou encore qu'est que le web développement de nos jours ?

J'entends parler de REACT, FLASK, DJANGO, Bootstrap qu'est-ce que c'est que tout ce merdié !

Visiblement et aussi étonnant que cela puisse paraître le net n'est pas d'un très grand secours 
pour répondre à cette qustion en français du moins.

En anglais sur `wikipédia Web developpement`_

.. _`wikipédia Web developpement` :  https://en.wikipedia.org/wiki/Web_development

D'après cette page, il s'agit de développer un site internet ou intranet, jusque là rien de neuf !
Depuis la simple page statique de texte jusqu'aux applications internet web complexes, on est dans
le vif du sujet ! Cette page cite à titre d'exemples : e-Business, e-commerce, réseau sociaux.

On apprend que cela fait intervenir un certain nombre de tâches comme:

- web engineering,
- web design,
- web content development,
- client liaison,
- client-side/server-side scripting,
- web server,
- network security configuration,
- e-commerce development.

Toutefois cela fait plus référence à l'aspect web dev que web design.

Les termes que je retiens : writing markup (html)and coding ainsi que  front-end developer, back-end 
developer, and full-stack developer et que cela peut passer par l'utilisation de CMS.

Une idée plutôt majeur qui ressort de nos jours est que de plus en plus d'applications informatiques
au sens large ont de plus en plus souvent leur interface homme machine fournie sous la forme de code
accessible via un navigateur WEB. Dès lors que le moteur de ces applications tourne sur une bécane
accesible au travers d'un réseau et qu'on l'interroge, la pilote depuis une autre machine, on peut
parle d'appli web. Or la demande de qualité de ces interfaces homme-machine IHM, en terme d'estétique
de réactivité est de plus en plus exigente c'est pourquoi il convient de s'aider de librairies qui
ont pris de part leurs complexités et leurs fonctionnalités respectives des tailles parfois
gigantesques.

On ne parle alors plus de librairies mais de frameworks.

Mais il ne faut pas oublier que derrière ces libairies, il y a toujours un langage informatique
comme Python, java, javscript, Perl, C++

Parmis les modules auquels répondent ces Frameworks, on peut retenir:

- des modèles d'IHM,
- des gestionnaires de sessions (avec toute la partie de gestion des droits d'accès)
- des interface pour les base de données (car oui souvent ces appli s'appuies sur des BdD),
- gestionnaires de transactions commerciales...

Un peu de termes en anglais, parmis ces fonctionnalités rencontrées:

- Web template system
- Caching
- Security
- Database access, mapping and configuration
- URL mapping
- AJAX
- Web services
- Web resources

Wikipedia nous présnte un comparatif de ces frameworks.

`Comparatif Frameworks sur wikipédia`_

.. _`Comparatif Frameworks sur wikipédia` : https://en.wikipedia.org/wiki/Comparison_of_web_frameworks

Et c'est là qu'on trouve les REACT, FLASK, BOOTSTRAP et autre JANGO...

----------------------------------------------------------------------------------------------------

.. index::
    single: Apache

====================================================================================================
APACHE
====================================================================================================

`Page officielle version courante`_

.. _`Page officielle version courante` : http://httpd.apache.org/docs/current/

Ces commandes ne focntionnent pas sur le serveur Proliant::

    apachectl  start : Démarrer
    apachectl  restart : Relancer
    apachectl status : Voir son état

Ce qui marche pour moi::

    systemctl status apache2
    apache2ctl -t -D DUMP_VHOSTS : vérifie les hôts déclarés

Fichiers importants::

    /etc/apach2/apache2.conf : fonctionne avec des includes des autres fichiers
    /etc/apach2/ports.conf
    /etc/apache2/sites-available/*.conf : un par site
    /etc/apache2/sites-enabled/ liens symboliques créés par a2ensite, a2dissite


Héberger plusieurs site sur plusieurs machines derrière la même IP avec APACHE2
====================================================================================================
Typiquement derrière une box internet (Livebox, Freebox en consor...) 2 serveurs hébergeant chacun
un ou plusieurs site intrenet.

Pour le cas d'une machine unique hébergeant plusieurs sites, cela se résoud avec des Virtual Host 

  

  


Site par défaut
====================================================================================================
Apache2 traite les fichiers par ordre alphabétique.
d'où le 000-default.cong ;-)

Pour savoir quel site est celui par défaut : apache2ctl -S

Cette commande liste tous les serveurs avec en plus une lige qui dit::

    default server...

Configuration
====================================================================================================
voir la page par défaut d'un site après l'installation::

    Configuration Overview

    Debian's Apache2 default configuration is different from the upstream default configuration, and
    split into several files optimized for interaction with Debian tools. The configuration system 
    is fully documented in /usr/share/doc/apache2/README.Debian.gz. Refer to this for the full 
    documentation. Documentation for the web server itself can be found by accessing the manual 
    if the apache2-doc package was installed on this server.

    The configuration layout for an Apache2 web server installation on Debian systems is as follows:

    /etc/apache2/
    |-- apache2.conf
    |       `--  ports.conf
    |-- mods-enabled
    |       |-- *.load
    |       `-- *.conf
    |-- conf-enabled
    |       `-- *.conf
    |-- sites-enabled
    |       `-- *.conf
              

        apache2.conf is the main configuration file. It puts the pieces together by including all 
        remaining configuration files when starting up the web server.
        ports.conf is always included from the main configuration file. It is used to determine the
        listening ports for incoming connections, and this file can be customized anytime.
        Configuration files in the mods-enabled/, conf-enabled/ and sites-enabled/ directories 
        contain particular configuration snippets which manage modules, global configuration 
        fragments, or virtual host configurations, respectively.
        They are activated by symlinking available configuration files from their respective 
        *-available/ counterparts. These should be managed by using our helpers a2enmod, 
        a2dismod, a2ensite, a2dissite, and a2enconf, a2disconf . See their respective man pages 
        for detailed information.
        The binary is called apache2. Due to the use of environment variables, in the default 
        configuration, apache2 needs to be started/stopped with /etc/init.d/apache2 or apache2ctl.
        Calling /usr/bin/apache2 directly will not work with the default configuration.

    Document Roots

    By default, Debian does not allow access through the web browser to any file apart of those 
    located in /var/www, public_html directories (when enabled) and /usr/share (for web 
    applications). If your site is using a web document root located elsewhere (such as in /srv) 
    you may need to whitelist your document root directory in /etc/apache2/apache2.conf.

    The default Debian document root is /var/www/html. You can make your own virtual hosts under
    /var/www. This is different to previous releases which provides better security out of the box.
    
Il semblerait que ci-dessus on ait oublié le fichier ports.conf. Ah non j'avais pas vu.

====================================================================================================
LINUX : monter un répertoire d'une autre machine
====================================================================================================
Cela pourait être utile à la place du mécanisme de mandat APACHE

`LINUX Partage de répertoire`_


----------------------------------------------------------------------------------------------------

.. index::
    single: DynDNS

====================================================================================================
Cients dynDNS
====================================================================================================
Possible de faire un `dynDNS chez OVH`_

.. _`dynDNS chez OVH` : https://docs.ovh.com/gb/en/domains/hosting_dynhost/

Une des conditions pour que cela fonctionne est d'avoir un client sur sa machine mais ovh ne fournis
 pas de référence !
 
.. code::

    apt install ddclient
    Mais attention il demande toutes les infos y compris le protocole utilisé.
    
Page concernant l'`intall de ddclient`_

.. _`intall de ddclient` : https://perhonen.fr/blog/2016/03/dynhost-dyndns-de-chez-ovh-2446

====================================================================================================
Weblinks
====================================================================================================


.. target-notes::

