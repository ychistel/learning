.. documentation

.. toctree:
   :maxdepth: 1

De nombreux scripts Python sont dans les documentations, les cours et exercices. Malheureusement, tous ces scripts donnés à titre d'exemple ne sont pas exécutables. Il existe toutefois un moyen de les rendre exécutables dans la page
web. Cela est devenu possible grâce aux navigateurs qui intègrent le **web assembly**. Cette technologie permet à
partir d'un script compilé d'être directement exécuté par le processeur depuis le navigateur.

La compilation d'un script est toujours un peu délicat à réaliser même si des outils existent et font cela très bien.
Pyodide est une librairie Javascript qui se charge de rendre exécutable un script par le navigateur. On donne ici
quelques éléments pour y parvenir en même temps qu'on découvre cette librairie.

Un premier script
-----------------

Parce qu'il faut bien commencer, on se limite à un cas de base. L'idée est la suivante:

- créer une page web html simple
- appeler la librairie pyodide.js d'en l'entête du fichier
- créer un script javascript exécutant un script python

.. rubric:: la page html

Ici le code html de base de notre page web.

.. literalinclude:: pyodide_1.html
   :language: html

Intégrer la librairie
---------------------

Il faut insérer dans le ``<head>`` de la page html l'appel vers la librairie en utilisant l'url de pyodide dans
l'attribut ``src``.

.. code-block:: html

   <script src="https://cdn.jsdelivr.net/pyodide/v0.22.1/full/pyodide.js"></script>

Suite à cette balise, on peut intégrer le script minimal de base pour exécuter un script Python dans la page web.
Celui-ci calcule la somme ``1+2`` et affiche le résultat dans la console du navigateur. Pour voir le résultat, il faut
ouvrir les outils de développement du navigateur et afficher la console javascript.

.. code-block:: html

   <script type="text/javascript">
      async function main(){
        let pyodide = await loadPyodide();
        console.log(pyodide.runPython("1 + 2"));
      }
      main();
   </script>

Allez plus loin
---------------

Un résultat qui s'affiche dans la console javascript du navigateur et un script Python réduit à une addition, c'est
plutôt maigre. Il faut donc approfondir et améliorer ces 2 aspects. Dans un premier temps, gérons l'affichage dans la
page web.
