++++++++++++++++++++++++++++++++
Mon utilisation de Sphinx
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
Liens externe locaux
================================  

directive .. only et role :download:

`Page Sphinx sur only`_

.. _`Page Sphinx sur only` : http://www.sphinx-doc.org/en/master/usage/restructuredtext/roles.html#role-download


Exemple :download:`doc pdf sphinx<sphinx.pdf>`

Autre :download:`utilisation avec un word <exemple_roleDL.docx>`


================================
Themes
================================
Recherche d'un thème avec bare de navigation fixe

.. note::

	Ce serait l'option stickysidebar  bar https://www.sphinx-doc.org/en/master/usage/theming.html
	au moins pour le theme classic

testés 
======================================
- guzzle : 
- cloud
 
A tester 
======================================
- catalystcloud
- rtd Read The Doc https://sphinx-rtd-theme.readthedocs.io/en/stable/installing.html

 
=========
Weblinks
=========

.. target-notes::


