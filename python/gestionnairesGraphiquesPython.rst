++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
Les gestionnaires graphiques dans Python
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. include:: ../idBlock.rst

:Création: 12/2023
:Maj: 12/2023

.. contents::
    :backlinks: top

====================================================================================================
Gestionnaires graphiques
====================================================================================================
tkinter
----------------------------------------------------------------------------------------------------
Voir fichiers Freeplane. Todo: convertir en rst en cour ci-dessous

pyQt5
----------------------------------------------------------------------------------------------------
Voir fichiers Freeplane. Todo: convertir en rst

Pysimplegui
----------------------------------------------------------------------------------------------------
Voir fichiers Freeplane. Todo: convertir en rst (et encore j'ai jsute mis une ligne pour m'en rappeler)

====================================================================================================
tkInter
====================================================================================================




Docs
----------------------------------------------------------------------------------------------------
::

        Super doc en pdf du site New Mexico Tech <http://infohost.nmt.edu/tcc/help/pubs/tkinter/web/index.html>
            téléchargé <../03-Cours_Docs/programmation/Python/tkinter.pdf>
                on WDD
            C'est surtout la doc de tlc/tk qui est importante
                tkinter est juste un wrapper entre Python et tcl/tk
                Correction 6/7/15, grace à ce doc, la doctcl/tk devient moins nécessaire
                Surtout que la gym du wrapper n'est pas simple
            C'est surtout un ref doc sans exemple
            Chapitre 27 à reconsidérer 6/11/2020
            tkinter rérérence <https://web.archive.org/web/20190524140835/https://infohost.nmt.edu/tcc/help/pubs/tkinter/web/index.html>
                JohnW. Shipman
                Super doc en pdf du site New Mexico Tech
                pdf dans coursEtDoc/programmation/python
                    JohnW. Shipman
        DOC Officielle <https://docs.python.org/fr/3/library/tkinter.html>

Trucs et astuce
----------------------------------------------------------------------------------------------------
Astuce tkInter:

     - Lier un fonction à un bouton par une fonction lambda permet de passer des paramètres à la callback utilisée

::

            Truc rigolo
            tkinter._test()

Outils
----------------------------------------------------------------------------------------------------
::

    Il existe un tkinterdesigner qui se nomme Page
        http://page.sourceforge.net/
        Je l'ai téléchargé et installé (MSI 08/2020)
            redo en 12/07/2022 sur le MSI
            J'ai eu un peu de mal à le lancer
            winpage.bat
                double click dessus
        Cela fonctionne si on suit le tuto du pdf. J'ai juste créé un bouton
            où ?
            Dans le répertoire doc
        Mais je me demande si je ne préfère pas faire à la main !
        le répertoire examples est bien fourni
        s'install directement en c:/page
        essais
            C:\MountWD\Donnees\ODJ\008_iao_wrk\Python\experimentations\tkinter_exemples\pageUiDesigner
                08/2020
            intéressant pour expérimenter des Widget




Structuration
----------------------------------------------------------------------------------------------------
::

    tkinter c'est <https://docs.python.org/3.4/library/tkinter.html#tkinter-modules>
        17 Widgets
            Button
            Canvas
                A canvas is a rectangular area intended for drawing pictures or other complex layouts. On it you can place graphics, text, widgets, or frames.
            Checkbutton
            Entry
            Frame
                A frame is basically just a container for other widgets.
                Frame widgets are a valuable tool in making your application modular. You can group a set of related widgets into a compound widget by putting them into a frame.
            Label
            LabelFrame
            Listbox
            Menu
            Menubutton
            Message
                This widget is similar to the Label widget but it is intended for displaying messages over multiple lines.
            OptionMenu
            Radiobutton
            Scale
            Scrollbar 
            Spinbox
            Text
                Text widgets are a much more generalized method for handling multiple lines of text than the Label widget. Text widgets are pretty much a complete text editor in a window
            +ttk qui
                Redéfini des Wgts et en défini 4 nouvx
                    import tkinter as tk
                    from tkinter import ttk
                    Sauvegarde l'espace de nom de tkinter donc:
                    on utilise la syntaxe ttk.wdg
                                            • Section 31, “ttk.Combobox” (p. 115).
                    • Section 37, “ttk.Notebook” (p. 126).
                    • Section 39, “ttk.Progressbar” (p. 130).
                    • Section 43, “ttk.Separator” (p. 137)
                    Les autres sont mis à la sauce de l'interface graphique de la plateform

            13 sous package ou modules
                import tkinter.messagebox
                import tkinter.filedialog
                PACKAGE CONTENTS
                    colorchooser
                    commondialog
                    constants
                    dialog
                    dnd
                    filedialog
                    font
                    messagebox
                    scrolledtext
                    simpledialog
                    test (package)
                    tix
                    ttk
            Des méthodes communes
                3 gestionnaires de géométrie différents <http://effbot.org/zone/tkinter-geometry.htm>
                    pack
                        .pack() empile les widget sur une colonne centrée les uns aux dessus des autres dans le widget parent
                        .pack(fill=X ) permet de prendre toute la largeur duparentWidget
                            de même avec fill=Y pour la verticale
                        .pack( side = LEFT ) permet d'aligner les wdg depuis la gauche vers la droite
                    grid
                    et place
                        place( x,y )
        Une gestion d'événements


