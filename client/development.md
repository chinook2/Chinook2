#Environnement de développement (Client)

- Tortoise git : https://tortoisegit.org
- Install git : https://git-scm.com/downloads
- Sencha cmd : https://www.sencha.com/products/extjs/cmd-download/
  - http://cdn.sencha.com/cmd/6.0.0.202/jre/SenchaCmd-6.0.0.202-windows-32bit.zip
- Sencha Ext JS 6 GPL : https://www.sencha.com/legal/GPL/
  - http://cdn.sencha.com/ext/gpl/ext-6.0.0-gpl.zip

Installer Sencha CMD de préférence dans C:\Sencha\Cmd et extJS dans C:\Sencha\ext-6.0.0


##Installation de l’application de développement 

Ajout de l’application dans le dossier C:/projets/chinook2
```
>cd C:/projets/chinook2
>sencha -sdk C:/Sencha/ext-6.0.0 generate app AppDemo ck-appdemo
```
La commande "sencha generate app" génère une application de démo de Ext.  
L'option "-sdk [...]" indique l'emplacement de la librairie Ext. Si l'option est absente la version "trial" d'Ext sera téléchargée  
L'option "AppDemo" indique le nom de l'applicaiton  
L'option "ck-appdemo" indique dans quel dossier l'application doit être créée  

Edite le fichier : ck-appdemo\app.json
````
"requires": [
    "font-awesome",
    // Chinook Package
    "ck-viewer"
],

"development": {
    // Allow debug in dev mode. Keep breakpoint on page reload.
    "loader": {
        "cache": "${build.timestamp}"
    },
    ///
    "tags": [
        // You can add this tag to enable Fashion when using app watch or
        // you can add "?platformTags=fashion:1" to the URL to enable Fashion
        // without changing this file.
        //
        // "fashion"
    ]
},
````
En ajoutant "ck-viewer" on ajoute une dépendance => l'application aura besoin du package "ck-viewer" pour fonctionner.

Todo: voir si utile de préciser les paramètres "toolkit" et "theme" !

Editer le fichier : ck-appdemo\classic\src\view\main\Main.js
````
Ext.define('AppDemo.view.main.Main', {
    extend: 'Ck.View',
    xtype: 'app-main'
});
````
Ce fichier contenait la vue principale de l'application. On a donc remplacé la page de démarrage de l'application de démo d'Ext par la vue de notre application.

Supprimer l'ancien style de l'application de démo d'Ext
````
>rmdir /S /Q ck-appdemo\classic\sass\src\view
````

Option : ajouter dans le fichier ck-appdemo\.sencha\app\sencha.cfg
````
skip.slice=1
````
Cela désactive la compatibilité avec les anciens navigateurs, notamment la gestion des arrondis des fenêtres

##Installation des sources des packages

````
>mkdir ck-appdemo\packages\local
>git clone https://github.com/chinook2/ck-viewer ck-appdemo\packages\local\ck-viewer
````


Lancer l’application
````
>cd ck-appdemo
>sencha app watch
````

Ouvrir le navigateur 
http://localhost:1841/

Note : pour travailler en temps réel sur les CSS : http://localhost:1841/?platformTags=fashion:true 

Compiler l’application
````
>sencha app build
````
Cela créé un dossier "production" dans le dossier "build"
