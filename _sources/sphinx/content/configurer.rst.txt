.. toctree::
   :maxdepth: 1

.. _`sphinx_design`: https://sphinx-design.readthedocs.io/en/latest/
.. _`notebook jupyter`: ../nb/exemple_nb.ipynb
.. _`extension sphinx`: https://www.sphinx-doc.org/en/master/usage/extensions/index.html
.. _`awesome sphinxdoc`: https://github.com/yoloseem/awesome-sphinxdoc

Le fichier de configuration
---------------------------

Pendant la phase d'installation du projet, le fichier de configuration ``conf.py`` a été créé. Les paramètres par
défaut sont les suivants :

.. literalinclude:: ../../conf.py
   :lines: 18-60


.. rubric:: Project information

Le projet est identifié par un nom qui apparaît sur la page web de la documentation, en haut du volet latéral. Pour le
reste, les informations de copyright et le nom de l'auteur apparaissent dans le pied de page.

.. rubric:: General configuration

#. Des extensions sont disponibles pour ajouter des contenus dans la documentation. Ces extensions sont associées à des
   modules Python à installer avec la commande ``pip``.

   -  ``sphinx_design`` est une extension qui permet de modifer l'apparence des contenus grâce à des règles de style en
      ``css``. Ces règles sont ajoutées dans les documents sources en utilisant la syntaxe des directives reST. Plus
      d'informations sur le site `sphinx_design`_.

   -  ``nbsphinx`` est une extension qui permet d'intégrer des notebook jupyter dans votre documentation. Par exemple,
      le lien suivant renvoie vers un notebook : `notebook jupyter`_

   D'autres extensions sont disponibles et présentées sur les sites `extension sphinx`_ et `awesome sphinxdoc`_.
