Exporter la documentation en latex
==================================

.. _`customization latex`: https://www.sphinx-doc.org/en/master/latex.html#latex-elements-confval

L'export en ``latex`` se fait exactement comme en ``html``. La seule différence apparait dans le format de l'export.

Avec le fichier ``make``
-----------------------

#. Ouvrir une console ou fenêtre de commande ``cmd`` et se placer dans le dossier de la documentation contenant le dossier ``source``.
#. Saisir la commande:

   .. code::

      make latex

#. L'exportation se réalise dans le dossier ``build``. Le dossier ``build`` contient alors 2 dossiers : ``doctrees`` et ``latex``. Le premier contient l'ensemble des ressources à exporter et le second l'exportation au format latex.

   .. figure:: ../img/arbo_build.png
      :align: center
      :class: padding-8 border-style-solid border-width-1 border-radius-8 border-color-blue-light

#. Aller dans le dossier ``latex`` et vérifier la présence du fichier ``latex`` et aussi ``pdf``.

   .. figure:: ../img/arbo_latex.png
      :align: center
      :class: padding-8 border-style-solid border-width-1 border-radius-8 border-color-blue-light

.. note::

   Le dossier ``latex`` contient de nombreux fichiers parmi lesquels on retrouve des fichiers de style pour latex (extension .sty) et les images présentes dans la documentation.

Avec la commande ``sphinx-build``
---------------------------------

Comme l'exportation en html, on peut donc utiliser directement la commande ``sphinx-build`` en remplaçant le premier paramètre lié au format d'exportation.

.. code::

   sphinx-build -b format_export dossier_source dossier_destination

Dans notre cas, le format d'export est ``latex``, le dossier contenant la documentation est ``source`` et le dossier de destination est ``build/latex``. La commande est donc:

.. code::

   sphinx-build -b latex source build/latex

Les formats d'images
--------------------

Pour une exportation en ``html``, les images peuvent être au format ``jpg`` ou ``png``. Il en est de même pour l'exportation en ``latex``. Dans ce cas, il n'y a pas de problème.

Toutefois, si on souhaite un format plus adapté aujourd'hui pour le web, il est intéressant d'utiliser un format vectoriel comme le ``svg``. Son principal avantage est de pouvoir adapter une image toute dimension sans perte de qualité contrairement aux images de format ``jpg`` et ``png``.

Malheureusement ce format n'est pas géré par la compilation en ``latex`` et même si le fichier est bien généré, celui-ci ne contient pas les images au format ``svg``. Il existe une soluton à ce problème qui nécessite l'installation de ``Imagemagick``, une application permettant de convertir des images dans différents formats.

Après l'installation de ``Imagemagick``, il faut ajouter une extension dans le fichier de configuration ``conf.py``:

.. code-block:: python

   extensions = ['sphinx.ext.imgconverter']

.. note::

   Cette extension vient s'ajouter aux autres extensions comme ``nbsphinx`` ou ``sphinx-design``.

Après cette installation et cette nouvelle configuration, l'exportation en ``latex`` parvient à insérer les images aux formats ``png``, ``jpg`` et ``svg``. En fait, les images ``svg`` sont convertuies au format ``png`` et sont insérées comme telles.

.. _`image converter using Imagemagick`: https://www.sphinx-doc.org/en/master/usage/extensions/imgconverter.html

Plus d'information sur la documentation sphinx et `image converter using Imagemagick`_.

Configuration de l'export
-------------------------

Il existe 2 types d'export en latex basés sur les classes ``sphinxmanual.cls`` et ``sphinxhowto.cls``. La première classe crée un document de type **report** avec une hiérarchie en chapitre, section et sous-sections alors que la seconde classe crée un document de type **article** avec des sections et des sous-sections. Par défaut, l'export utilise la classe ``sphinxmanual.cls`` ou ``manual``.

.. note::

   Il est possible de créer sa propre classe et de l'appliquer lors de l'export en latex.

