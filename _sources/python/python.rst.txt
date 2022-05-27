.. index::
    single: Python

++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
Python (mes notes)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

:Auteur: J.Soranzo
:Date: Août 2020
:mise à jour: 21/10/2021
:Societe: VoRoBoTics
:Entity: VoLAB

.. contents::
    :backlinks: top


====================================================================================================
Disclaimer
====================================================================================================
Ce fichier est constitué de mes notes personnelles sur Python. Il ne s'agit en aucune manière d'un
cours ou quoi que ce soit d'autre dans le genre. Ce serait plutôt un pense-bête.

====================================================================================================
Pourquoi les gens aiment Python
====================================================================================================
Parce qu'il est comme ARDUINO, il permet d'arriver simplement et rapidement à un résultat concret.

On peut tout tester dans la console ! !c'est le couteau suisse du programmeur.

Supprime la nécessité d'apprendre un IDE

Python c'est 31 mots clé !


====================================================================================================
Docs
====================================================================================================
`La librairie standard`_

.. _`La librairie standard` : https://docs.python.org/3/library/index.html

Index des package sur `Pypi Python Package Index`_

.. _`Pypi Python Package Index` : https://pypi.org/

.. WARNING::

    Toute la doc Python est téléchargeable sur https://www.python.org/ rubrique documentation dans 
    plusieurs langues !


====================================================================================================
Outils, IDE...
====================================================================================================

Miniconda, conda
----------------------------------------------------------------------------------------------------
Utilisation de miniconda3

`Conda documentation`_

.. _`Conda documentation` : https://docs.conda.io/en/latest/miniconda.html


`Conda cheat sheet`_

.. _`Conda cheat sheet` : https://docs.conda.io/projects/conda/en/latest/user-guide/cheatsheet.html

Mes commandes vraiment utiles::

    conda create -n toto (par défaut python 2.7)
    conda create -n toto python=3.6
    conda list -n toto
    conda remove --name toto --all
    conda info --envs
    conda --version

**Conda n'est pas lié à un répertoire !**


:: 

    conda env create -p ../venv -f locks/conda.yml
    Commande fonctionnelle liste des packages communs

::

    conda  create versus conda env create : la version avec env permet de créer ou d'exporter
    un environnement grâce aux fichiers yml

Pour exporter un environnement::

    conda env export --name toto --file constructor_of_toto.yml

Conda est lié à un dépôt. qui peut contenir des package différents d'une plateforme à l'autre.
Comme sur Raspberry pi: ``conda info`` indique ce dépôt:: 

    channel URLs :  https://repo.continuum.io/pkgs/free/linux-armv7l/
                    https://repo.continuum.io/pkgs/free/noarch/
                    https://repo.continuum.io/pkgs/pro/linux-armv7l/
                    https://repo.continuum.io/pkgs/pro/noarch/    

Donc sur RPi avec conda, il ne faut même pas espérer faire du python autre que 3.4 et 2.7

Et bien si, grâce à ``conda config --add channels rpi`` puis ``conda search --full-name python``

Source : site : ANegron's Blog `How to install Conda and Docker on your Raspberry Pi`_

.. _`How to install Conda and Docker on your Raspberry Pi` : https://www.anegron.site/2020/06/18/how-to-install-conda-and-docker-on-your-raspberry-pi/




.. index::
    pair: Python; Jupiter

.. _jupiterProjet:

Jupiter
----------------------------------------------------------------------------------------------------
A revoir

`Project Jupyter`_ exists to develop open-source software, open-standards, and services for interactive
computing across dozens of programming languages.

.. _`Project Jupyter` : https://jupyter.org/

`Prise en main de l'outil Jupyter`_

.. _`Prise en main de l'outil Jupyter` : https://www.youtube.com/watch?v=g2yckh3_22E


----------------------------------------------------------------------------------------------------


A revoir
----------------------------------------------------------------------------------------------------
`Scrapy`_  : permet de "grater" des page web

.. _`Scrapy` : https://doc.scrapy.org/en/1.2/intro/overview.html

`Python Code Quality: Tools & Best Practices`_

.. _`Python Code Quality: Tools & Best Practices` : https://realpython.com/python-code-quality/



.. index::
    pair: Python; Documenter du code Python

.. _documenterProjetPython:

====================================================================================================
Documenter du code Python et relation avec Sphinx
====================================================================================================
Je ne trace ici que les écueils auxquels j'ai été confronté. Il y a de nombreux sites qui traitent
du sujet.

Un très bon site pas à pas : `blog.flozz.fr`_

.. _`blog.flozz.fr` : https://blog.flozz.fr/2020/10/04/documenter-un-projet-python-avec-sphinx/

Cela passe par docstring ``""" """`` 

Sphinx permet de transformer des fichier restructured text en fichier latex, html... Mais, il 
n'extrait pas tout seul les docstring du code Python pour cela il lui faut une extension.

Comme autodoc qu'il faut ajouter dans le fichier config.py::

    extensions = [
        'sphinx.ext.autodoc'
    ]

Il faut créer une arborescence documentaire de fichiers rst et y placer des directives comme::

    .. automodule:: CRdcGui

    .. autoclass:: CRdcGUI
        :members:
        :undoc-members:

Il peut être aussi fort util de renseigner le chemin vers les sources au début du fichier config.py::

    import os
    import sys
    sys.path.insert(0, os.path.abspath('../sources'))

====================================================================================================
Éléments de langages
====================================================================================================
Annotations
----------------------------------------------------------------------------------------------------
Depuis Python 3.6, on peut annoter les paramètres d'une fonction ou les 

voir:

https://zestedesavoir.com/tutoriels/954/notions-de-python-avancees/2-functions/2-annotations-signatures/


Notations / opérateurs
----------------------------------------------------------------------------------------------------

.. index::
    pair: Python; Hexa

- Notation hex : C'est 0x33
- Binaire : 0b
- Octal : 0o

Long integer 123L

Code sur plusieurs lignes c'est avec le caractères \\

.. index::
    pair: Python; true/false

**Vrai, faux**

True et False avec une majuscule

.. index::
    pair: Python ;  Opérateurs

**Opérateurs**

Arithmétique : je ne parle pas des courants::

    % 	Modulo
    ** 	Puissance
    // 	Division entière

Tous les opérateurs arithmétiques peuvent être combinés avec = comme //= ou %= ...

les opérateurs logiques::

    X|Y X ou Y, ^ ou exclusif, & pour et, ~ pour l'inversion

Les opérateurs booléens::

    X or Y, X and Y et not X

