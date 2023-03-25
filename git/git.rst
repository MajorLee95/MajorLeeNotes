++++++++++++++++++++++++++++++++
Notes sur git
++++++++++++++++++++++++++++++++
.. image:: images/gitLogo.png
   :height: 100px
   :alt: git logo
   :align: left


.. |clearer|  raw:: html

    <div class="clearer"></div>    
   
:Auteur: J.Soranzo
:Date de création: Novembre 2019
:mise à jour: 08/12/2021
:Societe: VoRoBoTics
:Entity: VoLAB

.. index::
    single: git



|clearer|

.. contents::
    :backlinks: top

====================================================================================================
Introduction
====================================================================================================
penser au fichier xmind : ProcessusDocumentaire.mm  Freeplane

A mon avis, git prend tout son sens quand on l'utilise avec un dépôt distant. J'ai longtemps utilisé
git en faisant uniquement des dépôts git locaux. Jusqu'au jour où mon disque dur a crashé et que je 
n'avais pas de sauvegarde... Tous ces précieux commit qui se sont envolés...

Ce dépôt distant peut être:

- un dépôt sur github.com ou sur gitlab.com

.. HINT::

    `Comparaison Github Gitlab`_
    
.. _`Comparaison Github Gitlab` : https://www.ionos.fr/digitalguide/sites-internet/developpement-web/gitlab-vs-github/


====================================================================================================
Github config ssh
====================================================================================================
Ceci n'est pas vraiment du git mais faute de mieux...

Comment configure git pour s'authentifier avec des clé ssh ?

- Mettre la clé publique dans son compte github
- mettre sa clé privée dans le dépôt des clé local de sa machine ``C:\Users\user_name\.ssh``
- configurer le dépôt local avec de la forme : ``remote.origin.url=git@github.com:nom_utilisateur_github/nom_du_depot.git``
- configurer le ssh client (avec tortoisegit rubrique network en cli pas trouvé)

====================================================================================================
Commandes de base (ou kit de survie minimum)
====================================================================================================
::

    git help (-a: liste toute les commande, -g : liste des concepts)
        exemple : git help everyday (donne de l'aide sur l'utilisation de git tous les jours )
    git clone/init
    git status
    git log
    git log -p -1 (détails et limité au dernier -2 les 2 derniers...)
    git log --name-only --abbrev-commit -1
    
    git branch ou git branch -a (--all) -vv y compris les branche non trackées
    git add .
    git commit --message 'commit explication' --all
    git show
    git merge

====================================================================================================
Tutos en français
====================================================================================================
`Découvrir Git : introduction et premiers pas`_

.. _`Découvrir Git : introduction et premiers pas` : https://www.miximum.fr/blog/decouvrir-git/

====================================================================================================
Git FAQ
====================================================================================================

`FAQ Git : retrouvez les meilleures réponses à vos questions pour apprendre Git, de niveau débutant à expert`_

.. _`FAQ Git : retrouvez les meilleures réponses à vos questions pour apprendre Git, de niveau débutant à expert` : https://alm.developpez.com/faq/git/


====================================================================================================
Workflow
====================================================================================================
Développeur (en équipe)
----------------------------------------------------------------------------------------------------

En équipe peut aussi signifier, développer seul mais sur plusieurs machines différentes.
Une des grosse difficultés que je rencontre c'est de répondre à la question ?

Où on en est ? Ensuite ça roule...

Partons du postulat dans lequel on a un répertoire local de travail avec un sous répertoire .git

Ce petit indice nous dit qu'il s'agit d'un dépôt git local. 

- Question comment savoir dans quel état il se trouve ? 
- Est-il connecté à un dépôt distant ?
- Combien comporte-t-il de branche ? locales et éventuellement distante
- Quelles sont les branches suivies ?
- Quel est l'éventuel état de la synchronisation ? 



commandes::

    git status
    git branch -a
    git log --pretty=oneline --abbrev-commit --graph --decorate --all [>graph.txt]
    git tag -l
    git config --local -l



**Astuce**::

    - git config --global alias.adog "log --all --decorate --oneline --graph"
    - puis git adog 


.. index::
    pair: Git; Comit atomique