L'export en ``latex`` puis en ``pdf`` est modifiable. Pour cela, on ajoute au fichier de configuration ``conf.py`` des paramètres qui permettent d'ajouter des paquets, des commandes ou des environnements latex.

.. rubric:: Moteur de compilation

Par défaut, le moteur utilisé pour compiler le document ``latex`` en ``pdf`` est **pdflatex**. On peut compiler le document latex avec ``xelatex`` ou ``lualatex``. La variable python du fichier ``conf.py`` à modifier est ``latex_engine``. Elle admet comme valeur le moteur de compilation sous forme d'une chaine de caractères.

.. code:: python

   latex_engine = 'pdflatex' # ou 'xelatex' ou 'lualatex'

.. rubric:: Commandes latex

Pour ajouter une ou plusieurs commandes en latex à votre document, on déclare dans la variable ``latex_elements`` les commandes souhaitées. Cette variable est un dictionnaire python dont les clés sont des paramètres prédéfinis (voir la documentation de sphinx sur la `customization latex`_). Parmi les paramètres, on a:

-  ``papersize`` qui prend les valeurs `a4paper` ou `letter`
-  ``pointsize`` qui définit la taille de police de caractères
-  ``passoptionstopackages`` qui transmet les options à un paramètre
-  ``fncychop`` qui permet d'activer le package pour l'entête et le pied de page
-  ``sphinxsetup`` qui permet d'ajouter des commandes, packages et autres informations au document latex
-  ``preamble`` qui permet d'ajouter des paquets latex dans le préambule

.. code:: python

   latex_elements = {
      'cle_1' : r'commande latex',
      'cle_2' : r'commande latex',
      ...
      'cle_n' : r'''
         commande latex
         comande latex
         commande latex ..
      '''
   }

.. hint::

   Il est possible de saisir une commande pour une clé mais aussi de saisir plusieurs commandes dans une même clé avec une triple quote.

.. admonition:: Exemple

   Voici la variable python ``latex_elements`` pour l'export latex de cette documentation:

   .. code:: python

      latex_elements = {
         'papersize': 'a4paper',
         'fontpkg': '\\usepackage{amsmath,amsfonts,amssymb,amsthm}',
         'geometry': '\\usepackage[a4paper,left=0.6in, right=0.6in, top=0.6in, bottom=0.6in]{geometry}',

         'figure_align':'htbp',
         'pointsize': '11pt',

         'preamble': r'''
            \usepackage{verbatim}
            \usepackage{fancyvrb}
         ''',

         'sphinxsetup':r'''
            noteBorderColor={rgb}{0.53, 0.81, 0.98},
            tipBorderColor={rgb}{0.53, 0.81, 0.98},
            cautionBorderColor={rgb}{0.7, 0.93, 0.36},
            hintBorderColor={rgb}{0.7, 0.93, 0.36},
            warningBorderColor={rgb}{1.0, 0.25, 0.25},
            errorBorderColor={rgb}{1.0, 0.25, 0.25},
            importantBorderColor={rgb}{1.0, 0.25, 0.25},
         '''
   }

.. rubric:: Feuille de style

#. On crée une feuille de style pour son document latex qu'on appelle ``mystyle.sty``.
#. On déclare la feuille de style dans le fichier de configuration ``conf.py`` avec la variable python ``latex_additionnal_files`` qui prend en valeur une liste de chaines de caractères (associées aux fichiers).
#. On appelle la feuille de style depuis le fichier de configuration ``conf.py`` dans le dictionnaire ``latex_elements`` associée au mot clé ``preamble`` pour que la commande d'appel latex soit inséré dans le préambule du document latex.

.. code:: python

   latex_elements = r'input{mystyle.sty}'

.. hint:: 

   La feuille de style se trouve dans le même dossier que le fichier de configuation ``conf.py``

.. container:: exemple

   .. rubric:: Exemple
      
   c'est un container avec du contenu.
   c'est un container avec du contenu.
   c'est un container avec du contenu.
   c'est un container avec du contenu.
   c'est un container avec du contenu.

   c'est un container avec du contenu.