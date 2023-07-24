.. _`balises reST`:

Les balises reST
================

Titres et emphase
-----------------

Plutôt que faire une liste des différentes syntaxes possibles en **reST**, je propose à travers différents exemples l'utilisation de certains éléments de texte avec cette syntaxe.

.. rubric:: Les titres et les sous-titres

Comme en **html**, il existe différents niveaux de titres. La mise en place d'un titre est très simple puisqu'il suffit de le souligner par un même symbole. Les plus utilisés sont le signe égal ``=``, le tiret ``-``, l'astérisque ``*``, le signe plus ``+`` ou encore le dièse ``#`` (d'autres symboles sont possibles).

Le niveau de titre est automatiquement détecté lors de l'export vers le format html ou latex.

Code pour créer un titre et un sous-titre.

.. code::

   Titre principal
   ==============
   
   Sous-titre
   ----------

.. rubric:: Emphase: gras et italique

Comme la syntaxe markdown, pour la mise en forme de texte en gras ou en italique, on utilise l'astérisque comme balise. Un astérisque simple transforme le texte en *italique* et un double astérisque transforme le texte en **gras**.

.. code::

   Texte en *italique* et texte en **gras**.

Les listes
----------

.. rubric:: Listes numérotées

Les items d'une **liste numérotée** sont simplement précédés par un numéro suffixé par un point. Si le suffixe (séparateur) est remplacé par une parenthèse, à l'export c'est un point qui est utilisé.

.. admonition:: Exemple

   1. premier item
   2. Deuxième item
   
      a) sous-premier item du deuxième item
      b) sous deuxième item du second item

   3. troisième item
      
   Cette liste s'obtient avec le code suivant:
   
   .. code::
      
      1. premier item
      2. Deuxième item
   
         a) sous-premier item du deuxième item
         b) sous deuxième item du second item

      3. troisième item

.. note::

   Il est possible, voire avantageux, de remplacer les nombres par un dièse #. Lors de l'export, la numératation est automatique. D'ailleurs, si vous oubliez un numéro d'item, celui-ci est corrigé à l'exportation. Le code devient:

   .. code::
      
      #. premier item
      #. Deuxième item
   
         a) sous-premier item du deuxième item
         b) sous deuxième item du second item

      #. troisième item

.. rubric:: Listes à puces

Les items d'une liste non numérotée (liste à puces) sont précédés d'un tiret ou du signe plus +..

.. admonition:: Exemple

   + premier item
   + Deuxième item
      
   Cette liste s'obtient avec le code suivant:
   
   .. code::
      
      + premier item
      + Deuxième item

Il est possible de créer des sous-listes. C'est l'indentation qui crée le niveau de liste:

.. admonition:: Exemple

   - item de niveau 1
   - item de niveau 1
  
     - item de niveau 2
     - item de niveau 2

   - item de niveau 1

   Le tiret utilisé pour la puce est aligné avec le texte du niveau supérieur.

   Cette liste s'obtient avec le code suivant:

   .. code::

      - item de niveau 1
      - item de niveau 1
  
        - item de niveau 2
        - item de niveau 2

      - item de niveau 1


Les liens hypertextes
---------------------

On peut insérer un lien soit directement dans le texte (comme en html) soit par référence. 

.. rubric:: Lien hypertexte

La première méthode pour créer un lien directement dans le texte suit la syntaxe : ```nom du lien <url du lien>`_``.

.. admonition:: Exemple

   Voici un lien vers la page des lauréats normands du concours **la nuit du code 2022** sur le `site NSI-SNT <https://nsi-snt.ac-normandie.fr/nuit-du-code-2022-101>`_ de l'académie de Normandie.
   
   Le lien est codé par ```site NSI-SNT <https://nsi-snt.ac-normandie.fr/nuit-du-code-2022-101>`_``

.. rubric:: Lien par référence

L'autre méthode pour créer un lien hypertexte est le lien par référence. Lorsqu'une référence est construite, on peut l'utiliser plusieurs fois dans le document. La syntaxe est la suivante:

.. code-block:: rest
   
   .. _`nom du lien`: url du lien
   
Les simples quote ne sont pas nécessaires si le lien est constitué d'un seul mot. Ensuite, dans le document, on rappelle la référence en plaçant le *souligné du 8* après : `nom du lien`_.

.. admonition:: Exemple

   Je crée une référence pour un lien vers mes `pages github`_.

   .. _`pages github`: https://ychistel.github.io/learning
   
   .. code-block:: rest
   
      .. _`pages github`: https://ychistel.github.io/learning
   
   Ma référence créée, je la place dans mon document en utilisant le nom de la référence c'est à dire ```pages github`_``.

.. hint::

   Le positionnement des références dans le document n'a pas d'importance. Il est préférable de les regrouper dans le document, soit au début, soit à la fin.

.. rubric:: Ancre

Une "ancre" est un lien hypertexte interne au document, un renvoi vers une partie de la page html. Cette ancre est placée dans le document, là où l'on veut le renvoi. Il suffit de lui donner un nom avec la syntaxe:

.. code::

   .. _`nom ancre`: 

C'est dans l'appel qu'il y a une légère différence. Le lien est précédé de la balise ``:ref:`` suivie du nom de l'ancre sans le caractère souligné ajouté à la fin.

.. admonition:: Exemple

   Je crée une ancre pour revenir au début de cette page, juste au-dessus du titre principal. Cela s'écrit:
   
   .. code-block:: rest
   
      .. _`balises reST`: 
      
      Les balises reST
      ================
      ... suite du document
   
   Ensuite, je rappelle mon ancre en ajoutant la référence dans mon texte ``:ref:`balises reST``` qui donne le lien :ref:`balises reST`.


Il est possible de réaliser un renvoi vers une autre page de la documentation. Une ancre créée sur une page peut être rappelée sur n'importe qu'elle page de votre documentation.

.. admonition:: Exemple

   Une ancre a été créée sur la première page de la partie sur "reStructured Text". Il suffit de faire un appel de cette référence :ref:`reStructured Text` en insérant ``:ref:`reStructured Text```

.. tip::

   L'ancre vers une autre page de la documentation peut également se faire avec un lien hypertexte en utilisant un chemin relatif:
   
   .. code::

      .. _`reStructured Text`: ../index.html
   
   .. _`reStructured Text`: ../index.html
   
   Renvoi vers la page `reStructured Text`_.

.. rubric:: Lien de téléchargement

Pour finir avec les liens hypertextes, il est possible de créer un lien vers un document à télécharger. La balise qui le permet est ``:download:`` suivi du fichier à télécharger précédé du chemin relatif.

.. admonition:: Exemple

   On propose le téléchargement d'un document au format **pdf** nommé 
