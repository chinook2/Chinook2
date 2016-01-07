Ajouter C:\Program Files (x86)\Universal Adb Driver

This document explain how to complete a development environment for building mobile apps with Cordova.
Path examples are designed for 64 bits environment, for 32 bits replace "Program Files (x86)" by "Program Files"

#Development environment (Client Mobile)

First visit https://github.com/chinook2/Chinook2/blob/master/client/development.md

 - Java JDK : http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html
 - Node.js : https://nodejs.org/en/
 - Cordova : npm install -g cordova
   - you can specify cordova version like this : npm install -g cordova@5.4.0
   if npm command not found check if "C:\Program Files\nodejs" is present in PATH environment variable
 - Android SDK : http://developer.android.com/sdk/index.html#Other
   - prefer to install the SDK here : C:\Program Files (x86)\AndroidSDK
 - ADB Driver (optional) : https://github.com/koush/UniversalAdbDriver

Verify SDK Platform (Platform-tools and Build-tools), run the following command :
````
>android
````

If it doesn't work check if the following path is present in the PATH environment variable : C:\Program Files (x86)\AndroidSDK\tools

You need to select an API version for the SDK.
We recommend to use API 19 (Android 4.4) to have better compatibility... (Not sure !!) and Android SDK Build-tools 21

If an error occured for the installation re-run the SDK Manager as administrator (right click, "Run as administrator")

*IMPORTANT* : Cordova 5.4.x need API 22 !
For API 19 use Cordova x.x.x



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

If an android device is properly configured you can directly run the application with

`````
>sencha app run android
````

To list connected device what can directly host the applicaiton use

`````
>adb devices
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
