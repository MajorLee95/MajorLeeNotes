.. index::
    single: Python

++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
Python (mes notes)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

:Auteur: J.Soranzo
:Date: Août 2020
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


====================================================================================================
Elements de langages
====================================================================================================
Notations
====================================================================================================
- Notation hexa : C'est 0x33
- Binaire : 0b
- Octal : 0o

Long integer 123L

Code sur plusieurs lignes c'est avec le caractères \


.. index::
    pair: Python;  Tuple

Tuples
====================================================================================================
Ce sont simplement des listes non modifiables syntaxe : 
() à l d [] par rapport à la syntaxe d'une liste.

.. index::
    single: Python;  Liste

Listes
====================================================================================================
Toutes les méthodes de list::

    >>> listMethode[listMethode.index('clear'):listMethode.index('sort')]
    'clear', 'copy', 'append', 'insert', 'extend', 'pop', 'remove', 'index', 'count', 'reverse'

**Création**::

    toto = [1, 5, "tutu", 16.9, (12,3), ["Pierre", "05.12.34.56.78"]]
    toto = list([14,5,12])
    truc = list() #pour une liste vide
    ou encore troc = []

Eléments de syntaxe: les crochets.

**L'intérêt**::

    >>> seasons = ['Spring', 'Summer', 'Fall', 'Winter']
    >>> list(enumerate(seasons)) #liste de tuples (index, éléments)
        permet de créer une nouvelle liste avec des commandes !

**Ajout**::

    maList.append(nvlElement)
    attention pas de valeur de retour. Travaille directement sur maList
    maList.insert(6, "titi")
    maList.extend(autreListe)

**Accès**
    Pour accéder à un élément : malist[indice] indice commence évidement à 0
    Pour accéder à plusieurs élément consécutifs : malist[x:y]


**Suppression**::
    maList.remove("tutu")
    malist.pop() ou maList.popleft()
    ou del maList[3]

**pile et queue**
Elle peuvent être utilisées en pile ou en queue cf. <https://docs.python.org/3.1/tutorial/datastructures.html>

Grace à pop pour les piles et popleft pour les files d'attente.

insert(0 , item) et pop() : pour les Quelques

append() et pop() : pour les piles ou insert(0, item) et pop(0) semble moins efficace 
(faut tout décaller)

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
    ou encore lsit2=list1.copy()

.. index::
    pair: Python;  Compréhension de liste

**Compréhension de listes** ou listes en intension

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

Cela est réservé au paramètres non mommés et on peut combiner des paramètre et une liste.
La liste doit se trouver en dernier ainsi que des parmaètres nommés qui se trouveront après.



**enumerate**
Voir `Enumerate`_

.. index::
    pair: Python;  Dictionnaire

Dictionnaires
====================================================================================================
`Doc officielle sur les dictionnaires`_

.. _`Doc officielle sur les dictionnaires` : https://docs.python.org/3.1/tutorial/datastructures.html#dictionaries

Mot clé : dict, création: maVar = dict()

Eléments de syntaxe: les accolades et les :

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
                Reste ecrase 234.

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
====================================================================================================
C'est un mot clé et une fonction qui retourne un tuple(indice, valeur) et qui s'applique à tous
les itérators.

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
====================================================================================================
Syntaxe::

    def fonctionName(parametres, param = defValue) :
        return a, b, c,d

Les fonction peuvent retourner plusieurs valeurs.

Pas de surcharge

.. index::
    pair: Python;  Lambda

**fonction lambda** ? f = lambda x: x * x

Intérêt ? Ecrire du code plus concis.

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

Une liste peu devenir paramètres d'une fonction, Achement puissant::

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
====================================================================================================
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
    dns le premier on est obligé de mettre os.fonction()
    dns le second cas les fonctions font parties de l'espace de noms courant.
    Mais quand il s'agit d'un package avec des sous package
        from PyQt5.QtWidgets import QApplication,QWidget




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
====================================================================================================
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
====================================================================================================
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
    Simple: Python; Fichiers

Les fichiers
====================================================================================================
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
soit elle. J'ai lu un post qui disait de regrouper ses variables dans une liste avant de les
sauvegarder

.. index::
    pair: Python; Objets



Les objets
====================================================================================================
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

    Attention : var = nomclasse ne crée pas d'intance !!!
    var = nomClasse() oui

constructeur::

        def __init__(self, var1, var2...)
            # double underscore init doubleunderscore
            self.attribut1 = var1...

        le constructeur est considéré comme une méthode spéciale au même titre que __dict__
        est un attribut spécial