.. WARNING:: tkMessageBox est devenu tkinter.messagebox
    :class: without-title
              
    S'appelle au travers de ses méthode
        messagebox.askyesnocancel(title="Hello", message="coucou")
    Nécessite de faire :from tkinter import messagebox
        (j'ai pas réussi à le faire marcher autrement)

Limitations
----------------------------------------------------------------------------------------------------
::

    Ne supporte pas le multithreading
        génant pour exécuter une tâche périodique
        il y a une méthode applicable à tout widget .after
            chapitre 26 du livre sur tkinter.pdf
            from tkinter import *
            import subprocess
            
            output = subprocess.check_output('sleep 2 ; date', shell=True)
            
            win = Tk()
            f1 = Frame( win )
            tp = Label( f1 , text='Date: ' + str(output[:-1]))
            f1.pack()
            tp.pack()
            
            def task():
                output = subprocess.check_output('date', shell=True)
                tp.configure(text = 'Date: ' + str(output[:-1]))
                win.after(2000, task)
            win.after(2000, task)
            
            win.mainloop()
            
    le gestionnaire graphique grid à tendance à n'en faire qu'à sa tête pour positionner les objets
    utiliser pack, c'est ce que tout le monde fait ou presque

    Exemple de limitation: une zone de texte n'a pas de scroll bar automatique (on est obligé de l'ajouter à part)
        non voir les autres modules contenu dans la package
    Même avec ttk, il reste des manques.

Gestionnaires de geom
----------------------------------------------------------------------------------------------------
::

    Il y a 3 gestionnaires de géométrie <#4omhr2i30b381akekijnvatgo6>
        To display it, you need to call a special method: either grid, pack (which we’ve used in all examples this far), or place.
        pack()
            The pack() method mainly uses a packing algorithm in order to place widgets in a Frame or window in a specified order.  This method is mainly used to organize the widgets in a block.
            3 paramètres seulement fill, expand, side
            En vrai, il y en a un peu plus
                help (tk.Button.pack)
        grid()
            The most used geometry manager is grid() because it provides all the power of pack() function but in an easier and maintainable way.
            You can easily specify the location of a widget just by calling grid() function and passing the row and column indices to the row and column keyword arguments, respectively
        place()
            This method basically organizes the widget in accordance with its x and y coordinates. Both x and y coordinates are in pixels
                Thus the origin (where x and y are both 0) is the top-left corner of the Frame or the window
                Thus, the y argument specifies the number of pixels of space from the top of the window, to place the widget, and the x argument specifies the number of pixels from the left of the window
            geom manager utilisé par l'utilitaire Page
        site <https://www.studytonight.com/tkinter/python-tkinter-geometry-manager>

Petite recette de cuisine
----------------------------------------------------------------------------------------------------
::

    fen = tkinter.Tk()
        avec un T majuscule
        Dans cette fenêtre on peut alors mettre des Widgets
        Comme un Canevas
            can = tk.Canvas(fen, width = 400, height= 200, bg = 'ivory')
            can.pack()
        ou un Frame
            Dans le frame on peut mettre des button un autre Frame...
        ou un Button

