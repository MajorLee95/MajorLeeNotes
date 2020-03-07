++++++++++++++++++++++++++++++++
Sphinx
++++++++++++++++++++++++++++++++

:Auteur: J.Soranzo
:Date: Octobre 2019
:Societe: VoLAB
:Entity: VoRoBoTics

.. contents::

.. |clearer|  raw:: html

    <div class="clearer"></div>

.. index::
    pair: Sphinx; Documentation
    

======================================
Sphinx pour la documentation
======================================

.. image:: images/sphinxlogo.jpg
   :scale: 100 %
   :alt: alternate text
   :align: left

|clearer|

Voici mon utilisation de Sphinx !

Pourquoi ?
======================================
J'ai longtemps cherché un bon outil de documentation.

Quels sont mes critéres ?

A compléter.

    
.. index::
    pair: Doc-O-Matic; Documentation
    
Doc-O-Matic
======================================
Je le met ici mais je créerai un article plus tard quand j'aurai regardé de plus près

Oui mais non parce que c'est payant ! Même la version de base.

`site Doc-O-Matic`_

.. _`site Doc-O-Matic` : https://www.doc-o-matic.com/en/index.html

================================
Doc officielle
================================
`Site officiel Sphinx`_

.. _`Site officiel Sphinx` : https://www.sphinx-doc.org/en/master/index.html



================================
Au VoLAB
================================

Méthode Pierre: `voir sur son journal de manip`_

.. _`voir sur son journal de manip` : https://poltergeist42.github.io/JDM/DocUtils_RST_Sphinx.html

Que je complèterais par:

#. Créer le répertoire du projet
#. Créer à l'intérieur un répertoire 'projet' et un autre 'webdoc'
#. Dans projet créer \_01-userDoc se placer dedans pour lancer sphinx-quickstart
#. Selon qu'on est sous Linux ou sous Windwos on peut effacer un des 2 make (make.bat pour Windwos)

.. NOTE::
    sphinx-quickstart crée automatiquement le répertoire source

Commencer le boulot après.

Retouches de conf.py:

::
   
    master_doc = 'index'
    
    exclude_patterns = ['_build', 'Thumbs.db', '.DS_Store']
    
    html_theme = 'nature'

    html_theme_options = {
        "body_max_width" : "70%"
    }

Retouches de index.rst

::

    Si toctree il y a (ou doit y avoir):
    .. toctree::
       :maxdepth: 2
       :caption: Articles:
       :titlesonly:
    
    Supprimer : * :ref:`modindex` (on fait pas du Python ;-)

.. index::
    single: Sphinx; liens locaux
    single: Sphinx; download

================================
css pas dans gh-pages
================================
Mettre de le fichier .nojekill dans le répertoire source et pas dans le répertoire html ;-)

Ce fichier est utilisé par make html

================================
Liens externe locaux
================================  

directive .. only et role :download:

`Page Sphinx sur download`_

.. _`Page Sphinx sur download` : http://www.sphinx-doc.org/en/master/usage/restructuredtext/roles.html#role-download


Exemple :download:`doc pdf sphinx<sphinx.pdf>`

Autre :download:`utilisation avec un word <exemple_roleDL.docx>`

Quoique après relecture j'ai un gros doute `sur only`_

.. _`sur only` : https://www.sphinx-doc.org/en/master/usage/restructuredtext/directives.html#directive-only


================================
Themes
================================
Recherche d'un thème avec barre de navigation fixe

.. note::

	Ce serait l'option stickysidebar  bar https://www.sphinx-doc.org/en/master/usage/theming.html
	au moins pour le theme classic
    
Le pb est que les options ne sont pas commune d'un thème à l'autre.

testés 
======================================
- PSphinxTheme : dans les premier ! Avec sidebar rétractable 5 colorations fournies. Theme difficile à installer sous Windows !!! Erreur dans setup.py (os supported arch Linux ! )

**guzzle**

Ne support pas body_max_width dommage

.. image:: images/guzzle.jpg
   :width: 300 px
   :align: center

**cloud**

Plutôt pas mal, beaucoup d'option mais je trouve l'écartement entre les lignes de mon header

:Auteur: J.Soranzo
:Date: Octobre 2019
:Societe: VoLAB
:Entity: VoRoBoTics

trop important !

.. image:: images/cloud.jpg
   :width: 300 px
   :align: center

**murray**

Trop blanc mais intéressant pour son menu repliable.
 
A tester 
======================================
- catalystcloud
- rtd Read The Doc https://sphinx-rtd-theme.readthedocs.io/en/stable/installing.html


====================================================================================================
Petits trucs
====================================================================================================

.. index::
    single: Sphinx; Doxylink

Liens Doxygen
====================================================================================================
doxylink : contributed extension

`Doxylink documentation`_

.. _`Doxylink documentation` : https://sphinxcontrib-doxylink.readthedocs.io/en/stable/

----------------------------------------------------------------------------------------------------

.. index::
    single: Sphinx; clearer
    single! Sphinx; Séparateur html

Séparateur html
====================================================================================================
Clearer::

    .. |clearer|  raw:: html

        <div class="clearer"></div>
    _usage : |clearer|
 
Autres astuces difficilement classable 
==================================================================================================== 
7/3/20 J'ai trouvé ce site ou plutot ce MOOT de l'université de Grenoble : 

`ReFlexPro, Univ. Grenoble Alpes`_

.. _`ReFlexPro, Univ. Grenoble Alpes` :  http://espe-rtd-reflexpro.u-ga.fr/docs/sandbox2/fr/latest/syntaxe_sphinx.html#les-bases-de-la-syntaxe-de-sphinx



=========
Weblinks
=========

.. target-notes::


