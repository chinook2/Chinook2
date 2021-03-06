#Environnement de développement (Serveur)

- PHP : https://www.php.net (>= 5.5)
- composer : https://getcomposer.org/download
- Apigility : https://apigility.org  (1.3.x)
  - Utilise ZendFramework (2.5.x)

##Installation de l’application de développement 

### Apigility
Ajout de l’application dans le dossier C:/projets/chinook2/ck-server
```
>cd C:/projets/chinook2/ck-server
>php -r "readfile('https://apigility.org/install');" | php
```
Quitter via Ctrl+C le serveur built-in.

Déplacer tous les dossiers et fichiers de C:/projets/chinook2/ck-server/apigility vers C:/projets/chinook2/ck-server.

### Configuration d'Apache

Editer le fichier httpd.conf afin d'accéder au module APigility.

Une fois valide l'interface est disponible ici : http://localhost:8888/

````
Listen 127.0.0.1:8888
NameVirtualHost 127.0.0.1:8888
<VirtualHost 127.0.0.1:8888>
    ServerAdmin webmaster@apigility.fr
    
    DocumentRoot "C:/projets/chinook2/ck-server/public/"
    
    ServerName apigility
    
    ErrorLog "logs/apigility.error.log"
    CustomLog "logs/apigility.access.log" common
    
    SetEnv APPLICATION_ENV "development"
    
    <Directory "C:/projets/chinook2/ck-server/public/">
        DirectoryIndex index.php
        AllowOverride All
        Order allow,deny
        Allow from all
    </Directory>   
</VirtualHost>
````

### Modules complémentaires

On peut ajouter les modules complémentaires suivants :

````
>cd C:/projets/chinook2/ck-server
>composer require zfcampus/zf-apigility-documentation-swagger
>composer require zfcampus/zf-apigility-doctrine
````

Swagger (http://swagger.io/) est accessible à l'url : http://localhost:8888/apigility/swagger

###Mise à jour

La commande 'composer update' permet de mettre à jour le module Apigility et toutes ses dépendances (dont le Zend Framework)
````
>cd C:/projets/chinook2/ck-server
>composer update
````

##Installation des sources

````
>cd C:/projets/chinook2/ck-server
>mkdir module\Chinook
>git clone https://github.com/chinook2/ck-server module\Chinook
````

Note : le système ne permet pas de nommer le module 'ck-server' on utilise donc le nom 'Chinook'


Editer le fichier C:\projets\chinook2\ck-server\config\modules.config.php pour ajouter le module Chinook.
````
return array(
    'Application',
    ...
    'ZF\Versioning',
    'Chinook'
);

````

Test du service /about via cette url : http://localhost:8888/about