Snippet pour un bouton::

    bout = tkinter.Button(fen, text='le text du bouton', command = fen.destroy)
        à noter qu'à la fin on ne met pas de paranthèse à la méthode destroy, on passe son adresse à la fonction
        à la place de destroy, on peut utiliser quit
            quit permet de quitter le gestionnaire d'événement mais ne détruit pas la fenêtre
            Cette méthode sert à fermer (quitter) le réceptionnaire d’événements (mainloop) associé à cette fenêtre.
        et surtout après bout.pack()
            ou bout.grid(row=i, column=j)


Canvas versus frame
****************************************************************************************************
A **Frame** is designed to be a container for other widgets. It really doesn't do anything but provide 
a border and color, and to collect a set of widgets into a logical group.

A **Canvas** is something that can act as a container for other widgets (as can just about any widget), 
but it also has features that let you draw circles, lines, rectangles, and other objects on it.

A **Canvas** can also be scrolled, whereas a frame cannot.


Appli minimum
----------------------------------------------------------------------------------------------------
::

    version non objet
        reste à faire...

    version objet
        2 façons de faire rencontrées lors de mes recherche
            façon opneclassroom
                on dérive la classe Frame
                fenetre = Tk() 
                
                interface = Interface(fenetre)  
                interface.mainloop() 
                interface.destroy()

            façon Object-Oriented Programming in Python <https://python-textbok.readthedocs.io/en/1.0/index.html>
                on part de rien
                root = Tk() 
                my_gui = MyFirstGUI(root) 
                root.mainloop()

            Il me semble que la différence est dans l'utilisation
                Euh non finalement c'est pareil
                Il y a une légère subtilité
                    qui contient mainloop()
                    Dans un cas openCr c'est interface et la fenêtre en est un fille
                    Dans l'autre cas root reste root

Le reste à traiter
----------------------------------------------------------------------------------------------------
::
    
            import tkinter ou from tkinter import*
                ou encore import thinker as tk
                    ensuite on fait systematiquement tk.
            http://fsincere.free.fr/isn/python/cours_python_tkinter.php





            Event
                connection
                    p157 du pdf
                        Chapitre 54
                        tkinter.pdf <file:/C:/MountWD/Donnees/008_iao_wrk/03-Cours_Docs/programmation/Python/tkinter.pdf>
                    ie binding
                        w.bind()
                        w.bind_class()
                        w.bind_all()
                    La description de l'événnement est faite grace à une séquence texte
                        chaine donc ''
                        La sequence peut contenir plusieurs pattern qui doivent tous être valident pour déclencher le handler (fonction)
                        Chaque pattern est entouré de <...>
                            donc de base '<...>'
                            <[modifier-]...type[-detail]>
                                types
                                    Button
                                    KeyPress
                                    FocusIn
                                    ...
                                Modifiers
                                    Seulement 7
                                    Alt
                                        ex : Alt-KeyPress-h
                                        <Alt-KeyPress-h>'
                                    Shift
                                    Any
                                    ...
                                -détail
                                    Par exemple le nom des touches
                                        cf p158 du pdf
                                    num bouton souris
                                You can use shorter forms of the events.
                                    Quelle est la règle exacte ????
                revoir les méthodes commune dédiées aux events.
                    page 99 du pdf sur tkinter

            Applimin

            exemples
                tous les exemples dans le dossier \Python\experimentations\tkinter_exemples sont en code sequentiel
                il y a un exemple Oo à la fin du chapitre openclassroom
                https://vincent.developpez.com/cours-tutoriels/python/tkinter/apprendre-creer-interface-graphique-tkinter-python-3 <https://vincent.developpez.com/cours-tutoriels/python/tkinter/apprendre-creer-interface-graphique-tkinter-python-3/#LVIII>
                    pas Oo
                https://python-textbok.readthedocs.io/en/1.0/Introduction_to_GUI_Programming.html
                    Oo

====================================================================================================
From mindmap (le reste)
====================================================================================================
pyWx::

        PyWx
            ne supporte pas 3.x
                est resté en 2.7
            WxPy d'ailleurs