====================================================================================================
Commits atomiques
====================================================================================================
Article très intéressant `Commits atomiques - la bonne approche`_ sur adopteungit.fr

.. _`Commits atomiques - la bonne approche` : http://adopteungit.fr/methodologie/2017/04/26/commits-atomiques-la-bonne-approche.html

Le site ne répond plus (le 07/10/2021) mais il est dispo sur `github lgiraudel adopteungit`_

.. _`github lgiraudel adopteungit` : https://github.com/lgiraudel/adopteungit

code::

	git add --patch ...
    résister à git add --all

On y apprend d'abord comment faire de tout petits commit et surtout comment committer dans un fichier
seulement ce qu'on veut pour que le commentaire du commit corresponde bien au commit.

Les petites modifs de droite et de gauche...

Mais on y apprend également comment réorganiser ces tout petits commits.


====================================================================================================
git rebase
====================================================================================================
`Git rebase : qu'est-ce que c'est ? Comment s'en servir ?`_

.. _`Git rebase : qu'est-ce que c'est ? Comment s'en servir ?` : https://www.miximum.fr/blog/git-rebase/




- conserver un historique propre ;
- corriger des erreurs de fusion ;
- faciliter le travail collaboratif ;
- faciliter les fusions sur les branches qui nécessitent un très long développement.

*La commande git-rebase est comme une tronçonneuse : elle permet de couper une branche pour 
la regreffer à un autre endroit sur l'arbre.*

Pourquoi rebase ? Parce qu'on part du principe qu'on a basé notre branche de travail sur un commit
d'une autre branche et qu'entre temps cette branche a évolué et que avant de pousser un nouveau commit
sur notre branche distance, on change la base de notre branche pour l'emmener à la tête de la branche 
qui nous a servit de point de départ. Il y a alors un pull sous jascent qui se fait (avec éventuellement 
résolution de conflit). Le merge alors de notre branche sur la branche de base s'en trouve alors facilité.
Les conflits ont alors déjà été résolus.

.. WARNING:: Ne pas rebaser l'historique public
   :class: without-title


source : `Atlassian.com Git-rebase en français`_

.. _`Atlassian.com Git-rebase en français` : https://www.atlassian.com/fr/git/tutorials/rewriting-history/git-rebase

Règle d'or: L'historique partagé jamais tu ne rebaseras
----------------------------------------------------------------------------------------------------

.. WARNING:: Tant que vous rebasez vos petites branches en local, tout va bien. Mais attention, 
    :class: without-title

    si vous rebasez une branche qui se trouve déjà sur le serveur, c'est la catastrophe.

`Git rebase : qu'est-ce que c'est ? Comment s'en servir ?`_ §L'historique partagé jamais tu ne rebaseras

dit autrement:

.. WARNING:: N'utilisez jamais la commande git rebase sur les branches publiques. C'est la règle d'or !
   :class: without-title



Article connexe : Réécrire l'historique sur Atlassian
----------------------------------------------------------------------------------------------------
`Réécrire l'historique`_

.. _`Réécrire l'historique` : https://www.atlassian.com/fr/git/tutorials/rewriting-history

Il y a cette phrase dans le §Ne pas modifier les commits publics::

    Évitez de modifier un commit sur lequel repose le travail d'autres développeurs.

Même si ce n'est pas en apparence pas le cas. En effet, dès qu'un commit se trouve sur un dépôt distant
on ne peut pas savoir si une branche n'a pas été tirée d'un commit sur un dépôt local...

====================================================================================================
git bisec
====================================================================================================
`La chasse aux bugs avec git bisect`_

.. _`La chasse aux bugs avec git bisect` : http://adopteungit.fr/commande/bisect/2016/09/04/la-chasse-aux-bugs-avec-git-bisect.html

====================================================================================================
Gérer les dépôts immenses...
====================================================================================================
.. IMPORTANT::

    how to manage a project with source code, electronic schematic and source documentation ?

Un article : `How to handle big repositories with Git`_

.. _`How to handle big repositories with Git` : https://www.atlassian.com/git/tutorials/big-repositories

Un autre article un peu moins intéressant au niveau solution (moins riche) : 
`Best practices for using git in large project`_

