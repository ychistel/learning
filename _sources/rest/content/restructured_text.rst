Les bases de reStructuredText
*****************************

.. topic:: titre du topic

	**Auteurs** : Richard Jones & David Goodger, traduits par `Philippe Dessus <http://webcom.upmf-grenoble.fr/sciedu/pdessus/>`_

	**Date de création** : Juillet 2016.

	**Date de modification** : |today|.

	**Statut du document** : en travaux.

	**Licence** : Document placé dans le domaine public.

	**Résumé** : Ce document donne les principaux éléments de la syntaxe reST (reStructuredText), utilisée par Sphinx et certains wikis. C'est la traduction quasi-complète de R. Jones, `A ReStructuredText Primer <http://docutils.sourceforge.net/docs/user/rst/quickstart.html>`_, avec des ajouts provenant de D. Goodger, `reStructuredText Markup Specification <http://docutils.sourceforge.net/docs/ref/rst/restructuredtext.html>`_ et D. Goodger `reStructuredText Directives <http://docutils.sourceforge.net/docs/ref/rst/directives.html>`_ et commentés par le traducteur.

	**Voir aussi** : Le Document :ref: `syntaxe_sphinx` peut être lu ensuite.
	
	**Note** : Ces ressources constituent l'un des **kits de pérennisation** du projet `ANR-Idéfi ReflexPro <http://www.idefi-reflexpro.fr>`_ et a bénéficié de son financement. 


Introduction
============

Ce document est une introduction informelle à `reStructuredText <https://fr.wikipedia.org/wiki/ReStructuredText>`_ (reST), qui est un langage de balisage de texte. Le texte reST est interprété (p. ex., par `Sphinx <http://www.sphinx-doc.org>`_) pour produire des documents HTML pouvant être lus par un navigateur. 

Ne pas hésiter à afficher le code source de la page, quand cela est disponible, pour comprendre quelle est la syntaxe utilisée.

L'entité la plus basique est le paragraphe. C'est un bloc de texte séparé par des lignes vides (une suffit). Il faut noter qu'il n'est pas possible d'aller à la ligne à l'intérieur d'un bloc de texte (voir plus loin le non-effet du passage à la ligne). Les paragraphes doivent avoir la même indentation -i.e., être alignés à gauche. Des paragraphes qui sont décalés par rapport aux précédents sont traités comme des citations. Par exemple :

Ceci est un paragraphe, il est plutôt 
court

	Ce paragraphe indenté va être rendu comme un bloc en retrait, idéal pour les citations.

Là on revient à la ligne.

Styles de texte
===============

Dans les paragraphes et autres entités textuelles, il est possible de marquer du texte en *italiques* avec ``*italiques*`` ou en **gras** avec ``**gras**``, ou encore **partielle**\ment ainsi : ``**partielle**\ment``. Ce sont des balises dans le texte (*inline markup*) ; pour le faire .