pyQt::
    
        pyQt
            Workflow
                Installation
                    un .exe
                        j'ai des installateur qui date de 2014
                            v5.3.1
                    en 2020, il y a un dépôt <https://pypi.org/project/PyQt5/#files>
                        v5.13.0
                    Pour vérifier l'installation
                        >>> from PyQt5.QtWidgets import QApplication, QLabel >>> app = QApplication([]) >>> label = QLabel("Hello World!") >>> label.show() >>> app.exec_()
                PyQt is able to generate Python code from Qt Designer.
                    Mais Qt Designer ne fait pas partie du Pack
                        si justement !!!
                        où ?
                        prendre soit d'installer pyQT5.tools (pip install)
                        Ensuite on le trouve dans : repertoirInstallPython\Lib\site-packages\pyqt5_tools\Qt\bin
                    Comment ?
                        PyQt5 UI code generator 5.3.1
                        en ligne de commande !!! pyuic5
                Avec Qt Designer
                    On design graphiquement l'interface
                        Cela produit un fichier .ui
                        Avec QtDesigner qui produi un fichier .ui
                    On converti le fichier ui en fichier python avec
                        pyuic5.bat
                            dans C:\Python34\Lib\site-packages\PyQt5
                    Le mieux est de copier le fichier pyuic5.bat dans le répertoire de travail
                        pas nécessaire PATH redéfini
                    Commande : pyuic5 toto.ui -o toto.py [-x -i 0]
                        x genere code de fin
                        i 0 remplace les espace par des tab
                Ne reste plus qu'à mettre en place le cannevas pour l'application
                    appli min
                        Version non objet
                            #!/usr/bin/env python
    # coding: utf-8
    
    from PyQt4 import QtGui, QtCore
    import sys
    
    app = QtGui.QApplication(sys.argv)
    hello = QtGui.QPushButton("Hello World!", None)
    hello.show()
    app.exec_()
                        Version objet Qt
                            grace à pyuic5 on peut avoir automatiquement un semblant d'appel commutateur -x
                                if __name__ == "__main__":
        import sys
        app = QtWidgets.QApplication(sys.argv)
        FindAndReplaceDlg = QtWidgets.QDialog()
        ui = Ui_FindAndReplaceDlg()
        ui.setupUi(FindAndReplaceDlg)
        FindAndReplaceDlg.show()
        sys.exit(app.exec_())
                            La création d'une class fille de ui_maBoiteDeDialogue devient alors nécessaire pour ajouter des fonctionnalités/fonctions qui ne sont pas faisables dans QtDesigner
                                Avec 
                                    Les import qui vont bien
                                    la déclaration de la classe fille avec héritage multiple ( QDialog et classe mère ui_...
                                    Avec une fonction __ini__ qui appelle celle de la classe mère (comme pour toute classe fille en python)
                                        role de la fonction super()
                                    lancement également de setupUi()
                                        méthode de la classe fille
                                    Et bien évidement à la fin du fichier un code d'autotest
                                        on peut même y mettre des connection de signaux  et plein de code au besoin
                                        if __name__ == "__main__":
        app = QApplication(sys.argv)
        form = maBoiteDeDialog()
        form.show()
        app.exec_()
                                Exemples
                                    from PyQt5.QtCore import *
    from PyQt5.QtGui import *
    from PyQt5.QtWidgets import *
    import ui_maBoiteDeDialogue
    
    class classFifille(QDialog,
            ui_maBoiteDeDialogue.Ui_maBoiteDeDialogue):
    
            def __init__(self, text, parent=None):
                super(classFifille, self).__init__(parent)
            self.setupUi(self)			
                                    if __name__ == "__main__":
        import sys
    
        text = """US experience shows that, unlike traditional patents,
    software patents do not encourage innovation and R&D, quite the
    contrary. In particular they hurt small and medium-sized enterprises
    and generally newcomers in the market. They will just weaken the market
    and increase spending on patents and litigation, at the expense of
    technological innovation and research. Especially dangerous are
    attempts to abuse the patent system by preventing interoperability as a
    means of avoiding competition with technological ability.
    --- Extract quoted from Linus Torvalds and Alan Cox's letter
    to the President of the European Parliament
    http://www.effi.org/patentit/patents_torvalds_cox.html"""
    
        def found(where):
            print ("Found at %d" % where)
    
        def nomore():
            print ("No more found")
    
        app = QApplication(sys.argv)
        form = FindAndReplaceDlg(text)
        # form.connect(form, SIGNAL("found"), found)
        form.found.connect(found)
        # form.connect(form, SIGNAL("notfound"), nomore)
        form.nofound.connect(nomore)
        form.show()
        app.exec_()
                            J'ai créé un modèle d'appli mini dans 
                                C:\MountWD\Donnees\008_iao_wrk\Python\experimentations\appliMiniPyQt <file:/C:/MountWD/Donnees/008_iao_wrk/Python/experimentations/appliMiniPyQt>
                Ce qui sommes toute est un wokflow assez lourd
                    on s'éloigne vite de la simplicité inspirée par Python
                Au moins celui là il fonctionne
                    de plus grâce à Qt Designer on peut plus facilement exploiter la richesse de widget de Qt
            La doc officielle est limité au stric référence guide <http://pyqt.sourceforge.net/Docs/PyQt5/>
                Grosse liste alphabétique des Class
                pas de tuto
                Chapitres utiles
                    Les signaux <http://pyqt.sourceforge.net/Docs/PyQt5/signals_slots.html>
                        Signaux prédéfini sur les objects
                            On peut les connaitre dans QtDesigner
                            Il y a plusieur façon de connecter un signal à un slot
                                QtDesigner ne permet pas de faire la connection entre un signal prédéfini et un handler
                                ou à un handler
                                grâce à la méthode .connect()
                                    doit être hérité de QtObject
                                        QtCore.QObject.connect(self.ui.button_open,QtCore.SIGNAL("clicked()"), self.file_dialog)
                                Connection semi-auto aec le décorateur : @pyqtSlot
                        Signaux utilisateur
                            On défini un signal
                                avec pyqtsignal()
                            On le connect à un handler (un fonction)
                                signal.connect(fonction)
                            En l'émet au moment oportun
                                signal.emit()
                            Exemple
                                from PyQt5.QtCore import QObject, pyqtSignal
    
    class Foo(QObject):
    
        # Define a new signal called 'trigger' that has no arguments.
        trigger = pyqtSignal()
    
        def connect_and_emit_trigger(self):
            # Connect the trigger signal to a slot.
            self.trigger.connect(self.handle_trigger)
    
            # Emit the signal.
            self.trigger.emit()
    
        def handle_trigger(self):
            # Show that the slot has been called.
    
            print "trigger signal received"
    
                quelques uns sur le wiki
                Vite redirigé vers la doc de Qt
                Tutos qui ont l'air intéressant <http://www.rkblog.rk.edu.pl/w/p/extending-pyqt4-text-editor/>
            Conclusion
                Le mécanisme fondamental des signaux et slot est lourd
                    mais très puissant quand il est bien maitrisé
                On est quasiment obligé de travailler en objet
            Fichier ressource .qrc
                stock les images tel les icones cf menu fichier
                nécessite un fichier qrc
                qui se produit grace à Qt Designer
                    
                Ensuite après création, il faut le convertir grâce pyrcc5.exe (comme pour le fichier ui)
            Connecting by slot name <http://pyqt.sourceforge.net/Docs/PyQt5/signals_slots.html>
                fonctionnalité puissante de connection automatiques des signaux de l'interface vers des fonction écrite par le codeur
            versions
                Raspberry pi
                    pyqt4
                        Install PyQt4 for Python 3.4 <https://raspberrypi.stackexchange.com/questions/38843/install-pyqt4-for-python-3-4>
        gtk+
            ne supporte pas 3.x
            Peut être utilisé avec Glade
                Glade is a RAD tool to enable quick & easy development of user interfaces for the GTK+ toolkit and the GNOME desktop environment.
                    RAD Rapid Application Developpement
            on part gtk3
                seulement sous Linux
                puis on se retoruve sur PyGObject aka PyGi <https://wiki.gnome.org/action/show/Projects/PyGObject>
                    et on fini sur une erreur à  l'install
        pygame
            compatible python 3
            ça s'install dans la douleur
                cela l'est déjà sur Rpi (Jessy)
        pysimplegui
            12/05/23
            A revoir

====================================================================================================
Weblinks
====================================================================================================

.. target-notes::