Les opérateurs de comparaisons::

    == et != ou <>


.. index::
    pair: Python;  Tuple

Tuples
----------------------------------------------------------------------------------------------------
Ce sont simplement des listes non modifiables syntaxe : 
() à l d [] par rapport à la syntaxe d'une liste.

.. index::
    single: Python;  Liste

Listes
----------------------------------------------------------------------------------------------------
Toutes les méthodes de list::

    >>> listMethode[listMethode.index('clear'):listMethode.index('sort')]
    'clear', 'copy', 'append', 'insert', 'extend', 'pop', 'remove', 'index', 'count', 'reverse'

**Création**::

    toto = [1, 5, "tutu", 16.9, (12,3), ["Pierre", "05.12.34.56.78"]]
    toto = list([14,5,12])
    truc = list() #pour une liste vide
    ou encore troc = []

Éléments de syntaxe: les crochets.

**L'intérêt**::

    >>> seasons = ['Spring', 'Summer', 'Fall', 'Winter']
    >>> list(enumerate(seasons)) #liste de tuples (index, éléments)
        permet de créer une nouvelle liste avec des commandes !

**Ajout**::

    maList.append(nvlElement)
    attention pas de valeur de retour. Travaille directement sur maList
    maList.insert(6, "titi")
    maList.extend(autreListe)

**Concaténer 2 listes**::

    6 méthodes

    for i in test_list2 :
        test_list1.append(i)

    list3 = list1 + list2

    res_list = [y for x in [list1, list2] for y in x]

    extended_list.extend(listtoadd)

    res_list = [*test_list1, *test_list2]

    res_list = list(itertools.chain(test_list1, test_list2))



**Accès**
    Pour accéder à un élément : malist[indice] indice commence évidement à 0
    Pour accéder à plusieurs élément consécutifs : malist[x:y]


**Suppression**::
    
    maList.remove("tutu")
    malist.pop() ou maList.popleft()
    ou del maList[3]


**Longueur**
La méthode count permet de conter le nombre d'occurence d'un élément dans la liste.
Il faut utiliser la fonction len(malist)

**pile et queue**
Elle peuvent être utilisées en pile ou en queue cf. <https://docs.python.org/3.1/tutorial/datastructures.html>

Grace à pop pour les piles et popleft pour les files d'attente.

insert(0 , item) et pop() : pour les queues.

append() et pop() : pour les piles ou insert(0, item) et pop(0) semble moins efficace 
(faut tout décaler)

Concept très intéressant de tableau qui se vide au fur et à mesure de son traitement. Quand le 
tableau est vide, on a fini (récursivité...). De plus pop renvoi l'élément retirer ;-)

**test d'appartenance**::

        if variable in maListe:
            instruction in !

