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

On peut insérer un lien soit directement dans le texte (comme en html) soit par 
référence. 

La première méthode pour créer un lien directement dans le texte suit la syntaxe :
```nom du lien <url du lien>`_``.

.. admonition:: Exemple

   Voici un lien vers la page des lauréats normands du concours **la nuit du code 2022** 
   sur le `site NSI-SNT <https://nsi-snt.ac-normandie.fr/nuit-du-code-2022-101>`_ de 
   l'académie de Normandie.
   
   Le lien est codé par ```site NSI-SNT <https://nsi-snt.ac-normandie.fr/nuit-du-code-2022-101>`_``
   
L'autre méthode pour créer un lien hypertexte est le lien par référence. Lorsqu'une 
référence est construite, on peut l'utiliser plusieurs fois dans le document.
La syntaxe est la suivante:

.. code-block:: rest
   
   .. _`nom du lien`: url du lien ou ancre
   
Les simples quote ne sont pas nécessaires si le lien est constitué d'un seul mot. 
Ensuite, dans le document, on rappelle la référence en plaçant le *souligné du 8* après 
(et non avant).

.. admonition:: Exemple

   Je crée une ancre pour revenir au début de cette page. Je prends donc le titre 
   principal comme ancre. Cela s'écrit:
   
   .. code-block:: rest
   
      .. _`Structure d'un document`: Structure d'un document
   

   Ici je rappelle mon ancre en ajoutant dans mon texte Structure d'un document
   qui donne le lien `Structure d'un document`.

.. tip::

   On remarquera que l'url change en étant suffixée par le nom de l'ancre. Les espaces 
   sont remplacés par des tirets. S'il n'y a pas d'ambiguïté, le lien peut se faire 
   sur une autre page de la documentation:
   
   .. code-block:: rest

      .. _`Installation de sphinx`: ../sphinx/installer.html
   
   .. _`Installation de sphinx`: ../sphinx/installer.html
   
   Renvoi vers la page `Installation de sphinx`_.