Méthodes et self::

    on peut appeler une méthode depuis l'objet inctancieé ou depuis sa classe
        a = objet()
    a.methode(autreVar)
    ou objet.methode(a, autreVar)


Ceci provient du fait que les méthdes ne sont pas recopiées dans chaque objet instancé seulement
les attributs sont différents

Méthodes commence toutes avec self comme premier parmètre. Sauf les **méthodes statiques** et 
les **méthodes de classe**

.. index::
    pair: Python; property

**Getteurs et setteurs**: bien que la notion de private n'existe pas, on peut, grace au mot clé 
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

Autre façon de déclarer les getteurs et setteurs::

    def _width(self):
        return self.__width
    def _setWidth(self, width):
        # Perform some computation
        self.__width = width
    width = property(fget=_width, fset=_setWidth)
    #on nottera le jeu des doubles __ dans self.__width et sa disparition dans width = property

Property permet de redéfinir un attribut en lui allouant des acesseur et mutateur. Cela permet 
de redéfinir le comportament des attributs sans casser le code utilisateur.

width est redéfini alors qu'à l'extérieur on fait tjrs objet.width

Autre façon de transformer une méthode en propriété: grâce au décorateur **@property**::

    class Position:
    def __init__(self, longitude_deg, latitude_deg):
        self.longitude_deg = longitude_deg
        self.latitude_deg = latitude_deg

    @property
    def longitude(self):
        return self.longitude_deg * math.pi / 180

    Utilisation : position.longitute

.. index::
    pair: Python; Méthode spéciales

**Les méthodes spéciales**:  elles sont encadrées par __

Il en existe pour surcharger la pluspart des opérateurs::

    __add__ pour +
    __gt__ pour > 
    __mul__ pour *
    ...
    +=

La liste complète est énorme <https://www.mindmeister.com/fr/10510492/python-underscore>

Quelques unes parmis les plus intéressantes::

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

L'idée est créer des classe dynamiquement c'est à dire pendant l'éxécution. 
Fonctionnalité très avancées selon moi




Itérateur & générateur
====================================================================================================

Un itérateur est avant tout une classe qui va être chargé de parcourir l'objet conteneur
: cf. `opencs chapitre sur les boucles for`_

.. _`opencs chapitre sur les boucles for` : https://openclassrooms.com/fr/courses/235344-apprenez-a-programmer-en-python/233261-decouvrez-la-boucle-for


L'itérateur est créé dans la méthode spéciale __iter__ de la classe

Si on veut créer son propre itérateur pour sa propre classe, cela sinifie qu'il faudra créer 
une nouvelle classe dont une instance est retournée pat __iter__.

Donc en général __iter__ fait un ``return monIterator(self)``

L'itérateur a une méthode spéciale __next__. next() ou __next__ lève l'éxception StopIteration 
en fin d'itération.

Il y a 2 fonctions spéciales python associées à ces méthodes : iter() et next().

Un **générateur** est une fonction (ou méthode) qui contient le mot clé spécial yield

`Doc python sur les generator`_

.. _`Doc python sur les generator` : https://docs.python.org/3/glossary.html#term-generator
        
C'est un moyen plus simple de créer et de manipuler des itérateurs

L'avantage du générateur est qu'il n'est pas besoin de créer une class itérateur ni de méthode
__next__ ni de lever l'éxception de fin

Utilisation classique ::

    iter( monGenerator() )
    on peut créer des fonctions générateur indépement de toute classe
        exemple : intervalle(5, 10) renvoi des nombre de 6 à 10

    Les générateurs accepte des co-routines très puissant
        méthodes : .close() et .send()
            y a pas restart

Tout est sur openclassromm, `chapitre sur les boucle for`_

.. _`chapitre sur les boucle for` : https://openclassrooms.com/fr/courses/235344-apprenez-a-programmer-en-python/233261-decouvrez-la-boucle-for#/id/r-233202

Il s'agit d'une fonction très avancée dans leur création.

====================================================================================================
Astuces
====================================================================================================

====================================================================================================
I2C
====================================================================================================

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
A revoir
====================================================================================================
`Scrapy`_  : permet de "grater" des page web

.. _`Scrapy` : https://doc.scrapy.org/en/1.2/intro/overview.html

`Python Code Quality: Tools & Best Practices`_

.. _`Python Code Quality: Tools & Best Practices` : https://realpython.com/python-code-quality/

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