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
Pourquoi les gens aiment Python
====================================================================================================
Parce qu'il est comme ARDUINO, il permet d'arriver simplement et rapidement à un résultat concret.

supprime la nécessité d'apprendre un IDE

Python c'est 31 mots clé !


====================================================================================================
Docs
====================================================================================================
`La librairie standard`_

.. _`La librairie standard` : https://docs.python.org/3/library/index.html


====================================================================================================
Elements de langages
====================================================================================================

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
**Création**::

    toto = [1, 5, "tutu", 16.9, (12,3), ["Pierre", "05.12.34.56.78"]]
    toto = list([14,5,12])

Eléments de syntaxe: les crochets.

**L'intérêt**::

    >>> seasons = ['Spring', 'Summer', 'Fall', 'Winter']
    >>> list(enumerate(seasons))
        permet de créer une nouvelle liste avec des commandes !

**Ajout**::

    maList.append(nvlElement)
    attention pas de valeur de retour. Travaille directement sur maList
    maList.insert(6, "titi")
    maList.extend(autreListe)

**Suppression**::
    maList.remove("tutu")
    ou del maList[3]

Elle peuvent être utilisées en pile ou en queue cf. <https://docs.python.org/3.1/tutorial/datastructures.html>

Grace à pop pour les piles et popleft pour les files d'attente

**test d'appartenance**::

        if variable in maListe:
            instruction in !

.. warning:: attention à la copie de liste ne copie que le nom (l'adresse) pas les données.

Mais on peut utiliser les compréhensions de listes::

    list2 = [x for x in list]
    ou plus simplement list2 = list(list1)

.. index::
    pair: Python;  Compréhension de liste

**Compréhension de listes** ou listes en intension

C'est assurément un des grandes forces de Python. L'idée est de créer un liste en une seule ligne
Voir `les comprehensions de liste sur Sam et Max`_

.. _`les comprehensions de liste sur Sam et Max` : http://sametmax.com/python-love-les-listes-en-intention-partie/


.. code::

        [expression for element in sequence]
        moyen de filtrer les listes
            mais pas que
            [expression for element in sequence if condition]
        List comprehensions provide a concise way to create lists from sequences. Common applications are to make
    lists where each element is the result of some operations applied to each member of the sequence, or to create a
    subsequence of those elements that satisfy a certain condition.

    exemples

    [nb * nb for nb in liste_origine]
        c'est en ça que python devient for (on parcours la liste en une seul ligne. L'astuce est de créer une nouvelle liste
        [nb for nb in liste_origine if nb % 2 == 0]
            encore plus fort
        [str(round(355/113, i)) for i in range(1, 6)]
            donne : [’3.1’, ’3.14’, ’3.142’, ’3.1416’, ’3.14159’]
        ou encore:
            [x*y for x in vec1 for y in vec2]

**Remarque** : le for element in sequence est le même que dans la syntaxe d'une boucle for.
On peut considérer la compréhension de liste comme une boucle for condensée.

**Astuce** lire les compréhension de liste de la droite vers la gauche.

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

enumerate
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

`Pas de doc pdf seulement doc en ligne`_

pySerial includes a small console based terminal program called Miniterm. It can be started with::

    python -m serial.tools.miniterm <port name> (use option -h to get a listing of all options).

import serial et pas pyserial

Utilisation::

    ser=serial.Serial
    ser.inWaiting() :caractères en attente de réception

`Frames and protocols for the serial port - in Python`_

.. _`Pas de doc pdf seulement doc en ligne` : http://pyserial.sourceforge.net/index.html

.. _`Frames and protocols for the serial port - in Python` : http://eli.thegreenplace.net/2009/08/20/frames-and-protocols-for-the-serial-port-in-python

====================================================================================================
Gestionnaires graphiques
====================================================================================================


====================================================================================================
A revoir
====================================================================================================

====================================================================================================
Weblinks
====================================================================================================

.. target-notes::