.. warning:: 
    attention à la copie de liste list2=list1 ne copie que le nom (l'adresse) pas les données.

Mais on peut utiliser les compréhensions de listes::

    list2 = [x for x in list]
    ou plus simplement list2 = list(list1)
    ou encore list2=list1.copy()

.. index::
    pair: Python;  Compréhension de liste

**Compréhension de listes** ou listes en intension

La syntaxe est : ``[ action iterable]``::

    [ 'a' for i in rang(10) ]
        noter que i n'est pas nécessairement utilisé dans action

C'est assurément un des grandes forces de Python et un élément de programmation nouveau.
L'idée est de **créer un liste** en une seule ligne
Voir `les comprehensions de liste sur Sam et Max`_

Ca fabrique une liste !

.. _`les comprehensions de liste sur Sam et Max` : http://sametmax.com/python-love-les-listes-en-intention-partie/


.. code::

    [expression for element in sequence]
    moyen de filtrer les listes
        mais pas que
        [expression for element in sequence if condition]
    List comprehensions provide a concise way to create lists from sequences. Common applications
    are to make lists where each element is the result of some operations applied to each member 
    of the sequence, or to create a subsequence of those elements that satisfy a certain condition.

    exemples

    [nb * nb for nb in liste_origine]
        c'est en ça que python devient for (on parcours la liste en une seul ligne. L'astuce est de créer une nouvelle liste
        [nb for nb in liste_origine if nb % 2 == 0]
            encore plus fort
        [str(round(355/113, i)) for i in range(1, 6)]
            donne : [’3.1’, ’3.14’, ’3.142’, ’3.1416’, ’3.14159’]
        ou encore:
            [x*y for x in vec1 for y in vec2]

Création d'une liste de n éléments identique::

    >>> malist =[]
    >>> for i in range(10):
        malist.append(2)

mais::

    truc=[truc.append(5) for i in range(10)] ne marche pas
    mais truc = [ 5 for i in range(10) ] marche

**Remarque** : le for element in sequence est le même que dans la syntaxe d'une boucle for.
On peut considérer la compréhension de liste comme une boucle for condensée.

**Astuce**

- lire les compréhension de liste de la droite vers la gauche.
- maliste.append([1,2,5]) n'ajoute qu'un seul élément à la liste qui est [1,2,5]
- en revanche maliste **+=** [2,3,5] fonctionne et ajoute 3 élément à la liste ou .extend()
- la longueur de la liste malist.len() n'existe pas il faut faire len(list)
- maliste.append(2,3,5) ne fonctionne pas

**Liste et paramètres de fonction**
la syntaxe au niveau definition est ::

    def fonction(*parametres):

la fonction reçoit un tuple des paramètres.

L'appel d'une telle fonction peut se faire fonction( 1, 3, 6) ou fonction(\*malisteDeParametres)

Cela est réservé au paramètres non nommés et on peut combiner des paramètre et une liste.
La liste doit se trouver en dernier ainsi que des paramètres nommés qui se trouveront après.

**enumerate**
Voir `Enumerate`_

Exemples en vrac:

.. code:: python
    
    list(range(10)) #! crée une lise de 0 à 9
    [x*y for x in vec1 for y in vec2]
    avec des un if :
    listeRequetes = [ req[5][1:] for req in tablesEchanges if req[2] == 'VOL Numéro 1']
    # tablesEchanges est une liste de listes


.. index::
    pair: Python;  Dictionnaire

Dictionnaires
----------------------------------------------------------------------------------------------------
`Doc officielle sur les dictionnaires`_

.. _`Doc officielle sur les dictionnaires` : https://docs.python.org/3.1/tutorial/datastructures.html#dictionaries

Mot clé : dict, création: maVar = dict()

Éléments de syntaxe: les accolades et les :

On peut aussi créer des dictionnaires déjà remplis ::

    placard = {"chemise":3, "pantalon":6, "tee-shirt":7} - on notera les accolades

Remplissage : maVar[ clé ] = valeur

Clé et valeur peuvent être de tout type (y compris des tuples par exemple et y compris dans 
le même dictionnaire).

Exemple::

    dico['a',0]="toto" on note que les parenthèses du tuple sont facultatives
    >>> mon_dictionnaire["pseudo"] = "Prolixe"
    >>> mon_dictionnaire["mot de passe"] = "*"
    >>> mon_dictionnaire
    {'mot de passe': '*', 'pseudo': 'Prolixe'}
        
        la clé est par conception unique
            maVar[ "ici" ] = 234
            ...
            puis maVar[ "ici" ] = 'RESTE'
                Reste écrase 234.

{ 'banane', 'pomme', 'citron' } n'est pas un dictionnaire sans valeurs. C'est un set ou ensemble.
A la différence des liste, il ne peu contenir 2 fois la même valeur.

**Les dictionnaires peuvent servir de paramètre nommés d'une fonction** comme les listes pour les 
paramètres non nommés.

[ a for a in dico.keys()] donne la liste des clés

[ a for a in dico.items()] donne une **liste de tupple** et pas un dictionnaire::

    {'NADIA': 0, 'JOJO': 14}
    [('NADIA', 0), ('JOJO', 14)]

.. index::
    single: Python; Enumerate

Enumerate
----------------------------------------------------------------------------------------------------
C'est un mot clé et une fonction qui retourne un tuple(indice, valeur) et qui s'applique à tous
les iterators.

Différence::

    lsie = [12,35,'rien',65.3]
    >>> for elt in lsie:
    	print(elt)
	
    12
    35
    rien
    65.3
    >>> for elt in enumerate(lsie):
        print(elt)
     
    (0, 12)
    (1, 35)
    (2, 'rien')
    (3, 65.3)
    >>>


.. index::
    pair: Python;  Fonctions

Fonctions
----------------------------------------------------------------------------------------------------
Syntaxe::

    def fonctionName(parametres, param = defValue) :
        return a, b, c,d

Les fonction peuvent retourner plusieurs valeurs.

Pas de surcharge

.. index::
    pair: Python;  Lambda

**fonction lambda** ? f = lambda x: x * x

Intérêt ? Écrire du code plus concis.

lambda est un mot clé

`les fonctions lambda sur developpez`_

sur open classroom `meilleur explication de la fonction lambda sur Openclassroom`_

`Exemple du tri avec une lambda sur Openclassroom`_

En résumé: on met dans une variable une fonction pour pouvoir l'appeler ensuite sauf qu'on ne donne
pas de nom à la fonction.

Fonctions avec nombre paramètre indéterminé::

    def fonction_inconnue(*parametres):
        *parametre défini un tuple (rien à voir avec les pointeurs ?!
        on peut mixer
            def fonction_inconnue(nom, prenom, *commentaires):
    >>> def fonction_inconnue(*parametres):
    ...     """Test d'une fonction pouvant être appelée avec un nombre variable de paramètres"""
    ...     
    ...     print("J'ai reçu : {}.".format(parametres))
    ... 
    >>> fonction_inconnue() # On appelle la fonction sans paramètre
    J'ai reçu : ().
    >>> fonction_inconnue(33)
    J'ai reçu : (33,).
    >>> fonction_inconnue('a', 'e', 'f')
    J'ai reçu : ('a', 'e', 'f').
    >>> var = 3.5
    >>> fonction_inconnue(var, [4], "...")
    J'ai reçu : (3.5, [4], '...').
    >>>

Une liste peu devenir paramètres d'une fonction, vachement puissant::

    >>> liste_des_parametres = [1, 4, 9, 16, 25, 36]
    >>> print(*liste_des_parametres)

.. index::
    pair: Python; Décorateurs

**Les décorateurs**

Pour schématiser, une fonction modifiée par un décorateur ne s'exécutera pas elle-même mais 
appellera le décorateur. C'est au décorateur de décider s'il veut exécuter la fonction 
et dans quelles conditions. (from *openclassroom*). C'est un moyen simple de modifier le 
comportement d'une fonction. Un décorateur est une fonction (qu'il faut donc définir de la même 
manière qu'une autre fonction) qui est appelé avant l'appel de la fonction elle-même. Il se place
juste une ligne avant la définition de la fonction et est précédé par @.

On peut créer des décorateurs qui accepte des paramètres et dans ce cas on atteint vite 3 niveaux
de définition de fonctions imbriquées. Cf. OpenClassromm

Autres `explication très détaillée par Simeon Franklin`_ en anglais.

partial() appartient functool

super() sujet : class, hiérarchie

Permet d'appeler explicitement une méthode de la classe mère si celle-ci est redéfinie 
dans  la classe fille. Par exemple init


.. _`les fonctions lambda sur developpez` : https://python.developpez.com/cours/DiveIntoPython/php/frdiveintopython/power_of_introspection/lambda_functions.php

.. _`meilleur explication de la fonction lambda sur Openclassroom` : https://openclassrooms.com/courses/apprenez-a-programmer-en-python/pas-a-pas-vers-la-modularite-1-2#/id/r-231371

.. _`Exemple du tri avec une lambda sur Openclassroom` : https://openclassrooms.com/courses/apprenez-a-programmer-en-python/parenthese-sur-le-tri-en-python#/id/r-2233424

.. _`explication très détaillée par Simeon Franklin` : http://simeonfranklin.com/blog/2012/jul/1/python-decorators-in-12-steps/

----------------------------------------------------------------------------------------------------

.. index::
    pair: Python; Modules

Modules
----------------------------------------------------------------------------------------------------
C'est tout simplement un fichier .py qui contient des variables, des fonctions ou des classes.


.. index::
    pair: Python; import

Plusieurs mots clés sont associés à la notion de module::

    from
    import
    as


Plusieurs syntaxes sont possible::

    import maths
    from maths import sqr
    import maths as mathematiques
    from myModule import *
        importe  myModule dans l'espace de nom principal
        Si myModule est un package alors les noms des modules qu'il contient sont créés dans
        l'espace des noms courants ainsi que les noms de ses sous-packages mais pas de leurs modules
        respectifs.
    import crée un espace de nom (*from OpenClassroom*)


**Astuce**::

    diff entre import os et from os import *
    dans le premier on est obligé de mettre os.fonction()
    dans le second cas les fonctions font parties de l'espace de noms courant.
    Mais quand il s'agit d'un package avec des sous package
        from PyQt5.QtWidgets import QApplication,QWidget


.. NOTE::

    - Lister les modules accessibles : ``help('modules')``
    - Lister les package installés : ``pip list`` ou ``pip freeze``

Faire un test de module dans le module-même::

    if __name__ == "__main__":
 	    code à executer

Le code qui suit cette ligne n'est exécuté que si la condition est vrai. En d'autres termes
si le module est programme principal et non issu d'un import.

On peut intégrer l'aide dans le module ou dans la fonction::

    """visiblement en plaçant le texte en début de bloc (par exemple just entre le nom de la 
    fonction et le reste du code et en encadrant le texte avec un tripe double cote"""
    Ou carrément en début de module

    help("nomPackage.nomFonction ou nomPackage")

.. index::
    pair: Python; doctest

On peut même intégrer un test automatique cf. doctest.
The doctestmodule makes unit testing as simple and painless as possible. To use it all
we need to do is add examples to our docstrings, showing what we would type into the
interactive Python interpreter (or IDLE) and what response we expect back.

**A revoir** 24/08/2020

----------------------------------------------------------------------------------------------------

.. index::
    pair: Python; Exception

Les exceptions
----------------------------------------------------------------------------------------------------
On peut intercepter les erreurs (ou exceptions) levées par notre code grâce aux blocs try except.
La syntaxe d'une assertion est assert test:. Les assertions lèvent une exception AssertionError
si le test échoue.

On peut lever une exception grâce au mot-clé raise suivi du type de l'exception.

Mots clés : try et except (dans sa version la plus basic)

Il est plus que vivement conseillé de préciser un type d'erreur derrière except au risque de 
capturer toutes les exceptions y compris ctrl+c par exemple !

Un grand classique d'utilisation est la saisie de valeur::

    >>> while True:
    ...     try:
    ...         x = int(input("Please enter a number: "))
    ...         break
    ...     except ValueError:
    ...         print("Oops!  That was no valid number.  Try again...")

Il est également possible de faire suivre l ’instruction try de plusieurs blocs except. Chacun
d’entre eux traitant un type d’erreur spécifique::

    except
        Except error_name1:
        Except error_name2:
    else
    finaly
        A finally clause is always executed before leaving the try statement, même s'il y a un
        return dans le bloc
    pass
    assert
        Si le test renvoie True, l'exécution se poursuit normalement. Sinon, une exception
        AssertionError est levée.
        Il faut voir cela comme une affirmation (une assertion) dans si elle n'est pas correcte 
        alors erreur.

Exemples::

    try:
        resultat = numerateur / denominateur
    except NameError:
        print("La variable numerateur ou denominateur n'a pas été définie.")
    except TypeError:
        print("La variable numerateur ou denominateur possède un type incompatible avec la division.")
    except ZeroDivisionError:
        print("La variable denominateur est égale à 0.")
    else:
        print("Le résultat obtenu est", resultat)
    finally:
        # Instruction(s) exécutée(s) qu'il y ait eu des erreurs ou non
    except type_de_l_exception: # Rien ne doit se passer en cas d'erreur
        pass
            annee = input("Saisissez une année supérieure à 0 :")

    try:
        annee = int(annee) # Conversion de l'année
        assert annee > 0
    except ValueError:
        print("Vous n'avez pas saisi un nombre.")
    except AssertionError:
        print("L'année saisie est inférieure ou égale à 0.")

Sortir d'une boucle infinie par une iterruption clavier

.. index::
    pair: Python; package

Les packages
----------------------------------------------------------------------------------------------------
Il s'agit tout simplement d'un répertoire de module

On peut importer un pakage entier ou seulement un module dans le package ou seulement une fonction
d'un module dans un package.

::

    from package.fonctions import table
    import tkinter as tk
    from tkinter import messagebox
    from tkinter import ttk

On trouve de nombreux package et fonctions dans C:\Python34\Lib

Un package doit obligatoirement contenir un fichier _init_.py même vide. Ceci n'est plus vrai 
depuis la version 3.3

Liste des package hyper courant:

- random   : fonctions permettant de travailler avec des valeurs aléatoires
- math     : toutes les fonctions utiles pour les opérations mathématiques (cosinus,sinus,exp,etc.)
- sys      : fonctions systèmes
- os       : fonctions permettant d'interagir avec le système d'exploitation
- time     : fonctions permettant de travailler avec le temps
- calendar : fonctions de calendrier
- profile  : fonctions permettant d'analyser l'execution des fonctions
- urllib2  : fonctions permettant de récupérer des informations sur internet
- re       : fonctions permettant de travailler sur des expressions régulières

.. index::
    pair: Python; Fichiers

Les fichiers
----------------------------------------------------------------------------------------------------
outres le classique ``fichier = open('gilename', 'atttrib')`` avec comme attribut:

r, w, X, a, b, t, +

X création exclusive, échoue si le fichier exsite déjà. 

+ : ouvre en modification (lecture et écriture)

Il y a aussi la syntaxe::

    with open('file', 'wb') as fichier:

Avantage : pas besoin de close

.. index::
    pair: Python; Pickel

Un mot sur le module **pickel**: il permet la sérialisation de variable (cf doc officielle chapitre
12). Il utilise 2 méthodes : dump et load. C'est très utile pour stocker des variables et les 
recharger par la suite.

Décrit dans `openclassroom pickle`_

.. _`openclassroom pickle` : https://openclassrooms.com/fr/courses/235344-apprenez-a-programmer-en-python/232431-utilisez-des-fichiers#/id/r-232430

Dans tous les exemples que j'ai pu trouvé, on n'y voit jamais qu'une seule variable aussi complexe
soit elle. J'ai lu un post qui disait de regrouper ces variables dans une liste avant de les
sauvegarder

Exemple simpliste:

.. code:: python

    import os

    file_path = "D:/data123.txt"

    #check if file is present
    if os.path.isfile(file_path):
        #open text file in read mode
        text_file = open(file_path, "r")

        #read whole file to a string
        data = text_file.read()

        #close file
        text_file.close()

        print(data)

Autre exemple encore plus simpliste:

.. code:: python

    with open('file.txt') as f:
        contents = f.read()
        print(contents)

.. index::
    pair: Python; Objets

Les objets
----------------------------------------------------------------------------------------------------
classe template::

        class nomClasse: # Définition de notre classe
        """Classe documentation"""
        
            def __init__(self): # Notre méthode constructeur
                """Documentation du constructeur"""
                self.attr1 = valeurInitiale
                
            def methode(self, param1):
                """doc"""
                #code

**Importance** du paramètre self! Il faut mettre son grain de self un peu partout


créer une instance::

    Attention : var = nomclasse ne crée pas d'instance !!!
    var = nomClasse() oui

constructeur::

        def __init__(self, var1, var2...)
            # double underscore init double underscore
            self.attribut1 = var1...

        le constructeur est considéré comme une méthode spéciale au même titre que __dict__
        est un attribut spécial

Méthodes et self::

    on peut appeler une méthode depuis l'objet instancié ou depuis sa classe
        a = objet()
    a.methode(autreVar)
    ou objet.methode(a, autreVar)


Ceci provient du fait que les méthodes ne sont pas recopiées dans chaque objet instancié seulement
les attributs sont différents

Méthodes commence toutes avec self comme premier paramètre. Sauf les **méthodes statiques** et 
les **méthodes de classe**

.. index::
    pair: Python; property

**Getters et setters**: bien que la notion de private n'existe pas, on peut, grace au mot clé 
property créer des accesseurs et mutateurs

Exemple::

    class Personne:
     """Classe définissant une personne caractérisée par :
     - son nom ;
     - son prénom ;
     - son âge ;
     - son lieu de résidence"""
 
     
    def __init__(self, nom, prenom):
        """Constructeur de notre classe"""
        self.nom = nom
        self.prenom = prenom
        self.age = 33
        self._lieu_residence = "Paris" # Notez le souligné _ devant le nom


    def _get_lieu_residence(self):
    """Méthode qui sera appelée quand on souhaitera accéder en lecture
        à l'attribut 'lieu_residence'"""
 
        print("On accède à l'attribut lieu_residence !")
        return self._lieu_residence


     def _set_lieu_residence(self, nouvelle_residence):
        """Méthode appelée quand on souhaite modifier le lieu de résidence"""
        print("Attention, il semble que {} déménage à {}.".format( \
                self.prenom, nouvelle_residence))
        self._lieu_residence = nouvelle_residence


    # On va dire à Python que notre attribut lieu_residence pointe vers une
    # propriété
    lieu_residence = property(_get_lieu_residence, _set_lieu_residence)

Autre façon de déclarer les getters et setteurs::

    def _width(self):
        return self.__width
    def _setWidth(self, width):
        # Perform some computation
        self.__width = width
    width = property(fget=_width, fset=_setWidth)
    #on notera le jeu des doubles __ dans self.__width et sa disparition dans width = property

Property permet de redéfinir un attribut en lui allouant des acesseur et mutateur. Cela permet 
de redéfinir le comportement des attributs sans casser le code utilisateur.

width est redéfini alors qu'à l'extérieur on fait tjrs objet.width

Autre façon de transformer une méthode en propriété: grâce au décorateur **@property**::

    class Position:
    def __init__(self, longitude_deg, latitude_deg):
        self.longitude_deg = longitude_deg
        self.latitude_deg = latitude_deg

    @property
    def longitude(self):
        return self.longitude_deg * math.pi / 180

    Utilisation : position.longitude

.. index::
    pair: Python; Méthode spéciales

**Les méthodes spéciales**:  elles sont encadrées par __

Il en existe pour surcharger la plupart des opérateurs::

    __add__ pour +
    __gt__ pour > 
    __mul__ pour *
    ...
    +=

La liste complète est énorme <https://www.mindmeister.com/fr/10510492/python-underscore>

Quelques unes parmi les plus intéressantes::

    __init__
    __del__
    __repr__ pour l'affichage de l'objet
    __str__ utilisée lors de la conversion de l'objet en chaîne ;-)
    __getatr__
    __setattr__
    __delattr__
    __iter__
    __next__

Il y a aussi des "buildin functions" qui font le même boulot que ces méthodes::

    getattr(objet, "nom") # Semblable à objet.nom
    setattr(objet, "nom", val) # = objet.nom = val ou objet.__setattr__("nom", val)
    delattr(objet, "nom") # = del objet.nom ou objet.__delattr__("nom")
    hasattr(objet, "nom") # Renvoie True si l'attribut "nom" existe, False sinon

Celles des object conteneurs::

    __getitem__
    __setitem__
    __delitem__
    __contains__
    __len__ équivalent de la fonction len(objet) <=> objet.__len__()

Permette de fournir des métadata également comme::

    __autor__
    __version__
    __licence__

Certaines font vraiment partie du langage et d'autre tiennent plus de la convention de nommage.
c'est le cas de version autor...

L'attribut spécial __dict__. Cet attribut est un dictionnaire qui contient en guise de clés les 
noms des attributs et, en tant que valeurs, les valeurs des attributs.

**Héritage** ``class fifille(maman)``.

Biltin function super()::

    Il est souvent nécessaire d'initialiser un objet
        __init__(self, param1, param2, ...)
        Pour une classe fille c'est pareil et en plus il faut faire appel à l'init de la class mere
        avec
            maman.__init__(self, param1, pram2,...) seulement ceux de la maman
            (les 2 liste de paramètres peuvent être différentes)

        ou avec
            super(fifille, self).__init__(param1, param2...)
            pas de self dans la liste des param de maman !

.. code:: python

    class C(B):
        def method(self, arg):
            super().method(arg)    # This does the same thing as:
            # super(C, self).method(arg)

Fonctions utiles : ``issubclass()`` et ``isinstance()``

**Héritage multiple**: quand une classe hérite de plusieurs classes en parallèle:

``classeFille(mereA, mereB)``

L'héritage permet la surcharge des méthodes.

L'ordre de recherche d'un méthode correspond à l'ordre de déclaration:

- fille
- mere1
- mere1parentes
- mere2
- mere2Parents
- ...

On peut à tout moment préciser la méthode appelée par nomClasse.nomMethode(self,...)


**Simple underscore** pour attributs et méthodes: Python does have a concept of "private"—objects
with names that begin with a single leading underscore are considered to be private. 
As far as methods and instance variables are concerned, their privacy is merely a convention 
that we are invited to respect. And as for modules, private classes and functions, i.e., 
those whose name begins with a leading underscore, are not imported when using the from moduleName
import syntax. Python also has a concept of "very private"—methods and attributes with names that
begin with two leading underscores.

Very private objects are still accessible, but the Python interpreter angles their names to make 
it difficult to access them by mistake.

Il est possible aussi d'avoir des attributs de la class (static). Il faut les déclarer avant le 
constructeur.

On y accède avec le nom de la classe devant : nomClass.attrib1 +=1 pa exemple

Ainsi que des méthode de class avec le mot clé : cls + build in fonction classmethod()

Une méthode de classe a comme premier paramètre cls et pas self. Exemple:

.. code:: python

    class Compteur:     
    """Cette classe possède un attribut de classe qui s'incrémente à chaque     
    fois que l'on crée un objet de ce type"""       
    objets_crees = 0 # Le compteur vaut 0 au départ     
    
    def __init__(self):         
    """À chaque fois qu'on crée un objet, on incrémente le compteur"""
        Compteur.objets_crees += 1     
        
    def combien(cls):         
    """Méthode de classe affichant combien d'objets ont été créés"""
        print("Jusqu'à présent, {} objets ont été créés.".format(cls.objets_crees))

    combien = classmethod(combien)

Pour les méthodes static: ni self, ni cls + utiliser la fonction staticmethod

**Métaclasse** <https://openclassrooms.com/fr/courses/235344-apprenez-a-programmer-en-python/233659-decouvrez-les-metaclasses>

L'idée est créer des classe dynamiquement c'est à dire pendant l'exécution. 
Fonctionnalité très avancées selon moi




Itérateur & générateur
----------------------------------------------------------------------------------------------------

Un itérateur est avant tout une classe qui va être chargé de parcourir l'objet conteneur
: cf. `opencs chapitre sur les boucles for`_

.. _`opencs chapitre sur les boucles for` : https://openclassrooms.com/fr/courses/235344-apprenez-a-programmer-en-python/233261-decouvrez-la-boucle-for


L'itérateur est créé dans la méthode spéciale __iter__ de la classe

Si on veut créer son propre itérateur pour sa propre classe, cela signifie qu'il faudra créer 
une nouvelle classe dont une instance est retournée pat __iter__.

Donc en général __iter__ fait un ``return monIterator(self)``

L'itérateur a une méthode spéciale __next__. next() ou __next__ lève l'exceptions StopIteration 
en fin d'itération.

Il y a 2 fonctions spéciales python associées à ces méthodes : iter() et next().

Un **générateur** est une fonction (ou méthode) qui contient le mot clé spécial yield

`Doc python sur les generator`_

.. _`Doc python sur les generator` : https://docs.python.org/3/glossary.html#term-generator
        
C'est un moyen plus simple de créer et de manipuler des itérateurs

L'avantage du générateur est qu'il n'est pas besoin de créer une class itérateur ni de méthode
__next__ ni de lever l'exception de fin

Utilisation classique ::

    iter( monGenerator() )
    on peut créer des fonctions générateur independent de toute classe
        exemple : intervalle(5, 10) renvoi des nombre de 6 à 10

    Les générateurs accepte des co-routines très puissant
        méthodes : .close() et .send()
            y a pas restart

Tout est sur openclassroom, `chapitre sur les boucle for`_

.. _`chapitre sur les boucle for` : https://openclassrooms.com/fr/courses/235344-apprenez-a-programmer-en-python/233261-decouvrez-la-boucle-for#/id/r-233202

Il s'agit d'une fonction très avancée dans leur création.

If expression
----------------------------------------------------------------------------------------------------
Introduit avec la version 2.5 vise à faire la même chose que ``exp ?valeur si vrai:valeur si faux``
donc::

    X if condition else Y
    exemples:
    result = 'even' if a % 2 == 0 else 'odd'
    print (a if b else 0)

====================================================================================================
Astuces
====================================================================================================
tempo
----------------------------------------------------------------------------------------------------
::
    
    import time

    time.sleep(0.1) # en secondes

::

    from time import sleep

    sleep(0.1)


Sur les chaînes
----------------------------------------------------------------------------------------------------

.. index::
    pair: Python; Formater un chaîne

Formater une chaîne::

    "la chaine {1} à formater {0}".fomat( varZero, varUn)

Les chiffres dans les accolades sont facultatifs,
il s'agit de la méthode format de la class intégrée str

Tout est décrit en détail dans 
:download:`The Python Library Reference<fichiersJoints/library.pdf>` §Format String Syntax

.. index::
    pair: Python; Formater hexa

Pour de l'hexa::

    ":2X"
    print("Valeur hex = 0x{:04X}".format(a) )
    print("Valeur hex = {:#04X}".format(a) ) # mais directement 0X devant le nombre
    b=3.1425
    print("Valeur flottant 3 décimale = {:.3f}".format(b) )
    



Autre forme:

.. code:: python

    # formatage d'une adresse
    adresse = """
        {no_rue}, {nom_rue}
        {code_postal} {nom_ville} ({pays})"""
    .format(no_rue=5, nom_rue="rue des Postes", code_postal=75003, nom_ville="Paris", pays="France")
    print(adresse)


La class template à l'air bien aussi::

    from string import Template
    >>> s = Template(’$who likes $what’)
    >>> s.substitute(who=’tim’, what=’kung pao’)
    ’tim likes kung pao’

.. code:: python

    for i in range(len(chaine))


Génère tous les indices d'une chaîne


Initialiser une chaîne avec n fois le même caractère: ``chain = "-"*10``

::
    
    Recherche d'une lettre dans un mot
        for lettre in mot_complet:
                if lettre in lettres_trouvees:
    join str list
        a="toto" b=list(a) a=''.join(b)
    Supprimer les espaces
        méthode strip, rstrip ou lstrip
        
    pickling <https://docs.python.org/3/library/pickle.html>
        serialisation
        Chapitre 12 de la doc 3.4.4
        see also HDF5 et JSON

    Chaîne en nombre et inversement
    Chaîne en JSON

**Retour à la ligne**::

    print("\n") #tout simplement !

Tester, tester, tester
----------------------------------------------------------------------------------------------------
Cela doit devenir un réflexe, on peut tout expérimenter dans la console Python
des commandes seules mais aussi des bouts de codes qu'on a mis dans un fichier TOUT !

Jouer avec les fonctions, les classes dans des fichiers séparés, ça à l'air tout bête mais on peut
mettre des fonctions, des classes dans des fichiers et jouer avec dans la console.
 

Importer ses fichiers avec from mon_fichier import *

Pour les tests réels du code on se tournera vers `pytest`_ ou `unitest`_

.. _`pytest` : https://docs.pytest.org/en/6.2.x/#

.. _`unitest` : https://docs.python.org/3/library/unittest.html 

Print inline
----------------------------------------------------------------------------------------------------
Pour imprimer à la suite sans retour chariot ``sys.stdout.write(lettre) sys.stdout.flush()``

if
----------------------------------------------------------------------------------------------------
C'est bête mais  ``if: et elif:``

et pas ``else if`` ou ``elsif``

Où est python ?
----------------------------------------------------------------------------------------------------
::

    c:\>where.exe python
    C:\Users\nom\AppData\Local\Programs\Python\Python38\python.exe
    avec Windows search : python
        En 2 fois
        ouvrir l'emplacement du fichier
            chemin du raccourci
        propriété du racourci
        ouvrir emplacement de la cible

Turtle
----------------------------------------------------------------------------------------------------
Turtle <https://docs.python.org/3.3/library/turtle.html?highlight=turtle>

Petit truc graphique rigolo, plus riche qu'on ne pourrait s'y attendre !

Toujours terminé les script avec la fonction done()

Une vidéo sympa <https://www.youtube.com/watch?v=pxKu2pQ7ILo>


sur l'Aide
----------------------------------------------------------------------------------------------------
help et help short form::

            object.__dict__
            dir(objet)

Les 2 ne retournent pas tout à fait la même chose !

Afficher la doc d'un package::

    help()

Sur les liste, dico...
----------------------------------------------------------------------------------------------------
Parcours d'une liste en une seule ligne, c'est en ça que python devient fort et on crée une nouvelle 
liste, ceci se nomme liste en intention ou compréhension de liste::

    [nb * nb for nb in liste_origine]

Mais on peut également introduire un teste des valeurs dans cette opération::

    [nb for nb in liste_origine if nb % 2 == 0]

On peut vraiment faire des trucs puissants avec les listes en intention::

    [str(round(355/113, i)) for i in range(1, 6)]
        donne : [’3.1’, ’3.14’, ’3.142’, ’3.1416’, ’3.14159’]

**Range syntaxe**: ``range(0,10,2)`` paramètres : debut, fin,pas

**slice**::

    Slice
        L[4:16]
            prend tous les termes de 4 à 15
                terme de droite exclu
                formée des éléments L[k] où k vérifie i≤k<j
        [-4:]
            permet d'avoir les 4 dernier items d'une liste
            C'est vrai aussi pour les chaine de caractères
                texte[-1] permet d'avoir le dernier caractère
        [:5]
            les 5 premiers
        [5:]
            Du 5 ième à la fin
        [4:24:3]
            de 4 à 23 par pas de 3
        [::-1]
            retourne la liste
            s == s[::-1]
                détection de palindrome ;-)
                ça doit être bien utile

**any et all** sur une liste

any peut servir à faire un OU : ``any([1,0,1,0,1])``

all peut servir faire un ET : ``all([1,0,1,0,1])``

.. WARNING::

    all retourn vrai sur une liste vide

Any et all sont des fonction Python qui s'appliquent sur des itérables (pas forcément des listes)

::  

    bit bise
        N << nbits tout simplement
    tri avec la fonction sorted
        Il s'agit d'une fonction <strong>builtin</strong>, c'est-à-dire qu'elle est disponible d'office dans Python sans avoir besoin d'importer quoique ce soit. 
        accepte des arguments : keys et order
            sorted(etudiants, key=lambda etudiant: etudiant.age, reverse=True)
            remarquer le paramètre de key qui attend une fonction et lambda
        Module operator
            Le module operator propose les fonctions itemgetter et attrgetter qui peuvent être très utiles en tant que fonction clés, si on veut trier une liste de tuples ou une liste d'objets selon un attribut ;
        une autre façon de trier est d'utiliser la méthode sort de la clas list


Aficher un dictionnaire ligne à ligne
----------------------------------------------------------------------------------------------------

        for k,v in d.items():     print("{} : {}".format(k,v) )

Multiplication de liste
----------------------------------------------------------------------------------------------------
si x est une liste : x * 5 donne une liste qui recopie 5 fois la liste x::

    [1,2] * 5 donne [1,2,1,2,1,2,1,2,1,2]
    mais [ [1,2] for i in range (3)] donne une liste de 3 listes [[1, 2], [1, 2], [1, 2]]

.. index::
    pair: Python; byte
    pair: Python; bytearray

byte et byarray
----------------------------------------------------------------------------------------------------
::

    byte est immutable
    bytearray est la version mutable
    byte(array).fromhex('ABF0 F623').hex('-')
    doc pdf <../03-Cours_Docs/programmation/Python/python-3.9.0-docs-pdf-a4/docs-pdf/library.pdf>
    bytearray.extend(autre bytearray)
        ou +=
    list(bytearray) donne une liste de nombre
    bytearray(list)
    byarray(int.to_bytes(4, byteorder='big') )

Sur les modules, package...
----------------------------------------------------------------------------------------------------

::

    savoir si un package est importé
        dir()
    install package
        dans : C:\Python34\Scripts
            commande pip
                pip install C:\MountWD\00-Outils\06-ConceptionDeveloppement\Python\six-1.9.0-py2.py3-none-any.whl
    diff entre import os et from os import *
        dans le premier on est obligé de mettre os.fonction()
        dans le second cas les fonctions font parties de l'espace de noms courant.
        Mais quand il s'agit d'un package avec des sous package ?
            from PyQt5.QtWidgets import QApplication,QWidget
                Par cette instruction on greffe QApplication et QWidget à l'espace de nom local ci bien que l'accès à leur élémentsera un peu plus court au lieu de PyQt5.QtWidgets.QApplication.styleSheet() on écrira QApplication.styleSheet()
                on pourrait aussi faire import PyQt5.QtWidgets.QApplication as QApp et faire QApp.styleSheet
            différence entre ces 2 syntaxes
                from serial.tools import list_ports
                    greffe list_ports sur l'espace de nom local
                    list_ports.comports()
                    si on veut greffer tout le contenu de lit_ports sur l'espace de nom loval on fait
                        from serial.tools.list_ports import *
                import serial.tools.list_ports
                    utilisation de la seule fonction de list_ports
                        serial.tools.list_ports.comports()
                    Cette instruction import également serial et tools
        import packageName
            n'importe que l'espace de nom : packageName et le contenu de __init__.py
    force import
        essayer reload(module)
        import importlib
        importlib.reload()


Sur Les fichiers
----------------------------------------------------------------------------------------------------
::

        __file__
            se dit dunder file ;-)
        os.path.dirname(__file__)
            dans le même style:
            os.path.join(dir, 'data', filename)
                dans la doc de reference library.pdf <../03-Cours_Docs/programmation/Python/python-3.9.0-docs-pdf-a4/docs-pdf/library.pdf>
                    chapitre "FILE AND DIRECTORY ACCESS"