.. _`Best practices for using git in large project` : https://stackoverflow.com/questions/32068654/best-practices-for-using-git-in-large-project

Créer un dépôt serveur
----------------------------------------------------------------------------------------------------
git init --bare --share tout simplement

Petite subtilité au moment du clone : on peut cloner vers un sous répertoire dont le nom est
différent de celui de la source.

====================================================================================================
branches orphelines
====================================================================================================

Pourquoi créer des branches orphelines ?

- vous souhaitez avoir une branche dédiée pour votre documentation.

- vous souhaitez recommencer un projet dans une nouvelle technologie.

- vous souhaitez fusionner deux repositories qui n’ont pas le même historique.

::

    git checkout --orphan nom_de_la_branche

================================
petits trucs utiles 
================================
Mettre un projet déjà bien avancé sous GitHUB
----------------------------------------------------------------------------------------------------
Situation : j'ai un dossier projet déjà bien avancé et je souhaite le mettre sous github. Procédure:

- tout d'abord en local, aller dans le dossier du projet
- faire clic droit git bash here
- git init
- mettre en place .gitignore
- git add .
- git commit -m "premier commit"

https://www.fxparlant.net/github-ajouter-un-projet-deja-cree/


Créer une branche et s'y déplacer en une seule commande
----------------------------------------------------------------------------------------------------
::

    git checkout -b novelle_branch


Logiciels 
----------------------------------------------------------------------------------------------------

`gitKraken`_

.. _`gitKraken` : https://www.gitkraken.com/

Nécessite de créer un compte sur leur site ? Pourquoi au juste ?

`tortoisegit`_

 - dl dans outils/conception       
 - Ajoute un menu contextuel
			avec plein de commandes
            
.. _`tortoisegit` : https://tortoisegit.org/

Configurer Tortoise git avec des clé ssh:

- mettre ses clés dans ~/.ssh
- dans les setting du dépot remplacer htt:// par git@ avec : au lieu du premier /
- configurer également network/ssh client : ``C:\Windows\System32\OpenSSH\ssh.exe``
         
Suppression d'un fichier 
----------------------------------------------------------------------------------------------------
git rm
        
lister les fichiers indexé 
----------------------------------------------------------------------------------------------------
A priori git ls-files

Fichiers pas suivis git ls-files -o, sous-entendu --others (au pluriel)

Mais vers ou pointe origine 
----------------------------------------------------------------------------------------------------
 - git ls-remote
 - git remote show origin !!!
        
merger un seul fichier 
----------------------------------------------------------------------------------------------------
 - git fetch : récupère les branche distantes
 - git checkout La_branche contenant le fichier
 - git pull
 - retour sur la branche de travail
 - git checkout BRANCH FILE
    * BRANCH : le nom de la branche
    * FILE : chemin d'accès au fichier
            
exemple data/index.html ?

Je me suis mis dans le dossier en question et je n'ai donné que le nom du fichier et cela fonctionne
sous-entendu sans le chemin complet.
                
Écraser les dernière modif qui n'ont pas été commitées 
----------------------------------------------------------------------------------------------------
 - git checkout -- <file> (comme le signal la commande git status)
 - git reset --hard HEAD~1 (retour au dernier commit)
 - git rebase -i HEAD~10
 
 A propos de git reset --hard HEAD~1::
 
    When using git reset --hard HEAD~1 you will lose all uncommitted changes in addition to the 
    changes introduced in the last commit. The changes won't stay in your working tree so doing 
    a git status command will tell you that you don't have any changes in your repository.
    Tread carefully with this one. If you accidentally remove uncommitted changes which were never 
    tracked by git (speak: committed or at least added to the index), you have no way of getting 
    them back using git.

Retirer un répertoire de l'index  
----------------------------------------------------------------------------------------------------
Pour qu'il soit pris en compte par le git ignore::

    git rm --cached -r build
    
A condition de faire le add avant

Puis de les retirer après de l'index

lister les fichier dossier ignorés ? 
----------------------------------------------------------------------------------------------------
git ls-files --others -i --exclude-standard::
            
		git ls-files --stage
        
attention dans .gitignore un répertoire se termine par / et pas \
        
