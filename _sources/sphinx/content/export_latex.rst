Exporter la documentation en latex
==================================

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