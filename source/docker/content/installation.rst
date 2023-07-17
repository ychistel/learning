installation
============

- Docker desktop qui permet de créer et manager des containers avec une interface graphique.
- En ligne de commande sur un système linux.

EN association avec WSL et VSCODE, cela permet de gérer les conteneurs sans difficulté. L'extension Docker de VScode donne un accès aux conteneurs, y compris ceux installés sur un sous système linux.

Installation de python
----------------------

Sur debian, la version par défaut de Python est 2.7.18. Il est nécessaire d'installer la version 3 de Python et aussi l'outil `pip`d'installation des paquets Python.

.. code-block:: bash

   sudo apt install python
   sudo apt install pip

Après cela, on crée un alias pour que la bonne version de python soit lancée.

Les préférences utilisateurs se trouvent dans le fichier caché `.bashrc`. Dans ce fichier, il est possible d'appliquer les alias qui sont enregistrés dans le fichier `.bash_aliases`. Si celui-ci n'existe pas, on le crée et on ajoute l'alias pour Python.

.. code-block:: bash

   alias python='/usr/bin/python3'

Après l'ajout, on relance le fichier de préférences avec la commande:

.. code-block:: bash

   . .bashrc

On vérifie que l'alias est bien pris en compte avec un contrôle de la version de Python:

.. code-block:: bash

   python --version

Des paquets doivent être installés pour créer un conteneur Flask. On rassemble dans un fichier `requirement.txt` les dépendances et on les installe.

.. code-block:: text

   click==8.0.3
   colorama==0.4.4
   Flask==2.0.2
   itsdangerous==2.0.1
   Jinja2==3.0.3
   MarkupSafe==2.0.1
   Werkzeug==2.0.2
   gunicorn==20.1.0

Puis on les installe avec la commande:

.. code-block:: bash

   sudo pip install -r requirement.txt

Création d'un conteneur
-----------------------

L'objectif est de créer un conteneur qui permet la mise en place d'un serveur web avec Flask et le jeu sur les capitales avec une interface web.

On crée un dossier qui contient l'ensemble des fichiers et dossiers à ajouter à notre conteneur. Tous ces fichiers seront copier dans un dossier `app`du conteneur.

On crée le fichier `Dockerfile` qui permet de créer le conteneur. Celui-ci contient:

.. code-block:: bash

   # start by pulling the python image
   FROM python:3.8-alpine
   
   # copy the requirements file into the image
   COPY ./requirements.txt /app/requirements.txt
   
   # switch working directory
   WORKDIR /app
   
   # install the dependencies and packages in the requirements file
   RUN pip install -r requirements.txt
   
   # copy every content from the local file to the image
   COPY . /app

   # configure the port
   EXPOSE 5000

   # configure the container to run in an executed manner
   ENTRYPOINT [ "python" ]
   
   # fichier à exécuter pour démarrer le serveur web.
   CMD ["serveur.py" ]

Ensuite on crée l'image du conteneur avec la commande:

.. code-block:: bash

   docker image build -t docker_flask .

- `docker_flask` est le nom de l'image à construire
- En fin de ligne, on indique le dossier où se trouve le fichier Dockerfile ; le point indique le dossier où on se trouve.

Avec cette image, on lance notre conteneur en saisissant la commande:

.. code-block:: bash

   docker run -p 5000:5000 -d docker_flask

Enfin on ouvre un navigateur et on saisit l'url `http://localhost:5000`.

L'image que l'on vient de construire peut être déposée sur le dépôt (hub) de docker. La commande qui permet de le faire est la suivante:

.. code-block:: bash

   # on se connecte à son compte
   docker login

   # on pousse l'image sur le dépôt
   docker push login/nom_image
