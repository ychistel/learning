.. Documentation

Sphinx 
======

Sphinx est un module Python qui permet de construire une documentation à partir de 
fichiers **reStructured Text** (extension *rst*).	Les formats d'export pour la 
documention sont divers mais les plus courants sont **html** et **latex**. Sphinx offre 
de nombreux avantages :

1. Les fichiers **markdown** et **notebook jupyter** peuvent également être utilisés pour 
   alimenter la documentation et bien entendu les fichiers Python qui contiennent une aide 
   entre triples quote.
2. Les fichiers sources peuvent être placés dans différents sous-dossiers. Les liens 
   hypertextes (dans le cas d'un export html) seront automatiquement ajoutés.

Comme souvent, il y a une contrepartie :

1. Comprendre le fonctionnement de Sphinx, la structure des dossiers et fichiers et la 
   méthode de construction de la documentation.
2. Apprendre un nouvau langage de balisage très proche du markdown, mais a la portée de 
   tous.

Cela peut paraitre beaucoup mais finalement l'investissement est réduit vu la qualité de 
construction de la documentation.

.. toctree::
   :maxdepth: 1
   :caption: Sphinx
   
   content/installer.rst
   content/configurer.rst
   content/structure.rst
   

 