Pour faire apparaître du texte en police à empattement fixe, utiliser de doubles guillemets : ``texte à empattement fixe`` (justement utilisés pour signaler les commandes reST dans ce document). Noter qu'aucun bidouillage supplémentaire ne peut être fait à l'intérieur de tels guillemets (p. ex., pas d'italiques).

Pour utiliser l'un de ces caractères "spéciaux" dans le texte, il suffit de le faire précéder d'un antislash comme ceci : ``5\*6=30``, qui sera rendu ainsi : 5\*6=30.

Cette astuce est indispensable, par exemple, quand on veut afficher une référence en APA ::

	* Jessor, R. (1993). Successful adolescent development among youth in high-risk settings. *American Psychologist*, *48*\ (2), 117-126.

Sera rendue ainsi :

* Jessor, R. (1993). Successful adolescent development among youth in high-risk settings. *American Psychologist*, *48*\ (2), 117-126.


Astuce
======

Il faut considérer que le balisage en ligne est une forme de parenthésage et qu'il doit être utilisé en tant que tel : immédiatement avant et après le texte que l'on veut marquer (sans insérer d'espaces, ni au milieu d'un mot). 

Listes
======

Les listes d'items sont de trois sortes : énumération, à puces, définitions. Pour toutes ces listes on peut avoir autant de paragraphes et de sous-listes que l'on veut, du moment que le côté gauche de leur paragraphe est aligné avec la première ligne de texte.

Les listes doivent toujours démarrer comme un nouveau paragraphe (après une ligne vide).

Les listes d'énumérations
-------------------------

Concerne les énumérations (nombres, lettres, chiffres romains). Commencer une ligne avec le nombre ou la lettre suivi(e) d'un point, une parenthèse fermante ou entre parenthèses. Les formes suivantes sont reconnues (attention, tous les navigateurs peuvent ne pas rendre ces énumérations de la même manière : mieux vaut les tester) :

1. Nombres

A. Lettres capitales
	et ça peut aller sur plusieurs lignes

	avec 2 paragraphes !

a. lettres minuscules
	
	3. avec une sous-liste démarrant avec un nombre différent.
	4. assurez-vous que les nombres sont corrects !

I. Chiffres romains majuscules

i. Chiffres romains minuscules
    
(1) Encore des nombres

2) Et encore ! 

Les listes à puce commencent indifféremment par un "-", "+", ou "*".

* une liste à puce avec  "*"

  - une sous-liste avec "-"

    + encore une autre sous-liste

  - un autre item

Note : si un paragraphe commence par un signe pouvant être interprété comme un énumérateur, le premier caractère sera précédé d'un anti-slash ::

	\A. Einstein est un gars vraiment très intelligent

est rendu ainsi :

\A. Einstein est un gars vraiment très intelligent

.. liste_definition:

Les listes de définition
------------------------

Au contraire des précédentes, les listes de définition consistent en un terme et la définition de ce terme. Peuvent être utilisées pour un glossaire, un dictionnaire. Le format d'une telle liste est :

Machin
  La définition de machin, indentée. Noter que le terme est automatiquement mis en gras. Le terme doit tenir en une ligne. la définition tient en un ou plusieurs paragraphes, indentés de la même manière par rapport au terme. Ne pas sauter de ligne entre le terme et sa définition.


Préformatage (code informatique)
================================

Pour inclure un paragraphe de texte préformaté, terminer le bloc par "::". Le bloc préformaté qui suivra sera terminé quand le texte reviendra au même niveau d'indentation que le texte juste avant le bloc préformaté. Et les deux deux-points sont convertis en un simple deux-points s'ils ne sont pas précédés d'une espace. L'exemple, ci-dessous débute par ``Un exemple::``. Si une espace est mis avant les `::` ils n'apparaissent pas.

Un exemple::

	Espaces, retour-chariot, toute sorte de balisage (comme *celui-ci* ou \celui-ci) sont préservés dans de tels blocs.
  Voyez comme j'ai changé de niveau d'indentation
  (mais pas suffisamment pour sortir du bloc)

Là, j'en suis sorti !


Noter que si un paragraphe consiste seulement en "::", il sera supprimé de l'output (donc pas rendu):

::

    Voici du texte préformaté, mais le premier "::" paragraphe est supprimé

Sections
========

Plus d'informations `ici <http://docutils.sourceforge.net/docs/user/rst/quickstart.html#sections>`_

