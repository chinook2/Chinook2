This document explain how to install a development environment

#Development environment (Client)

- Tortoise git : https://tortoisegit.org
- Install git : https://git-scm.com/downloads
- Sencha cmd : https://www.sencha.com/products/extjs/cmd-download/
  - http://cdn.sencha.com/cmd/6.0.2/jre/SenchaCmd-6.0.2-windows-32bit.zip
- Sencha Ext JS 6 GPL : https://www.sencha.com/legal/GPL/
  - http://cdn.sencha.com/ext/gpl/ext-6.0.0-gpl.zip

Install Sencha CMD preferably in C:\Sencha\Cmd\6.x.x and extJS in C:\Sencha\ext-6.0.0 (extract the folder)

Add Git binaries path to the PATH environment variable

##Development application installation

Adding the application in the folder C:/projets/chinook2
```
>cd C:/projets/chinook2
>sencha -sdk C:/Sencha/ext-6.0.0 generate app AppDemo ck-appdemo
```
Command "sencha generate app" generate an Ext demonstration application.

The option "-sdk [...]" point to Ext library. Without this option the "trial" version of Ext is downloaded.

The option "AppDemo" set the application name.

The option "ck-appdemo" point to the folder where the application must be created  

Edit the file : ck-appdemo\app.json
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
By adding "ck-viewer" one dependence is added => the application will require "ck-viewer" package to work.

Todo: check if parameters "toolkit" and "theme" are useful

Edit the file : ck-appdemo\classic\src\view\main\Main.js
````
Ext.define('AppDemo.view.main.Main', {
    extend: 'Ck.View',
    xtype: 'app-main'
});
````
This file point to the main view of the application. We replaced Ext application start page by our application view.

Remove the old Ext application style
````
>rmdir /S /Q ck-appdemo\classic\sass\src\view
````

Optional : add to the file ck-appdemo\\.sencha\app\sencha.cfg
````
skip.slice=1
````
This disable compatibility with old browsers, especially the windows rounded management(it take a while).

##Packages sources installation

````
>mkdir ck-appdemo\packages\local
>git clone https://github.com/chinook2/ck-viewer ck-appdemo\packages\local\ck-viewer
````


Launch the application
````
>cd ck-appdemo
>sencha app watch
````

Run to http://localhost:1841/

Note : to work with non-cached CSS : http://localhost:1841/?platformTags=fashion:true 

Compil application
````
>sencha app build [classic]
````
The "classic" modifier is required when building with Sencha Cmd 6.0.1
This create a "production" directory into "build" folder
