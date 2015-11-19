This document explain how to complete a development environment for building mobile apps with Cordova

#Development environment (Client Mobile)

First visit https://github.com/chinook2/Chinook2/blob/master/client/development.md

 - Java JDK : http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html
 - Node.js : https://nodejs.org/en/
 - Cordova : npm install -g cordova
   - you can specify cordova version like this : npm install -g cordova@5.4.0
 - Android SDK : http://developer.android.com/sdk/index.html#Other
 - ADB Driver (optional) : https://github.com/koush/UniversalAdbDriver

Verify SDK Platform (Platform-tools and Build-tools), run the following command :
````
>android
````

You need to select an API version for the SDK.
We recommend to use API 19 (Android 4.4) to have better compatibility... (Not sure !!) and Android SDK Build-tools 21

*IMPORTANT* : Cordova 5.4.x need API 22 !



##Development application installation

To add Cordova support modify your applications app.json builds block as follows :

````
"builds": {
    "classic": {
        "toolkit": "classic",
        "theme": "theme-triton"
    },
    "modern": {
        "toolkit": "classic",
        "theme": "theme-triton",
        "packager": "cordova",
        "cordova": {
            "config": {
               "platforms": "android",
               "id": "com.mydomain.AppDemo"
            }
        }
    }
}
````

 run the following command (optional will be executed on build process the first time) :
 
 ````
 >sencha cordova init com.mycompany.AppDemo AppDemo 
 ````
 
 
 
Building

`````
>sencha app build modern
````


## Options

To show a splash screen ...

````
>cordova\cordova plugin add cordova-plugin-splashscreen
````

config.xml : 

Files are in \ProjectName\cordova\src

````
<platform name="android">
		<icon src="res/icon-hdpi.png" density="ldpi"/>
		<icon src="res/icon-hdpi.png" density="mdpi"/>
		<icon src="res/icon-hdpi.png" density="hdpi"/>
		<icon src="res/icon-hdpi.png" density="xhdpi"/>
		
		<splash src="res/splash-land-xhdpi.png" density="land-xhdpi"/>
		<splash src="res/splash-land-hdpi.png" density="land-hdpi"/>
		<splash src="res/splash-land-hdpi.png" density="land-mdpi"/>
		<splash src="res/splash-land-hdpi.png" density="land-ldpi"/>
		
		<splash src="res/splash-port-xhdpi.png" density="port-xhdpi"/>		
		<splash src="res/splash-port-hdpi.png" density="port-hdpi"/>
		<splash src="res/splash-port-hdpi.png" density="port-mdpi"/>
		<splash src="res/splash-port-hdpi.png" density="port-ldpi"/>
</platform>
<preference name="SplashScreen" value="screen" />
<preference name="SplashScreenDelay" value="10000" />
````

In Application.js to hide the screen when app is ready : 

````
launch: function () {
		// Cordova splashscreen
		if(navigator.splashscreen) navigator.splashscreen.hide();
````