Ouvrir un fichier avec with:

.. code:: python
            
    try:
        with open(fIn, 'r') as f:
            file_content = f.read()       
            print "read file " + fIn    
        if not file_content:       
            print("no data in file " + fIn)       
            pass  
        except IOError as e:    
            print("I/O error({0}): {1}".format(e.errno, e.strerror) )

Autres astuces
----------------------------------------------------------------------------------------------------
::

    event driven dans Tkinter
        on peut ajouter des event grace aux méthodes communes
            ok mais ? comment
    copie d'objets
        soit:
    obj_a = [1, 4, 5]
    obj_b = obj_a
                obj_b n'est pas une copie de obj_a
                    les 2 référence le même objet
                alors que dans :
    obj_b = list(obj_a)
                    obj_b est bien une recopie de obj_a
                on peut utilisé aussi le slicing pour réaliser une vraie copie
                    a=b[:]
        Initialisation multiple
            c'est pas a,b,c = 0
            c'est a=b=c=0
            Par contre attention avec les liste
                A=B=C=[1,2,3]
                une seule liste existe et A B et C en sont des alias
        Fonctions : object classique en python
            >>> def add(x, y):
    ...     return x + y
    >>> def sub(x, y):
    ...     return x - y
    >>> def apply(func, x, y): # 1
    ...     return func(x, y) # 2
    >>> apply(add, 2, 1) # 3
    3
    >>> apply(sub, 2, 1)
    1
    
        operateur ternaire <https://python.developpez.com/cours/DiveIntoPython/php/frdiveintopython/power_of_introspection/and_or.php>
            particularité des opérateur and et or
        
        permutter 2 varibles
            a,b = b,a
        Connaître son environnement
            object os.environ
                object iterable
                on peut écrire : os.environ['PATH']
                    retorune une chaine
        Les décorations d'un script exécutable:
            # -* coding : Latin-1 -* import os #... os.system("pause")
            Mettre fenêtre en pause
                import os
    ....
    os.system("pause")
            if __name__ == "__main__":         #code à executer
            #! /usr/bin/env python3 # -*- coding: utf8 -*-


