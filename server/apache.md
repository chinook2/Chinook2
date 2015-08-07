#Configuration Apache

Exemple de configuration apache.

````
# OGC
Alias /wms "C:/projets/chinook2/ck-data/"
Alias /wfs "C:/projets/chinook2/ck-data/"
Alias /geojson "C:/projets/chinook2/ck-data/data/"

<Directory "C:/projets/chinook2/ck-data/">
	Options Indexes FollowSymLinks
	AllowOverride All
	Order allow,deny
	Allow from all
	
	#AddType application/vnd.ogc.se_xml .xml
</Directory>
````

##Rewrite URL

Le fichier .htaccess dans le dossier C:/projets/chinook2/ck-data/

````
RewriteEngine On
RewriteRule ^([A-Za-z0-9-]+)/?$ /cgi-bin/mapserv?map=/projets/chinook2/ck-data/map/$1.map [QSA]
````

Transforme : 

http://localhost:8080/wms/default/?LAYERS=region&amp;VERSION=1.1.0

En :

http://localhost:8080/cgi-bin/mapserv?map=/Projets/__Chinook2/ck-data/map/default.map/?LAYERS=region&VERSION=1.1.0