Pour organiser du texte long en sections, vous pouvez utiliser des titres de section. Ce sont de simples lignes de texte (un ou plusieurs mots) avec une décoration spécifique : avant ou après le titre, avec des tirets, des signes égal, des tildes, ou tout caractère non-alphanumérique : = - `' " _ + # < > qui plaît. Une décoration seulement sous le titre est distincte de la même décoration utilisée sur et sous le titre. La décoration doit avoir la même longueur que le texte. Utiliser les décorations de manière cohérente, car tous les titres de sections avec la même décoration sont censés être au même niveau de titre.

Titre chapitre 1
================

Titre Section 1.1
-----------------

Titre Sous-section 1.1.1 
~~~~~~~~~~~~~~~~~~~~~~~~

Titre Section 1.2
-----------------

.. _lien_interne:

Titre Chapitre 2 
================

Il faut noter que chaque titre peut aussi être utilisé comme cible d'un lien interne au document, en utilisant simplement son nom. Pour créer un lien hypertexte avec un titre du document, écrire simplement \`Titre Chapitre 2\`_ pour avoir le lien `Titre Chapitre 2`_.

Le lien hypertexte pointant sur une ancre se définit ainsi : \:ref:`lien_interne`\ pour produire le lien :ref:`lien_interne`.

Titre du document/sous-titre
============================

Le titre du document entier est distinct des titres des sections et doit être formaté d'une manière différente. Utiliser une décoration unique au début du document pour son titre. Utiliser une autre décoration unique immédiatement après le titre du document. Par exemple :


Titre du Document
=================


Sous-Titre 
^^^^^^^^^^

Section 1
=========

Noter que les titres du document et de section utilisent tous deux des signes "=" mais ce sont des styles non reliés. Le texte des titres décoré au-dessus et au-dessous peuvent être indentés par souci d'esthétique.

Séparation
==========

Une séparation (rendue en HTML avec la balise <hr>) se crée avec la répétition d'au moins 4 caractères de ponctuation, séparée de lignes vides ::

	paragraphe

	----

	paragraphe

se rend ainsi :

paragraphe

----

paragraphe


Commentaires
============

Pour insérer un commentaire qui ne sera pas traité par reST ou Sphinx, faire débuter le paragraphe par "..".


Tableaux
========

Plus d'informations `ici <http://docutils.sourceforge.net/docs/ref/rst/directives.html#tables>`_

Il y a plusieurs manières de construire des tableaux avec reST et aucune n'est aisée, notamment lorsque les tableaux sont complexes.

Tableaux simples
----------------

Commencent et finissent par une simple ligne de signe "=". Le signe "-" est utilisé optionnellement pour signaler une fusion de deux colonnes contiguës. Un ou plusieurs espaces signalent les limites de colonnes::

	====  ====  ========
	A     B     A et B
	----  ----  --------
	 \    	    a et b
	====  ====  ========
	Faux  Faux  Faux
	Vrai  Faux  Faux
	====  ====  ========

sera rendu ainsi :

====  ====  ========
A     B     A et B
----  ----  --------
 \    	    a et b
====  ====  ========
Faux  Faux  Faux
Vrai  Faux  Faux
====  ====  ========

Note : Débuter une ligne par un espace vide rend la ligne entière vide. Il convient donc de signaler par un antislash (voir tableau) la première case vide, si elle l'est.

Tableaux CSV
------------

Une autre possibilité est de composer un tableau en spécifiant son format et son contenu ligne à ligne::

	.. csv-table:: Délices glacés!
   		:header: "Produit", "Quantité", "Description"
   		:widths: 15, 10, 30

   		"Albatross", 2.99, "On a stick!"
   		"Crunchy Frog", 1.49, "If we took the bones out, it wouldn't be
  		 crunchy, now would it?"
   		"Gannet Ripple", 1.99, "On a stick!"

sera rendu ainsi :

.. csv-table:: Délices glacés!
   :header: "Produit", "Quantité", "Description"
   :widths: 15, 10, 30

   "Albatross", 2.99, "On a stick!"
   "Crunchy Frog", 1.49, "If we took the bones out, it wouldn't be
   crunchy, now would it?"
   "Gannet Ripple", 1.99, "On a stick!"

Tableaux en liste
-----------------