Ctrl C
----------------------------------------------------------------------------------------------------
.. code:: python

    #!/usr/bin/env python
    import signal
    import sys

    def signal_handler(sig, frame):
        print('You pressed Ctrl+C!')
        sys.exit(0)

    signal.signal(signal.SIGINT, signal_handler)
    print('Press Ctrl+C')
    signal.pause()

Trouvé sur `stackoverflow.com How do I capture SIGINT in Python?`_

.. _`stackoverflow.com How do I capture SIGINT in Python?` : https://stackoverflow.com/questions/1112343/how-do-i-capture-sigint-in-python

autre façon meilleur et testée sur projet IOTEps:

.. code:: python

    from threading import Event

    exit = Event()

    def main():
        while not exit.is_set():
        do_my_thing()
        exit.wait(60)

        print("All done!")
        # perform any cleanup here

    def quit(signo, _frame):
        print("Interrupted by %d, shutting down" % signo)
        exit.set()

    if __name__ == '__main__':

        import signal
        for sig in ('TERM', 'HUP', 'INT'):
            signal.signal(getattr(signal, 'SIG'+sig), quit);

        main()

Sur `Stackoverflow break/interrupt a time.sleep() in python`_

.. _`Stackoverflow break/interrupt a time.sleep() in python` : https://stackoverflow.com/questions/5114292/break-interrupt-a-time-sleep-in-python





