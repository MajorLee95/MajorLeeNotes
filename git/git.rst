.. index::
    single: git

.. |clearer|  raw:: html

    <div class="clearer"></div>    
    
++++++++++++++++++++++++++++++++
Notes sur git
++++++++++++++++++++++++++++++++
.. image:: images/gitLogo.png
   :height: 100px
   :alt: git logo
   :align: left
   
   
:Auteur: J.Soranzo
:Date: Novembre 2019
:Societe: VoRoBoTics
:Entity: VoLAB


|clearer|

.. contents::
    :backlinks: top

================================
git
================================
penser au fichier xmind



================================
petits trucs utiles 
================================
Logiciels 
======================================

`gitKraken`_

.. _`gitKraken` : https://www.gitkraken.com/

Nécessite de créer un compte sur leur site ? Pourquoi au juste ?

`tortoisegit`_

 - dl dans outils/conception       
 - Ajoute un menu contextuel
			avec plein de commandes
            
.. _`tortoisegit` : https://tortoisegit.org/   
         
Suppression d'un fichier 
======================================
git rm
        
lister les fichiers indexé 
======================================
A priori git ls-files

Fichiers pas suivis git ls-files -o, sous-entendu --others (au pluriel)

Mais vers ou pointe origine 
======================================
 - git ls-remote
 - git remote show origin !!!
        
merger un seul fichier 
======================================
 - git fetch : recupère les branche distantes
 - git checkout La_branche contenant le fichier
 - git pull
 - retour sur la branche de travail
 - git checkout BRANCH FILE
    * BRANCH : le nom de la branche
    * FILE : chemin d'acces au fichier
            
exemple data/index.html ?

Je me suis mis dans le dossier en question et je n'ai donné que le nom du fichier et cela fonctionne
sous-entendu sans le chemin complet.
                
Ecraser les dernière modif qui n'ont pas été commitées 
===========================================================
 - git checkout -- <file> (comme le signal la commande git status)
 - git reset --hard HEAD~1 (retour au dernier commit)
 - git rebase -i HEAD~10
 
 A propos de git reset --hard HEAD~1::
 
    When using git reset --hard HEAD~1 you will lose all uncommited changes in addition to the 
    changes introduced in the last commit. The changes won't stay in your working tree so doing 
    a git status command will tell you that you don't have any changes in your repository.
    Tread carefully with this one. If you accidentally remove uncommited changes which were never 
    tracked by git (speak: committed or at least added to the index), you have no way of getting 
    them back using git.

Retirer un répertoire de l'index  
======================================
Pour qu'il soit pris en compte par le git ignore::

    git rm --cached -r build
    
A condition de faire le add avant

Puis de les retirer après de l'index

lister les fichier dossier ignorés ? 
======================================
git ls-files --others -i --exclude-standard::
            
		git ls-files --stage
        
attention dans .gitignore un répertoire se termine par / et pas \
        
Ratacher la tête 
======================================
Procédure::

    git checkout -b temp
    git branch -f master temp
    git checkout master
    git branch -d temp
        
      
        
Annuler le dernier commit 
======================================
    
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
    Cette commmande permet de revenir à l'état du dernier commit (ne pas confondre)

Autres possibilités::

    git revert
    ou git add . suivi d'un git commit --amend
        
        
        
Lister les commit d'une branche distante 
=========================================
- Utile quand on est out of date
- git remote show
- git ls-remote

Dépôt git sur clé usb 
======================================

Créer `un dépôt git sur une clé usb, sur wikibook`_

.. _`un dépôt git sur une clé usb, sur wikibook` : https://en.wikibooks.org/wiki/Git/Repository_on_a_USB_stick

=====================================
Reste des notes xmind a transformer
===================================== 
        
::  
        
	une ch'tite commande sympa git log --pretty=oneline --abbrev-commit --graph --decorate
		trace l'arborescence sous forme textuelle
	clé SSH
		visiblement dépendante de l'ordinateur non ?
		Au tout au moins réside dans un répertoire locale de la machine
		Comment les entrées dans un nouvel environnement ?
	cherry-pick
		écrèmer
	Lister les différences entre branches locale et branche distante
		git diff maBranche origin/branche
			ne se connecte pas au serveur en réalité
			fait la diff par rapport au copies locale
		avant faire un git fetch
	git push
		Situation 
			git local
			je veux le mettre sous github
			adding-an-existing-project-to-github-using-the-command-line/
			git push --all
				from official ref
				Push all branches (i.e. refs under refs/heads/); cannot be used with other <refspec>.
	supprimer une branche distante
		git push origin : <nombrancheasupprimer>
	Merge branche distante
		git pull non !
	Traquer une nouvelle branche distante
		le 31/03
			avec tutoise
			on commence par un git fetch origin pour mettre à jour la base locale
			puis un checkout de la branche distante => créé une branche locale.
		git branch -- track <branch> <branche_distante>
	créer un dépot distant sur le serveur du VoLAB
		git init --bare chemin
			attention dans la ligne de commande remplacer tous les \ par des /
			sur le serveur
				le -- bare sur le serveur est mandatory sinon on se fait tej au moment du push
				on ne sairait une fois pusher sur un rep avec un working dir ça se fait pas alley un
		en local
			soit changer origin si c'est un dépot existant
	Errors
		git cannot lock ref d'une branche distante lors d'un pull
			le fichier dans l'arbo git était corrompu
	lister les fichiers d'une branche
		git ls-tree nom_de_la_branche -r (recursiv)
	git fetch --prune
		nettoyage des liens pourri
	merge d'un répertoire d'une autre branche
		git checkout branch chemin
	Déplacer le dernier commit d'une branche vers une autre branche
		git checkout l'autre branche
		git merge la branche où se trouve le commit fautif
		git checkout la branche du commit fautif
		git reset --hard HEAD~1


=========
Weblinks
=========

.. target-notes::
