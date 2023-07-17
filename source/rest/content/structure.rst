.. Sphinx: Documentation sur sphinx

Syntaxe **reST**
----------------

Le langage **reST** est un langage de balisage (markup language) très proche du markdown. 
Un fichier reST est un fichier texte dont les éléments sont mis en évidence par des 
**balises** ou des **directives**. 

Les **balises** principales sont:

- les titres et sous-titres
- l'emphase: gras et italique
- les listes numérotées et non numérotées
- les liens

Une **directive** suit une syntaxe précise et permet d'agir sur le document pour créer 
des mises en forme de texte plus élaborées. La syntaxe est la même quelle que soit la 
directive utilisée.

.. code-block:: rest

   .. directive:: nom
   
      :paramètre_1: valeur_1
      :paramètre_2: valeur_2
      etc
      
Certaines directives n'ont pas de nom. Les paramètres ne sont pas obligatoires, et 
certaines directives n'ont pas de paramètres. Tout ce qui est identé après la déclaration 
de la directive est contenue dans celle-ci.

Les principales directives sont:

- la navigation : toctree
- les blocs de textes : admonition, note, tip
- les blocs de code
- les images
- les tableaux

De nombreux sites documentent sur la syntaxe et les possibilités offertes par **reST**.

.. _`reStructuredText Markup Specification`: https://docutils.sourceforge.io/docs/ref/rst/restructuredtext.html
.. _`Quick reStructuredText`: https://docutils.sourceforge.io/docs/user/rst/quickref.html
.. _`Sphinx Directives`: https://www.sphinx-doc.org/en/master/usage/restructuredtext/directives.html

+ `reStructuredText Markup Specification`_ documentation de docutils
+ `Quick reStructuredText`_
+ `Sphinx Directives`_

Composer un document en **reST**
-------------------------------

Plutôt que faire une liste des différentes syntaxes possibles en **reST**, je propose de 
voir comment on rédige certains éléments de texte avec cette syntaxe.

Les titres et les sous-titres
*****************************

Comme en **html**, il existe différents niveaux de titres. La mise en place d'un titre 
est très simple puisqu'il suffit de le souligner par un même symbole. Les plus 
utilisés sont le signe égal ``=``, le tiret ``-``, l'astérisque ``*``, le signe plus 
``+`` ou encore le dièse ``#`` (d'autres symboles sont possibles).

Le niveau de titre est automatiquement détecté lors de l'export avec la commande 
``make``.

Donnons un exemple de code pour les titres:

.. code-block:: rest

   Titre principal
   ==============
   
   Sous-titre
   ----------

L'emphase, le gras et l'italique
********************************

Pour placer du texte en gras ou en italique, on utilise l'astérisque comme balise. Un 
astérisque simple transforme le texte en *italique* et un double astérisque transforme 
le texte en **gras**.

.. code-block:: rest

   Texte en *italique* et texte en **gras**.

Les listes
**********

les items d'une **liste numérotée** sont simplement précédés par un numéro suffixé par 
un point. Si le suffixe (séparateur) est remplacé par une parenthèse, à l'export c'est 
un point qui est utilisé.

.. admonition:: Exemple

   1. premier item
   2. Deuxième item
   
      a) sous-premier item du deuxième item
      b) sous deuxième item du second item
      
   Cette liste s'obtient avec le code suivant:
   
   .. code-block::
      
      1. premier item
      2. Deuxième item
   
         a) sous-premier item du deuxième item
         b) sous deuxième item du second item

Les items d'une liste non numérotée (liste à puces) sont précédés d'un tiret ou autres 
symboles.

.. admonition:: Exemple

   + premier item
   + Deuxième item
      
   Cette liste s'obtient avec le code suivant:
   
   .. code-block::
      
      + premier item
      + Deuxième item

Les liens hypertextes
*********************

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
      
   
Directive toctree
*****************

La `directive toctree`_ permet de construire un **menu de navigation** entre les 
pages de la documentation en utilisant les titres et sous-titres de chaque document. 
La profondeur des titres utilisés est déterminé par la parmètre ``:maxdepth:``.

.. admonition:: Exemple

   Pour la documentation que vous lisez actuellement, on a la directive suivante:
   
   .. code-block::
      
      .. toctree::
         :maxdepth: 2
         :caption: Sphinx

.. important::
   
   Lors de la construction de cette documentation, le menu de navigation a été placé 
   dans une colonne, à gauche du document **html**.
   

.. _`directive toctree`: https://www.sphinx-doc.org/fr/master/usage/restructuredtext/directives.html#toctree-directive

Les blocs de textes
*******************