Python2 to 3
----------------------------------------------------------------------------------------------------

.. index::
    single: Python; 2 to 3

`Cheat Sheet: Writing Python 2-3 compatible code`_

.. _`Cheat Sheet: Writing Python 2-3 compatible code` : http://python-future.org/compatible_idioms.html


.. index::
    pair: Python; Time

====================================================================================================
Time
====================================================================================================
package standard (pas besoin de pip install)

Construct a file name with time:

.. code:: python

    from time strftime
    filename= "bprefixe_" + strftime("%Y%m%d-%H%M%S") + ".txt"


====================================================================================================
I2C
====================================================================================================
En pré-ambule hors Python::

    sudo apt-get install i2c-tools
    sudo i2cdetect -y 1

ça sent bon la Raspberry pi ;-)

2 façon de faire smbus ou mieux `smbus2`_ est compatible python 3.x::

    pip install smbus2

    from smbus2 import SMBus

Sur `Pypi smbus2`_
        
et `Quick2wire en Python3`_


.. _`smbus2` : https://github.com/kplindegaard/smbus2

.. _`Pypi smbus2` : https://pypi.org/project/smbus2/

.. _`Quick2wire en Python3` : https://github.com/quick2wire/quick2wire-python-api


Wiring pi
----------------------------------------------------------------------------------------------------
C'est une librairie C non Python cf.

