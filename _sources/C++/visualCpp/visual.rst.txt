++++++++++++++++++++++++++++++++
Note concernant Visal C++ 2013 *
++++++++++++++++++++++++++++++++

:Auteur: J.Soranzo
:Date: Octobre 2019
:Societe: VoRoBoTics
:Entity: VoLAB

.. contents:: TdM Visual C++ 2013

.. index::
    single: Programmation; Visual
    single: C++; Visual


======================================
Configuration
======================================




======================================
MFC
======================================

Microsoft Fondation Class (MFC) qu'est-ce dont ?
==================================================

.. index::
    single: Programmation; MFC
    pair: MFC; Visual


est une bibliothèque de classes en C++ encapsulant l'API Win32 (écrite en C) de Windows. Sa première apparition date de 1992
Parmi les inconvénients de la MFC, on trouve:

 - documentation pléthorique, mais pas structurée ;
 - problème de gestion de l’unicode
 - internationalisation dans le code (au lieu d'être une simple option à indiquer)
 - emploi de templates figés qui créent souvent les vues (document - vue) ;
 - utilisation de boucle d'événements (messages) et pas de callback /listener ;
 - surcouche orientée objet (pas objet) permettant d'accéder à l'API windows qui est en C
 - utilisation exclusive de Visual Studio ;
 - Utilisation sans API de la surcouche C++

Bien que .NET soit portable et facile d'accès, MFC reste plus abouti notamment pour Win32 kernel API, DirectX, STL, ATL, (pas ADO). Microsoft supporte la MFC par l'utilisation de wrapper. 
	
on peut créee des projet sous Visual 2013
 - ATL
 - WCF
 - CLR : Common Language Runtime
 - Win32
 - F#

CLR est le nom choisi par Microsoft pour le composant de machine virtuelle du framework .NET
Le CLR est composé des quatre parties suivantes:

 * Common Type System (CTS) ;
 * Common Language Specification (CLS) ;
 * Metadata ;
 * Virtual Execution System (VES).
 
 
.net
Microsoft .net
est le nom donné à un ensemble de produits et de technologies informatiques de l'entreprise Microsoft pour rendre des applications facilement portables sur Internet.

Framework .net

abr. NetFx

un ensemble de bibliothèques de haut niveau

Infrastructure de développement
s'appuie sur la norme Common Language Infrastructure (CLI)


La métode DoDatExchange( CDataExchange* pDX ) et la macro

BEGIN_MESSAGE_MAP(CClasseDeLaBoiteDeDialogue, CDialogEx)

sont les 2 constituants qui lie fonction (ici des méthodes) à des éléments de face avant


Hierarchy chart ! ça fait peur !

`source pour MFC hierachy chart`_

.. _`source pour MFC hierachy chart` : https://docs.microsoft.com/en-us/cpp/mfc/hierarchy-chart?view=vs-2019



`MFC class lib overview`_

.. _`MFC class lib overview` : https://docs.microsoft.com/en-us/cpp/mfc/class-library-overview?view=vs-2019

======================================
Les différentes type d'applications
======================================

A écrire...

=========================
Liaison série
=========================
A écrire...

============================
Web socket
============================

MFC support Win socket 1 et pas Win socket 2

Note annexe sur les sockets hors du monde Windows

Stream sockets (e.g. uses TCP)

Datagram sockets (e.g. uses UDP)

===========================
multitache
===========================
A écrire...

====================================================================================================
Tips
====================================================================================================

.. index::
    pair: MFC; Enter key
    

Déconnecter la touche ENTER du bouton quit
====================================================================================================
`Sur stackoverflow`_

.. _`Sur stackoverflow` : https://stackoverflow.com/questions/17828258/how-to-prevent-mfc-dialog-closing-on-enter-and-escape-keys

::

    When the user presses Enter key in a dialog two things can happen:

    The dialog has a default control (see CDialog::SetDefID()). Then a WM_COMMAND with the ID of this 
    control is sent to the dialog.
    The dialog does not have a default control. Then WM_COMMAND with ID = IDOK is sent to the dialog.
    With the first option, it may happen that the default control has a ID equal to IDOK. Then the
    results will be the same that in the second option.

    By default, class CDialog has a handler for the WM_COMMAND(IDOK) that is to call to CDialog::OnOk(),
     that is a virtual function, and by default it calls EndDialog(IDOK) that closes the dialog.

    So, if you want to avoid the dialog being closed, do one of the following.

    Set the default control to other than IDOK.
    Set a handler to the WM_COMMAND(IDOK) that does not call EndDialog().
    Override CDialog::OnOk() and do not call the base implementation.
    About IDCANCEL, it is similar but there is not equivalent SetDefID() and the ESC key is hardcoded.
    So to avoid the dialog being closed:

    Set a handler to the WM_COMMAND(IDCANCEL) that does not call EndDialog().
    Override CDialog::OnCancel() and do not call the base implementation.

=========
Weblinks
=========

.. target-notes::