.. _`sphinx_design`: https://sphinx-design.readthedocs.io/en/latest/
.. _`notebook jupyter`: ../nb/exemple_nb.ipynb
.. _`extension sphinx`: https://www.sphinx-doc.org/en/master/usage/extensions/index.html
.. _`awesome sphinxdoc`: https://github.com/yoloseem/awesome-sphinxdoc

Le fichier de configuration
---------------------------

Pendant la phase d'installation du projet, le fichier de configuration ``conf.py`` a été créé. Les paramètres par
défaut sont les suivants :

.. literalinclude:: ../python/conf.py
   :lines: 18-60


.. rubric:: Project information

Le projet est identifié par un nom qui apparaît sur la page web de la documentation, en haut du volet latéral. Pour le
reste, les informations de copyright et le nom de l'auteur apparaissent dans le pied de page.

Les informations sont celles saisies pendant l'installation lancée par la commande ``sphinx-quickstart``.

.. rubric:: General configuration

#. Des extensions sont disponibles pour ajouter des contenus dans la documentation. Ces extensions sont associées à des modules Python à installer avec la commande ``pip``. La variable ``extensions`` contient dans une liste python les noms des extensions installées et à utiliser pour le projet.

   -  ``sphinx_design`` est une extension qui permet de modifer l'apparence des contenus grâce à des règles de style en
      ``css``. Ces règles sont ajoutées dans les documents sources en utilisant la syntaxe des directives reST. Plus
      d'informations sur le site `sphinx_design`_.

   -  ``nbsphinx`` est une extension qui permet d'intégrer des notebook jupyter dans votre documentation. Par exemple,
      le lien suivant renvoie vers un notebook : `notebook jupyter`_

   D'autres extensions sont disponibles et présentées sur les sites `extension sphinx`_ et `awesome sphinxdoc`_.

#. Il est possible de modifier l'apparence des pages ``html`` proposée par le thème. Ces fichiers sont placés dans le dossier ``_templates`` dont le chemin d'accès est indiqué dans la variable ``template_path``.
#. La variable ``language`` contient la langue utilisée et saisie à l'installation avec la commande ``sphinx-quickstart``.
#. Lors de l'exportation en ``html`` ou en ``latex``, certains dossiers ou fichiers peuvent être ignorés. Ils sont indiqués dans une liste python enregistrée dans la variable ``exclude_pattens``.

.. rubric:: Options for HTML output

#. La première variable ``html_theme`` contient le thème graphique utilisée pour l'affichage des pages html. Il est possible de changer de thème si celui proposé par défaut ne convient pas. C'est donc dans cette variable que la modification se fait. Les thèmes sont des modules python et doivent être installés avec la commande ``pip``. 

   .. admonition:: Exemple

      Le theme **Read the doc** est un thème proposé par la plateforme de contenu du même nom. Pour l'appliquer à notre projet, il faut donc installer le module ``sphinx-rtd-theme`` :

      .. code::

         pip install sphinx-rtd-theme

      Puis modifier la variable ``html_theme`` dans le fichier de configuration ``conf.py``:

      .. code::

         html_theme = 'sphinx_rtd_theme'

      Attention, le nom du module contient des tirets du 6 alors que le nom du theème contient des soulignés du 8!

   .. note::

      Pour le projet de documentation que vous lisez, j'ai opté pour le thème ``sphinx_book_theme`` qui s'installe avec le module python ``sphinx-book-theme``

#. La variable ``html_static_path`` contient la liste des dossiers contenant des fichiers supplémentaires à appliquer aux pages web créées. Si on souhaite apporter des règles **css** supplémentaires ou des scripts **javascript** pour modifier le comportement des pages web, c'est dans ce dossier qu'il faut les installer. La variable ``html_static_path`` contient le nom du dossier dans lequel se trouve ces fichiers. Par défaut, le dossier est ``_static`` et il est fortement conseillé de ne pas le modifier.

.. rubric:: Options for LaTeX output

Les paramètres d'exportation en ``latex`` peuvent être modifiés. Absents du fichier créé à l'installation, c'est dans le fichier de configuration ``conf.py`` qu'ils devront être ajoutés. 

.. _`options latex`: https://www.sphinx-doc.org/en/master/usage/configuration.html#latex-options

Plus d'information sur le site de la documentation sphinx et les `options latex`_.