Pour surexposer un texte, il existe des directives prédéfinies qui vont à la 
création de la documentation générer des blocs html avec des propriétés css adaptées 
pour la surexposition. Ces directives prédéfinies sont **tip**, **caution**, 
**warning** **important**, **note**, **error** et **hint**.

Voici quelques exemples de ces directives.

.. code-block:: rest

   .. important::
      
      La directive surexposant un texte **important** ci-après.
      
.. important::
      
      La directive surexposant un texte **important** ci-après.
      
.. code-block:: rest

   .. hint::
      
      La directive surexposant une **indication** ci-après.
      
.. hint::
      
      La directive surexposant une **indication** ci-après.
      
.. code-block:: rest

   .. error::
      
      La directive surexposant une **erreur** ci-après.
      
.. error::
      
      La directive surexposant une **erreur** ci-après.

.. code-block:: rest

   .. note::
      
      La directive surexposant une **note** ci-après.
      
.. note::
      
      La directive surexposant une **note** ci-après.
      
.. code-block:: rest

   .. warning::
      
      La directive surexposant un **avertissement** ci-après.
      
.. warning::
      
      La directive surexposant un **avertissement** ci-après.

.. code-block:: rest

   .. caution::
      
      La directive surexposant une **mise en garde** ci-après.
      
.. caution::
      
      La directive surexposant une **mise en garde** ci-après.

Si cela ne suffit pas, on peut personnaliser ce bloc de texte surexposé. Cette 
documentation est alimentée de blocs de texte servant d'exemples. Pour ce faire, on 
utilise la directive **admonition** qui accepte un nom. En voici justement un exemple.

.. code-block:: rest

   .. admonition:: Exemple
      
      La directive surexposant un bloc personnalisé pour **exemple** ci-après.
      
.. admonition:: Exemple
   
   La directive surexposant un bloc personnalisé pour **exemple** ci-après.
   
.. tip:: 

   La couleur utilisée pour les blocs peut être changée en apportant des propriétés 
   css. La création d'un bloc **admonition** associé à un nom crée lors de la 
   construction de la documentation une classe css de même nom.

Les blocs de code
*****************

Comme pour les blocs de textes à surexposer, il est possible de mettre en évidence un 
code avec la `directive code-block`_. Cette directive accepte en nom le langage 
utilisé.

.. admonition:: Exemple

   Un script en python avec les numéros de lignes.
   
   .. code-block:: python
      :linenos:
      
      def carre(n):
         return n**2
   
   Puis on appelle la fonction dans l'interpréteur Python:
   
   >>> carre(4)
   16
   
   Le code pour obtenir l' affichage de la fonction ``carre`` ci-dessus est le suivant:
   
   .. code-block:: rest
   
      .. code-block:: python
         :linenos:
         
         def carre(n):
            return n**2
            
   L'affichage du code de l'interpréteur Python est encore plus simple puisqu'il suffit 
   de saisir les 3 chevrons >>> sans utiliser la directive **code-block**.

Une autre méthode d'insertion de code est possible et présente l'avantage de ne pas 
recopier le code. La `directive literalinclude`_ permet d'insérer le contenu d'un fichier 
passé en paramètre. Il y a des options qui permettent de sélectionner les lignes du 
fichier à insérer et aussi la mise en évidence de certaines lignes de code grâce à un 
surlignage.

.. admonition:: Exemple
   
   Supposnons que le fichier ``exemple.py`` contienne le code de la fonction ``carre``. 
   On peut insérer ce code avec la directive :
   
   .. code-block:: rest
   
      .. literalinclude:: exemple.py
         :language: python:
         :linenos:
         
   Ce qui donnera le même affichage que l'exemple précédent. Le principal intérêt est que 
   le fichier mis à jour provoque une mise à jour de la documentation.

.. _`directive code-block`: https://www.sphinx-doc.org/fr/master/usage/restructuredtext/directives.html#directive-code-block
.. _`directive literalinclude`: https://www.sphinx-doc.org/fr/master/usage/restructuredtext/directives.html#directive-literalinclude

Insérer une image
*****************

La `directive image`_ permet d'insérer une image dans un document. Elle admet un nom de 
fichier image comme paramètre. De nombreuses options permettent de gérer l'apparence de 
l'image comme la taille et sa disposition.

.. admonition:: Exemple

   Pour insérer le logo de Python dans ce document, nous devons ajouter le code suivant:

   .. code-block:: rest
      
      .. image:: img/Python-logo-notext.svg

   .. image:: ../img/Python-logo-notext.svg

.. _`directive image`: https://www.sphinx-doc.org/fr/master/usage/restructuredtext/basics.html?highlight=image#images
