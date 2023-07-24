.. _`reStructured Text`:

reStructured Text (reST)
========================

Un fichier texte rédigé avec la syntaxe reST permet la mise en forme des différents éléments de texte lors de la compilation du document en html. Cette syntaxe simplifiée s'apparente à la syntaxe mardown utilisée dans les notebook jupyter.

Quelle différence entre ces syntaxes et pourquoi choisir reST ?

-  Il y a très peu de différence en dehors de la syntaxe elle-même. Elle peut paraître plus lourde au premier abord, mais elle offre au final plus de fonctionnalités.
-  Le choix de reST est lié à la construction de la docamentation par le module ``sphinx`` de Python qui s'appuie par défaut sur cette syntaxe. Mais surtout, elle intègre de très nombreux éléments de mise en forme du texte contrairement à markdown qui nécessite le reoucrs à l'intégration de code ``html`` ! On perd en cohérence et un document en markdown n'est plus vraiment en markdown.

.. toctree::
   :maxdepth: 2
   :hidden:

   content/syntaxe.rst
   content/balises.rst
   content/directives.rst