Rattacher la tête 
----------------------------------------------------------------------------------------------------
Procédure::

    git checkout -b temp
    git branch -f master temp
    git checkout master
    git branch -d temp
        
      
        
Annuler le dernier commit 
----------------------------------------------------------------------------------------------------
    
Situation :
- des fichiers modifiés
- un fichier ajouté

Commandes::

    git add fichierajouté
    git commit -m "texte"
    
- ne commit que le nouveau fichier
- la bonne commande eut été git commit -am "texte"
- ou avant git add --all
        
Besoin: supprimer ce commit pour le refaire avec l'option -am

.. WARNING::  

    Surtout pas git reset --hard HEAD, écrase toutes les modifs
    Cette commande permet de revenir à l'état du dernier commit (ne pas confondre)

Autres possibilités::

    git revert
    ou git add . suivi d'un git commit --amend
        
        
        
Lister les commit d'une branche distante 
----------------------------------------------------------------------------------------------------
- Utile quand on est out of date
- git remote show origin
- git ls-remote

Dépôt git sur clé usb 
----------------------------------------------------------------------------------------------------

Créer `un dépôt git sur une clé usb, sur wikibook`_

.. _`un dépôt git sur une clé usb, sur wikibook` : https://en.wikibooks.org/wiki/Git/Repository_on_a_USB_stick


Trace l'arborescence sous forme textuelle
----------------------------------------------------------------------------------------------------
une ch'tite commande sympa::

	git log --pretty=oneline --abbrev-commit --graph --decorate
    voir aussi git adog en début de chapitre
    
clé SSH
----------------------------------------------------------------------------------------------------

- visiblement dépendante de l'ordinateur non ?
- Au tout au moins réside dans un répertoire locale de la machine
- Comment les entrées dans un nouvel environnement ?

`Article intéressant sur W3C clé ssh`_

.. _`Article intéressant sur W3C clé ssh` : https://fr.w3docs.com/snippets/git/comment-generer-une-cle-ssh-pour-git.html

.. code::

	 ls -al ~/.ssh

Généralement OpenSSH installé par défaut sous Ubuntu.

Sous Windows::

    ssh-add : error
    ssh-agent error 1058 : service est mis sur disable dans Windows, le passer sur manuel !


cherry-pick : écrémer
----------------------------------------------------------------------------------------------------

Lister les différences entre branches locale et branche distante
----------------------------------------------------------------------------------------------------
::

    git diff maBranche origin/branche
        ne se connecte pas au serveur en réalité
        fait la diff par rapport au copies locale
    avant faire un git fetch

git push
----------------------------------------------------------------------------------------------------

::

    Situation
        git local
        je veux le mettre sous github
        adding-an-existing-project-to-github-using-the-command-line/
        git push --all
            from official ref
            Push all branches (i.e. refs under refs/heads/); cannot be used with other <refspec>.

supprimer une branche distante
----------------------------------------------------------------------------------------------------
git push origin : <nombrancheasupprimer>

le 17/10/2020 : git push origin +HEAD

Gros pb

git rebase -i HEAD~11
(vi) drop versus pick

:wq

git push origin HEAD:gh-pages --force

Supprimer une branche locale
----------------------------------------------------------------------------------------------------
git branch --help

git branch -d ou --delete (si pas pushée enfin je crois !)

Merge branche distante
----------------------------------------------------------------------------------------------------
git pull non !

Traquer une nouvelle branche distante
----------------------------------------------------------------------------------------------------