====================================================================================================
PySerial
====================================================================================================
pyserial

`Pas de doc pdf seulement doc en ligne`_ mais un très bon readthedoc à noter que la doc sur 
pythonhosted.org est identique.

pySerial includes a small console based terminal program called Miniterm. It can be started with::

    python -m serial.tools.miniterm <port name> (use option -h to get a listing of all options).

import serial et pas pyserial

Utilisation de la classe Serial du module serial::

    ser=serial.Serial()
    ser.baudrate=19200
    ser.port='COM4'
    ser.open()

    ser.inWaiting() :caractères en attente de réception

**Astuce**::

    ser=serial.Serial()
    ser (dans la console python) permet de voir les paramètres et l'état ouvert/fermé
    Ecrire une chaîne ser.write( "texte".encode() )

On peut aussi donner tous les paramètres d'un coup au constructeur Serial. 
Voir `la doc short intro`_

`Frames and protocols for the serial port - in Python`_

.. _`Pas de doc pdf seulement doc en ligne` : https://pyserial.readthedocs.io/en/latest/pyserial.html

.. _`Frames and protocols for the serial port - in Python` : http://eli.thegreenplace.net/2009/08/20/frames-and-protocols-for-the-serial-port-in-python

.. _`la doc short intro` : https://pyserial.readthedocs.io/en/latest/shortintro.html

====================================================================================================
Gestionnaires graphiques
====================================================================================================



====================================================================================================
Appli minimum (template)
====================================================================================================
Construire ou récupérer un set de template. Appli mini en version avec objet/sans objet avec/sans
Tkinter au total 4 templates.

J'ai déjà un template avec Qt dans::
    
    C:\MountWD\Donnees\ODJ\008_iao_wrk\Python\experimentations\appliMiniPyQt

====================================================================================================
Weblinks
====================================================================================================

.. target-notes::