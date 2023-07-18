Syntaxe reST
============

Le langage **reST** est un langage de balisage (markup language) proche du markdown. Un fichier **reST** est un fichier texte dont les éléments sont mis en évidence par des  **balises** et des **directives**. 

Les **balises** sont des caractères qui viennent devant un texte ou encadrer un texte pour le mettre en valeur. Les principales balises sont utilisées pour:

- les titres et les sous-titres
- l'emphase: gras et italique
- les listes numérotées et non numérotées
- les liens hypertextes

Une **directive** est une dexcription du contenu que l'on souhaite insérer dans le document. Chaque directive suit la même syntaxe quelle que soit la directive. En voici la structure générale:

.. code-block:: rest

   .. directive:: nom
   
      :paramètre_1: valeur_1
      :paramètre_2: valeur_2
      etc

.. warning::

   L'indentation devant chaque ligne est importante. Si elle n'est pas correctement utilisée, la directive n'est pas reconnue.
      
Certaines directives n'ont pas de nom. Les paramètres ne sont pas obligatoires, et certaines directives n'ont pas de paramètres.

Les principales directives sont:

- la navigation : toctree
- les blocs de textes : admonition, note, tip, hint, warning, error, important
- les blocs de code: code-block
- les figures: figure
- les images: image aux formats png, jpg ou svg
- les tableaux : table, csv-table, list-table

De nombreux sites documentent la syntaxe et les possibilités offertes par **reST**.

.. _`reStructuredText Markup Specification`: https://docutils.sourceforge.io/docs/ref/rst/restructuredtext.html
.. _`Quick reStructuredText`: https://docutils.sourceforge.io/docs/user/rst/quickref.html
.. _`Sphinx Directives`: https://www.sphinx-doc.org/en/master/usage/restructuredtext/directives.html

+ `reStructuredText Markup Specification`_ documentation de docutils
+ `Quick reStructuredText`_
+ `Sphinx Directives`_

