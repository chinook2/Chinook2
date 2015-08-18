This document explain how to deploy the application in production

#Create a new application

Add remote repository and check it
````
>sencha repository add ck http://chinook2.github.io/Chinook2/pkgs
>sencha repository list
````

Initialize a standard application
````
>sencha -sdk /Sencha/ext-6.0.0 generate app AppDemo ck-appdemo
````

Edit the file : ck-appdemo\app.json
````
"requires": [
  "font-awesome",
  "ck-viewer"
],
````

Edit the file : ck-appdemo\classic\src\view\main\Main.js
````
Ext.define('AppDemo.view.main.Main', {
    extend: 'Ck.View',
    xtype: 'app-main'
});
````

Remove directory : ck-appdemo\classic\sass\src\view

Application build to integrate the ck-viewer package (auto download from remote repository)
````
ck-appdemo>sencha app build
Sencha Cmd v6.0.0.202
[INF] Processing Build Descriptor : classic
[INF] Downloading : ....................
[INF] Extracting  : ....................
...
````

The application starts with a default interface.


##TODO

Use application templates !
````
sencha generate package ck-app --type TEMPLATE
````

Repository initialization and launching
````
sencha generate app --template ck-app AppDemo ./ck-appdemo 
````
