Sphinx 
======

Sphinx est un **module** Python qui permet de construire une documentation à partir de fichiers texte suivant la syntaxe **reStructured Text** (extension *rst*). Les formats d'export pour la documention sont divers mais les plus courants sont **html** et **latex**. Sphinx offre de nombreux avantages :

1. Les fichiers **markdown** et **notebook jupyter** peuvent également être utilisés pour alimenter la documentation et bien entendu les fichiers **Python** qui contiennent une aide entre triples quote.
2. Les fichiers sources peuvent être placés dans différents sous-dossiers. Les liens hypertextes (dans le cas d'un export html) seront automatiquement ajoutés.

Comme souvent, il y a une contrepartie :

1. Comprendre le fonctionnement de Sphinx, la structure des dossiers et des fichiers et la méthode de construction de la documentation.
2. Apprendre un nouveau langage de balisage très proche du markdown, mais à la portée de tous.

L'investissement est assez important mais finalement très rentable vu la qualité de construction de la documentation.

.. note::

   Cette documentation a été réalisée avec ``sphinx``.

.. toctree::
   :maxdepth: 1
   :hidden:
   
   content/installer.rst
   content/configurer.rst
   content/structurer.rst
   content/export_html.rst
   content/export_latex.rst

 
