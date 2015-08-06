#Créer une nouvelle Application

Ajouter le dépôt distant (et vérification)
````
>sencha repository add ck http://chinook2.github.io/Chinook2/pkgs
>sencha repository list
````

Initialiser une application standard
````
>sencha -sdk /Sencha/ext-6.0.0 generate app AppDemo ck-appdemo
````

Editer le fichier : ck-appdemo\app.json
````
"requires": [
  "font-awesome",
  "ck-viewer"
],
````

Editer le fichier : ck-appdemo\classic\src\view\main\Main.js
````
Ext.define('AppDemo.view.main.Main', {
    extend: 'Ck.View',
    xtype: 'app-main'
});
````

Supprimer le dossier : ck-appdemo\classic\sass\src\view

Build de l’application afin d’intégrer le package ck-viewer (download auto depuis le dépôt distant)
````
ck-appdemo>sencha app build
Sencha Cmd v6.0.0.202
[INF] Processing Build Descriptor : classic
[INF] Downloading : ....................
[INF] Extracting  : ....................
...
````

L’application se lance avec une interface par défaut.


##TODO

Utiliser des templates d’application !
````
sencha generate package ck-app --type TEMPLATE
````

On init alors le repo des packages et on lance
````
sencha generate app --template ck-app AppDemo ./ck-appdemo 
````
