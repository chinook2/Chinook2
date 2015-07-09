#Mise en ligne des packages

Initialise le repo local (adapter l'adresse mail)
````
>sencha package repo init -name "Memoris" -email "name@email.com"
````

Build du package (depuis le dossier du package)
````
ck-appdemo\packages\local\ck-viewer>sencha package build
````

Ajoute le package au repo local
````
ck-appdemo\build\ck-viewer>sencha package add ck-viewer.pkg
````

Contrôle que le package soit bien présent dans la liste des packages disponibles.
````
>sencha package list
Sencha Cmd v6.0.0.202
[INF] Listing of global catalog
[INF]    Package ck-viewer
[INF]       2.0.0
````

Upload du package sur le dépôt GitHub (https://github.com/chinook2/Chinook2/tree/gh-pages/pkgs).
* C:\Sencha\Cmd\repo\pkgs\catalog.json
* C:\Sencha\Cmd\repo\pkgs\ck-viewer (le dossier du package).

Commit et push des fichiers.
