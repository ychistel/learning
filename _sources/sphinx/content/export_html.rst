Exporter la documentation en html
=================================

Lorsque les premiers contenus sont rédigés, il faut exporter la documentation au format ``html``. Plusieurs méthodes sont possibles pour réaliser cette compilation.

Avec le fichier ``make``
-----------------------

Lors de la création de la structure avec la commande ``sphinx-quickstart``, le fichier ``make.bat`` a été ajouté. Ce fichier est un exécutable ``windows`` qui lance l'exportation de la documentation dans un autre format.

La procédure est la suivante:

#. Ouvrir une console ou fenêtre de commande ``cmd`` et se placer dans le dossier de la documentation contenant le dossier ``source``.
#. Saisir la commande:

   .. code::

      make html

#. L'exportation se réalise dans le dossier ``build``. Le dossier ``build`` contient alors 2 dossiers : ``doctrees`` et ``html``. Le premier contient l'ensemble des ressources à exporter et le second l'exportation au format html.

   .. figure:: ../img/arbo_html.png
      :align: center
      :class: padding-8 border-style-solid border-width-1 border-radius-8 border-color-blue-light

#. Aller dans le dossier ``html`` et ouvrir le fichier ``index.html`` avec un navigateur.

   .. figure:: ../img/index_html.png
      :align: center
      :class: padding-8 border-style-solid border-width-1 border-radius-8 border-color-blue-light

Avec la commande ``sphinx-build``
---------------------------------

Le programme batch ``make.bat`` n'est finalement qu'un programme qui utilise la commande ``sphinx-build`` avec des paramètres prédéfinis comme le nom du dossier où se trouve les sources de la documentation et le dossier de destination ``build``.

On peut donc utiliser directement la commande ``sphinx-build`` à condition d'ajouter les paramètres nécessaires. La commande assez simple requiert 3 paramètres:

.. code::

   sphinx-build -b format_export dossier_source dossier_destination

Dans notre cas, le format d'export est ``html``, le dossier contenant la documentation est ``source`` et le dossier de destination est ``build``. La commande est donc:

.. code::

   sphinx-build -b html source build

Tous les fichiers de l'export sont directement inclus dans le dossier build, ce qui n'est pas conseillé. 

.. figure:: ../img/arbo_html_2.png
   :align: center
   :class: padding-8 border-style-solid border-width-1 border-radius-8 border-color-blue-light

Pour rassemebler la documentation dans un même dossier, il suffit d'ajouter un nom de dossier après le dossier ``build``. Celui-ci sera créé s'il n'existe pas.

.. code::

   sphinx-build -b html source build/doc

Auto-construction avec ``sphinx-autobuild``
-------------------------------------------

Les 2 méthodes précédentes ne permettent pas de visualiser directement dans le navigateur les modifications apportées à la documentation. Il faut relancer la commande d'export et actualiser le navigateur pour voir les modifications.

Une dernière méthode le permet. Elle s'appuie sur le module Python ``sphinx-autobuild``. Il suffit juste de remplacer la commande ``sphinx-build`` par ``sphinx-autobuild``:

.. code::

   sphinx-autobuild -b html source build/doc

Après la validation de la commande, on remarque qu'un serveur web a été lancé et que la documentation est accessible à l'adresse ``http://127.0.0.1:8000`` ou ``http://localhost:8000``.

.. figure:: ../img/serveur_web.png
   :align: center
   :class: padding-8 border-style-solid border-width-1 border-radius-8 border-color-blue-light

Dans le navigateur, on ouvre un nouvel onglet en  saisissant l'url du serveur local lancé par la commande. 

.. figure:: ../img/index_html_2.png
   :align: center
   :class: padding-8 border-style-solid border-width-1 border-radius-8 border-color-blue-light

Le serveur web met à jour les pages web exportées dès qu'elles sont modifiées. C'est plus confortable et cela permet de corriger aussitôt si les modifications apportées ne sont pas satisfaisantes.