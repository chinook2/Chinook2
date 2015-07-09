#Environnement de développement

- Tortoise git : https://tortoisegit.org
- Install git : https://git-scm.com/downloads
- Sencha cmd : https://www.sencha.com/products/extjs/cmd-download/
  - http://cdn.sencha.com/cmd/6.0.0.202/jre/SenchaCmd-6.0.0.202-windows-32bit.zip
- Sencha Ext JS 6 GPL : https://www.sencha.com/legal/GPL/
  - http://cdn.sencha.com/ext/gpl/ext-6.0.0-gpl.zip

Installer Sencha CMD de préférence dans C:\Sencha\Cmd et extJS dans C:\Sencha\ext-6.0.0


##Installation de l’application de développement 

Ajout de l’application
```
>sencha -sdk /Sencha/ext-6.0.0 generate app AppDemo ck-appdemo
```

Edite le fichier : ck-appdemo\app.json
````
"requires": [
    "font-awesome",
    "ck-viewer"
],
````

Editer le fichier : ck-appdemo\classic\src\view\main\Main.js
````
Ext.define('AppDemo.view.main.Main', {
    extend: 'ck.View',
    xtype: 'app-main'
});
````

Supprimer le dossier : ck-appdemo\classic\sass\src\view

Option : ajouter dans le fichier ck-appdemo\.sencha\app\sencha.cfg
````
skip.slice=1
````

##Installation des sources des packages

Créer le dossier : ck-appdemo\packages\local

Se placer dans le dossier ck-appdemo\packages\local et lancer via TortoiseGit la commande Git clone 

Url du dépôt : https://github.com/chinook2/ck-viewer
 

Lancer l’application
````
>cd ck-appdemo
ck-appdemo>sencha app watch
````

Ouvrir le navigateur 
http://localhost:1841/

Note : pour travailler en temps réel sur les CSS : http://localhost:1841/?platformTags=fashion:true 

Compiler l’application
````
ck-appdemo>sencha app build
````