::

	le 31/03
        avec tortoise
        on commence par un git fetch origin pour mettre à jour la base locale
        puis un checkout de la branche distante => créé une branche locale. et c'est suffisant !

    git branch -- track <branch> <branche_distante> (7/6/21: j'ignore ?)
    ou plus simplement git checkout --track origin/branche_distante (si elle n'est pas traquée une nouvelle 
    branche locale est crée)

Reconnecter une branche distante à une branche locale
----------------------------------------------------------------------------------------------------
::

    git branch --set-upstream-to=origin/master master


créer un dépôt distant sur le serveur du VoLAB
----------------------------------------------------------------------------------------------------
::

    git init --bare chemin
        attention dans la ligne de commande remplacer tous les \ par des /
        sur le serveur
		le -- bare sur le serveur est mandatory sinon on se fait tej au moment du push
		on ne sairait une fois pusher sur un rep avec un working dir ça se fait pas alley un
    en local
        soit changer origin si c'est un dépot existant

Errors : git cannot lock ref d'une branche distante lors d'un pull
----------------------------------------------------------------------------------------------------
Le fichier dans l'arbo git était corrompu !

lister les fichiers d'une branche
----------------------------------------------------------------------------------------------------
::

    git ls-tree nom_de_la_branche -r (recursiv)

nettoyage des liens pourri
----------------------------------------------------------------------------------------------------

git fetch --prune
    
merge d'un répertoire d'une autre branche
----------------------------------------------------------------------------------------------------
    git checkout branch chemin

Déplacer le dernier commit d'une branche vers une autre branche
----------------------------------------------------------------------------------------------------

::

    git checkout l'autre branche
    git merge la branche où se trouve le commit fautif
    git checkout la branche du commit fautif
    git reset --hard HEAD~1



====================================================================================================
Exemple de la commande git help everyday
====================================================================================================
::

    GITEVERYDAY(7)                                                                Git Manual                                                               GITEVERYDAY(7)

    NAME
        giteveryday - A useful minimum set of commands for Everyday Git

    SYNOPSIS
        Everyday Git With 20 Commands Or So

    DESCRIPTION
        Git users can broadly be grouped into four categories for the purposes of describing here a small set of useful command for everyday Git.
        ·   Individual Developer (Standalone) commands are essential for anybody who makes a commit, even for somebody who works alone.
        ·   If you work with other people, you will need commands listed in the Individual Developer (Participant) section as well.
        ·   People who play the Integrator role need to learn some more commands in addition to the above.
        ·   Repository Administration commands are for system administrators who are responsible for the care and feeding of Git repositories.

    INDIVIDUAL DEVELOPER (STANDALONE)
        A standalone individual developer does not exchange patches with other people, and works alone in a single repository, using the following commands.

        ·   git-init(1) to create a new repository.
        ·   git-log(1) to see what happened.
        ·   git-checkout(1) and git-branch(1) to switch branches.
        ·   git-add(1) to manage the index file.
        ·   git-diff(1) and git-status(1) to see what you are in the middle of doing.
        ·   git-commit(1) to advance the current branch.
        ·   git-reset(1) and git-checkout(1) (with pathname parameters) to undo changes.
        ·   git-merge(1) to merge between local branches.
        ·   git-rebase(1) to maintain topic branches.
        ·   git-tag(1) to mark a known point.

    Examples
        Use a tarball as a starting point for a new repository.

                $ tar zxf frotz.tar.gz
                $ cd frotz
                $ git init
                $ git add . (1)
                $ git commit -m "import of frotz source tree."
                $ git tag v2.43 (2)

            1. add everything under the current directory.
            2. make a lightweight, unannotated tag.

        Create a topic branch and develop.

                $ git checkout -b alsa-audio (1)
                $ edit/compile/test
                $ git checkout -- curses/ux_audio_oss.c (2)
                $ git add curses/ux_audio_alsa.c (3)
                $ edit/compile/test
                $ git diff HEAD (4)
                $ git commit -a -s (5)
                $ edit/compile/test
                $ git diff HEAD^ (6)
                $ git commit -a --amend (7)
                $ git checkout master (8)
                $ git merge alsa-audio (9)
                $ git log --since='3 days ago' (10)
                $ git log v2.43.. curses/ (11)

            1. create a new topic branch.
            2. revert your botched changes in curses/ux_audio_oss.c.
            3. you need to tell Git if you added a new file; removal and modification will be caught if you do git commit -a later.
            4. to see what changes you are committing.
            5. commit everything, as you have tested, with your sign-off.
            6. look at all your changes including the previous commit.
            7. amend the previous commit, adding all your new changes, using your original message.
            8. switch to the master branch.
            9. merge a topic branch into your master branch.
            10. review commit logs; other forms to limit output can be combined and include -10 (to show up to 10 commits), --until=2005-12-10, etc.
            11. view only the changes that touch what’s in curses/ directory, since v2.43 tag.

    INDIVIDUAL DEVELOPER (PARTICIPANT)
        A developer working as a participant in a group project needs to learn how to communicate with others, and uses these commands in addition to the ones needed
        by a standalone developer.

        ·   git-clone(1) from the upstream to prime your local repository.
        ·   git-pull(1) and git-fetch(1) from "origin" to keep up-to-date with the upstream.
        ·   git-push(1) to shared repository, if you adopt CVS style shared repository workflow.
        ·   git-format-patch(1) to prepare e-mail submission, if you adopt Linux kernel-style public forum workflow.
        ·   git-send-email(1) to send your e-mail submission without corruption by your MUA.
        ·   git-request-pull(1) to create a summary of changes for your upstream to pull.

    Examples
        Clone the upstream and work on it. Feed changes to upstream.

                $ git clone git://git.kernel.org/pub/scm/.../torvalds/linux-2.6 my2.6
                $ cd my2.6
                $ git checkout -b mine master (1)
                $ edit/compile/test; git commit -a -s (2)
                $ git format-patch master (3)
                $ git send-email --to="person <email@example.com>" 00*.patch (4)
                $ git checkout master (5)
                $ git pull (6)
                $ git log -p ORIG_HEAD.. arch/i386 include/asm-i386 (7)
                $ git ls-remote --heads http://git.kernel.org/.../jgarzik/libata-dev.git (8)
                $ git pull git://git.kernel.org/pub/.../jgarzik/libata-dev.git ALL (9)
                $ git reset --hard ORIG_HEAD (10)
                $ git gc (11)

            1. checkout a new branch mine from master.
            2. repeat as needed.
            3. extract patches from your branch, relative to master,
            4. and email them.
            5. return to master, ready to see what’s new
            6. git pull fetches from origin by default and merges into the current branch.
            7. immediately after pulling, look at the changes done upstream since last time we checked, only in the area we are interested in.
            8. check the branch names in an external repository (if not known).
            9. fetch from a specific branch ALL from a specific repository and merge it.
            10. revert the pull.
            11. garbage collect leftover objects from reverted pull.

        Push into another repository.

                satellite$ git clone mothership:frotz frotz (1)
                satellite$ cd frotz
                satellite$ git config --get-regexp '^(remote|branch)\.' (2)
                remote.origin.url mothership:frotz
                remote.origin.fetch refs/heads/*:refs/remotes/origin/*
                branch.master.remote origin
                branch.master.merge refs/heads/master
                satellite$ git config remote.origin.push \
                            +refs/heads/*:refs/remotes/satellite/* (3)
                satellite$ edit/compile/test/commit
                satellite$ git push origin (4)

                mothership$ cd frotz
                mothership$ git checkout master
                mothership$ git merge satellite/master (5)

            1. mothership machine has a frotz repository under your home directory; clone from it to start a repository on the satellite machine.
            2. clone sets these configuration variables by default. It arranges git pull to fetch and store the branches of mothership machine to local
            remotes/origin/* remote-tracking branches.
            1. arrange git push to push all local branches to their corresponding branch of the mothership machine.
            2. push will stash all our work away on remotes/satellite/* remote-tracking branches on the mothership machine. You could use this as a back-up method.
            Likewise, you can pretend that mothership "fetched" from you (useful when access is one sided).
            1. on mothership machine, merge the work done on the satellite machine into the master branch.

        Branch off of a specific tag.

                $ git checkout -b private2.6.14 v2.6.14 (1)
                $ edit/compile/test; git commit -a
                $ git checkout master
                $ git cherry-pick v2.6.14..private2.6.14 (2)

            1. create a private branch based on a well known (but somewhat behind) tag.
            2. forward port all changes in private2.6.14 branch to master branch without a formal "merging". Or longhand

            git format-patch -k -m --stdout v2.6.14..private2.6.14 | git am -3 -k

        An alternate participant submission mechanism is using the git request-pull or pull-request mechanisms (e.g as used on GitHub (www.github.com) to notify your
        upstream of your contribution.


    ... supprimé INTEGRATOR et REPOSITORY ADMINISTRATION





=========
Weblinks
=========

.. target-notes::
