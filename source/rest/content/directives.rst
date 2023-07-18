Les directives reST
===================

Directive toctree
-----------------

La `directive toctree`_ permet de construire un **menu de navigation** entre les pages de la documentation en utilisant les titres et sous-titres de chaque document. La profondeur des titres utilisés est déterminé par la paramètre ``:maxdepth:``.

.. admonition:: Exemple

   Pour la documentation que vous lisez actuellement, on a la directive suivante:
   
   .. code-block::
      
      .. toctree::
         :maxdepth: 1
         :caption: Sphinx

.. important::
   
   Lors de la construction de cette documentation, le menu de navigation a été placé dans une colonne, à gauche du document **html**. Le placement de ce menu est défini par le thème appliqué à la documentation. 
   

.. _`directive toctree`: https://www.sphinx-doc.org/fr/master/usage/restructuredtext/directives.html#toctree-directive

Les blocs de textes
-------------------

.. rubric:: Blocs prédéfinis

Pour surexposer un texte, il existe des directives prédéfinies qui vont lors de l'exportation de la documentation générer des blocs html avec des propriétés css adaptées pour la surexposition. Ces directives prédéfinies sont **tip**, **caution**, **warning**, **important**, **note**, **error** et **hint**.

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

.. rubric:: Bloc personnalisable

Si cela ne suffit pas, on peut personnaliser ce bloc de texte surexposé. Cette documentation est alimentée de blocs de texte servant d'exemples. Pour ce faire, on utilise la directive **admonition** qui accepte un nom. En voici justement un exemple.

.. code-block:: rest

   .. admonition:: Exemple
      
      La directive surexposant un bloc personnalisé pour **exemple** ci-après.
      
.. admonition:: Exemple
   
   La directive surexposant un bloc personnalisé pour **exemple** ci-après.
   
.. tip:: 

   La couleur utilisée pour les blocs peut être changée en personnalisant des propriétés css.

Les blocs de code
-----------------

Comme pour les blocs de textes à surexposer, il est possible de mettre en évidence du code comme le langage Python.

.. rubric:: Insérer le code dans le contenu

La `directive code-block`_ permet d'insérer du code dans le contenu de notre documentation. Cette directive accepte en nom le langage utilisé. Cette directive admet des paramètres. On peut ajouter le paramètre ``linenos``  pour afficher les numéros de lignes.

.. admonition:: Exemple

   Un script en python avec les numéros de lignes.
   
   .. code-block:: python
      :linenos:
      
      def carre(n):
         return n**2
   
   Puis on appelle la fonction dans l'interpréteur Python:
   
   >>> carre(4)
   16
   
   Le code pour obtenir l'affichage de la fonction ``carre`` ci-dessus est le suivant:
   
   .. code::
   
      .. code-block:: python
         :linenos:
         
         def carre(n):
            return n**2
            
   L'affichage du code de l'interpréteur Python est encore plus simple puisqu'il suffit de saisir les 3 chevrons ``>>>`` sans utiliser la directive **code-block**.

.. rubric:: Insérer le contenu d'un fichier

Une autre méthode d'insertion de code est possible et présente l'avantage de ne pas recopier le code. La `directive literalinclude`_ permet d'insérer le contenu d'un fichier. Le nom du fichier et le chemin relatif sont ajoutés en tant que nom. 

Cette directive admet des paramètres (options) qui permettent de sélectionner les lignes du fichier à insérer et aussi la mise en évidence de certaines lignes de code grâce à un surlignage.

.. admonition:: Exemple
   
   Supposons que le fichier ``exemple.py`` contienne le code de la fonction ``carre``. On peut insérer ce code avec la directive :
   
   .. code::
   
      .. literalinclude:: ../python/exemple.py
         :language: python
         :linenos:
         
   Cette directive affiche dans le contenu de la documentation le code du fichier python ``exemple.py``. 
   
   .. literalinclude:: ../python/exemple.py
         :language: python
         :linenos:

   Le principal intérêt est que le fichier mis à jour provoque une mise à jour de la documentation.

.. _`directive code-block`: https://www.sphinx-doc.org/fr/master/usage/restructuredtext/directives.html#directive-code-block
.. _`directive literalinclude`: https://www.sphinx-doc.org/fr/master/usage/restructuredtext/directives.html#directive-literalinclude

Directives figure et image
--------------------------


.. rubric:: Insérer une figure

La directive ``figure`` permet d'insérer une image en y assciant une légende. La syntaxe est la suivante:

.. code::

   .. figure:: chemin/vers/fichier/image
      :align: center/left/right
      :width: dimension

      Texte de la légende

Voici en exemple, l'insertion du logo du langage Python en tant que ``figure`` avec une légende.

.. figure:: ../img/Python.svg
   :align: center
   :width: 200

   Logo Python (format svg)


.. rubric:: Insérer une image

La `directive image`_ permet d'insérer une image dans un document. Juste après le nom de la directive, on place le nom du fichier image avec son chemin relatif. De nombreuses options (paramètres) permettent de gérer l'apparence de l'image comme la taille et sa disposition.

.. admonition:: Exemple

   Pour insérer le logo de Python centré dans ce document avec une dimension de 200 pixel, nous ajoutons le code suivant:

   .. code-block:: rest
      
      .. image:: ../img/Python-logo-notext.svg
         :align: center
         :width: 200

   .. image:: ../img/Python-logo-notext.svg
      :align: center
      :width: 200

.. _`directive image`: https://www.sphinx-doc.org/fr/master/usage/restructuredtext/basics.html?highlight=image#images