Il est aussi possible de générer un tableau à partir de la directive list-table, de manière plutôt aisée (attention à utiliser des espaces pour l'indentation, et non des tabulations)::

	.. list-table:: Délices glacés!
	   :widths: 15 10 30
	   :header-rows: 1

	   * - Produit
	     - Quantité
	     - Description
	   * - Albatross
	     - 2.99
	     - Sur un bâton!
	   * - Crunchy Frog
	     - 1.49
	     - Si on avait enlevé les os, il aurait été moins croquant, non?
	   * - Gannet Ripple
	     - 1.99
	     - Sur un bâton!

qui sera rendu ainsi :

.. list-table:: Délices Glacés!
   :widths: 15 10 30
   :header-rows: 1

   * - Produit
     - Quantité
     - Description
   * - Albatross
     - 2.99
     - Sur un bâton!
   * - Crunchy Frog
     - 1.49
     - Si on avait enlevé les os, il aurait été moins croquant, non?
   * - Gannet Ripple
     - 1.99
     - Sur un bâton!

Tableaux en grille
------------------

Une manière plus complexe de réaliser tous types de tableaux est de considérer que :

* un signe "-" délimite l'extérieur du tableau et les lignes horizontales du tableau ;
* un signe "=" déilite le bas de l'en-tête du tableau ;
* un signe "+" signale les intersections entre lignes verticales et horizontales du tableau ;
* un signe "|" signale les lignes verticales.

Ainsi, le tableau ci-dessous ::

	+------------------------+------------+----------+
	| Header row, column 1   | Header 2   | Header 3 |
	+========================+============+==========+
	| body row 1, column 1   | column 2   | column 3 |
	+------------------------+------------+----------+
	| body row 2             | Cells may span        |
	+------------------------+-----------------------+

Sera rendu ainsi :

+------------------------+------------+----------+
| Header row, column 1   | Header 2   | Header 3 |
+========================+============+==========+
| body row 1, column 1   | column 2   | column 3 |
+------------------------+------------+----------+
| body row 2             | Cells may span        |
+------------------------+-----------------------+

Comme cela est assez difficile à réaliser sans erreurs, nous conseillons l'utilisation de l'éditeur `SublimeText <https://www.sublimetext.com>`_ avec l'extension `rst-completion <https://github.com/mgaitan/sublime-rst-completion>`_, qui permet quasi-automatiquement de réaliser des tableaux complexes. Il y a également l'`éditeur de tableaux en ligne <http://truben.no/table/>`_ de Truben qui peut être utilisé pour coder des tableaux automatiquement.


Notes de bas de page
====================

L'appel d'une note de bas de page peut être :

* un nombre d'un ou plusieurs chiffres ;
* un "#" pour des notes numérotées automatiquement ;

L'appel est inséré ainsi dans le texte ``[1]_``, rendu par un lien hypertexte cliquable : [1]_. Chaque corps de note démarre par un double point "..", une espace l'un des appels ci-dessus entre crochets, une espace, suivi par le corps de la note. Ce dernier est indenté d'au moins 3 espaces et aligné à gauche. Le corps peut être placé n'importe où dans le document (pas seulement à sa fin)::

	.. [1] Je suis un corps de note de bas de page.

est rendu ainsi :

.. [1] Je suis un corps de note de bas de page.


Liens hypertextes
=================

Nous avons déjà vu plus haut (`Titre Chapitre 2`_) le moyen d'insérer des liens hypertextes référant à des sections du même document (ancres). 

Liens externes
--------------

Référer à un lien hypertexte externe peut se faire, soit ainsi::

	`A ReStructuredText Primer <http://docutils.sourceforge.net/docs/user/rst/quickstart.html>`_

qui sera rendu ainsi :
`A ReStructuredText Primer <http://docutils.sourceforge.net/docs/user/rst/quickstart.html>`_

Soit ainsi::

	`A ReStructuredText Primer`_ (hyperlien)
	.. _ReStructuredText Primer: http://docutils.sourceforge.net/docs/user/rst/quickstart.html (cible, indiquée plus loin dans le document, ou à sa toute fin)

Ce qui sera rendu ainsi (noter, en visualisant le code source de la page, la spécification de la cible à la toute fin du document). Cela peut d'ailleurs être pratique d'avoir ainsi un certain nombre de liens qui reviennent souvent dans une série de documents (adresses, etc.) : `A ReStructuredText Primer`_. D'autres moyens de réaliser des liens entre documents Sphinx sont décrits ici :ref:`syntaxe_sphinx`.


Substitutions
=============

Il est possible de spécifier un ou plusieurs mots (bloc), censés revenir souvent dans un document, qui remplaceront à la compilation le terme qui les représente. Cela est utile pour représenter des mots, une image (mais pas des liens hypertextes). Voici comment représenter le bloc et le mot qui les représente::

	Voici un |mot| à remplacer.

et comment on indique le bloc qui va remplacer le mot (à placer n'importe où dans le doc, p. ex. en toute fin)::

	.. |mot| `mot qui va remplacer celui`

Cela sera rendu ainsi :

Voici un |mot| à remplacer.

.. |mot| replace:: mot qui va remplacer celui


Il existe également les termes réservés suivants : ``|today|``, qui insère la date courante ; ``
|version| et |release] qui indiquent resp. les numéros de la version et de la sous-version du projet. 


Directives
==========
Passons maintenant à la description de directives, qui étendent les capacités de reST. Il est à noter qu'on ne peut utiliser de directives avec du texte mis en forme (gras, italiques).

Insertion de HTML
-----------------

La directive ``:raw:`` permet d'insérer du code HTML (ou LaTeX) dans un document reST::

	.. raw:: html

   <hr width=50 size=10>

sera rendu ainsi

.. raw:: html

   <hr width=50 size=10>

Cela peut être très utile, notamment pour insérer des vidéos, du QCM, ou autres éléments HTML.

Table des matières
------------------

Plus d'informations `ici <http://docutils.sourceforge.net/docs/ref/rst/directives.html#table-of-contents>`_

On peut afficher la table des matières du document qui la contient, p. ex., à son début ou sa fin. La directive est ``.. contents::``. Les options sont les suivantes. "depth" indique la profondeur des sections listées dans la table, "local" commande la production d'une table correspondant à la section dans laquelle la directive est située ; "backlinks" produit les liens "en retour" de chaque (sous-titre) jusqu'à la table::

	.. contents:: Table des matières
		:depth: 2
		:local: 
		:backlinks: top

est rendu ainsi:

.. contents:: Table des matières
	:depth: 2
	:backlinks: top

**Attention** : Ne pas confondre cette directive avec la directive toctree, qui peut elle aussi générer une table des matières sur une page (index, par défaut), mais qui, surtout, crée la structure de documents concernés dans la table selon la commande de compilation (build). Ainsi, la commande <make html> (sans les signes <>) générera la table des matières et les liens vers les autres documents.

**Astuce** : Comme la directive 'contents' ne produit que la table des matières du document en cours (p. ex., l'index), il n'est pas aisé d'ajouter automatiquement une table des matières complète à un document. Voici la procédure :

* générer un seul document HTML fusionnant un cours, avec la commande make singlehtml ;
* l'ouvrir dans un navigateur ; 
* faire un clic droit sur la table des matières (cadre à gauche), et faire "Inspecter l'élément" ;
* identifier les lignes de code générant la table des matières et faire clic droit>Copier comme HTML ;
* coller la table des matières à l'endroit voulu du fichier généré par la commande singlehtml.
 
 
Images
------

Pour inclure une image dans votre document, utiliser la directive ``image``. Par exemple :: ``.. image:: images/computer.png`` sera rendu ainsi :

.. image:: images/computer.png

Il est possible d'ajouter des informations de taille, d'échelle, d'alignement et de texte alternatif ::

	.. image:: images/computer.png
   		:height: 100
   		:width: 200
   		:scale: 50
   		:align: center
   		:alt: ordinateur

Sera rendu ainsi :

.. image:: images/computer.png
   :height: 100
   :width: 200
   :scale: 50
   :align: center
   :alt: ordinateur


Encadré flottant
----------------

Il est possible d'insérer un encadré flottant (p. ex., pour réaliser des encadrés indépendants du texte, un résumé, etc.), flottant à droite du texte courant, avec la syntaxe suivante::

	.. sidebar:: Titre du texte flottant
   		:subtitle: Texte optionnel

   		Le texte flottant est ici.

Qui sera rendu comme le texte à droite.

.. sidebar:: Titre du texte flottant
   		:subtitle: Texte optionnel

   		Le texte flottant est ici.


.. _rest_admonitions:

Paragraphes spécifiques (admonitions)
-------------------------------------

Se référer à :ref:`sphinx_admonitions` pour les admonitions ajoutées par Sphinx.

Il existe de nombreux moyens de mettre en valeur un paragraphe. Les voici, appliquées au même paragraphe, respectivement ``.. admonition::``, ``.. note::``, ``.. attention::``, ``.. caution::``, ``.. danger::``, ``.. error::``, ``.. hint::````.., ``.. important::``, ``.. tip``, ``.. warning::``. Il faut aussi noter que le rendu de chaque admonition peut varier selon le thème choisi, et qu'il convient de les utiliser de manière cohérente et mesurée tout au long des documents. L'admonition varie en fonction de la langue définie dans le fichier conf.py :

.. admonition:: admonition générique
	
	Un texte d'admonition, avec l'intitulé que l'on veut.

.. note:: Voici un paragraphe que je veux mettre en évidence. Voici un paragraphe que je veux mettre en évidence. Voici un paragraphe que je veux mettre en évidence.

.. caution:: Voici un paragraphe que je veux mettre en évidence. Voici un paragraphe que je veux mettre en évidence. Voici un paragraphe que je veux mettre en évidence.

.. danger:: Voici un paragraphe que je veux mettre en évidence. Voici un paragraphe que je veux mettre en évidence. Voici un paragraphe que je veux mettre en évidence.

.. error:: Voici un paragraphe que je veux mettre en évidence. Voici un paragraphe que je veux mettre en évidence. Voici un paragraphe que je veux mettre en évidence.

.. hint:: Voici un paragraphe que je veux mettre en évidence. Voici un paragraphe que je veux mettre en évidence. Voici un paragraphe que je veux mettre en évidence.

.. important:: Voici un paragraphe que je veux mettre en évidence. Voici un paragraphe que je veux mettre en évidence. Voici un paragraphe que je veux mettre en évidence.

.. tip:: Voici un paragraphe que je veux mettre en évidence. Voici un paragraphe que je veux mettre en évidence. Voici un paragraphe que je veux mettre en évidence.

.. warning:: Voici un paragraphe que je veux mettre en évidence. Voici un paragraphe que je veux mettre en évidence. Voici un paragraphe que je veux mettre en évidence.


Formules mathématiques
======================

Il est possible d'insérer, dans le texte ou en tant que bloc spécifique, des formules mathématiques (utiliser la syntaxe LaTeX). Voici le bloc::

	.. math::

		α_t(i) = P(O_1, O_2, … O_t, q_t = S_i λ)

qui sera rendu :

.. math::

	α_t(i) = P(O_1, O_2, … O_t, q_t = S_i λ)

et les formules dans le texte : ``:math:`A_\text{c} = (\pi/4) d^2``, sera rendu ainsi : :math:`A_\text{c} = (\pi/4) d^2`.

Directives HTML
===============

Il existe une série de directives spécifiques HTML permettant d'ajouter des méta-données ou des balises HTML dans un document reST. La directive ``.. meta::`` permet d'ajouter des méta-données dans le document (balise meta).


Et après ?
==========

Ce document est une simple introduction à reST. Plus d'informations ici : 

* `Intro à reST en français (AFUL) <https://aful.org/wikis/interop/ReStructuredText>`_
* `Quick reST <http://docutils.sourceforge.net/docs/user/rst/quickref.html#hyperlink-targets>`_
* `L'ensemble des directives <http://docutils.sourceforge.net/docs/ref/rst/directives.html>`_

.. _A ReStructuredText Primer: http://docutils.sourceforge.net/docs/user/rst/quickstart.html
