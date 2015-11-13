# apkToSource
Decompile APK Step by Step Guide

**Step 0 – Download APK**

Use this [online tool](http://apps.evozi.com/apk-downloader/) to download your desired APK file from Google Play.

Or pull it from the phone using following commands :-

adb shell pm list packages

adb shell pm path com.example.app

adb pull /data/app/com.example.app/appname.apk


**Step 1 – Download tools**

You will need Java (JRE) and the following tools:

[ApkTool](http://ibotpeaches.github.io/Apktool/)
[Dex2Jar](https://github.com/pxb1988/dex2jar)
[JD-GUI](http://jd.benow.ca/)

**Step 2 – Extract resources**

Open command prompt (or terminal if you’re on linux).
Navigate to the directory where ApkTool is located.
Run the following command (I’m using com.example.app.apk as an example):

**java -jar apktool_2.0.0rc4.jar decode --no-src com.example.app.apk**

Make sure to use your downloaded version of ApkTool.

After the command finishes, a directory named com.example.app will be created in the current directory. It will contain the android manifest file, assets, libraries and all resources. Everything but java sources.

We have specified –no-src in the above command to skip decoding sources, because ApkTool generates smali code instead of java.

**Step 3 – Convert DEX to JAR**

The com.example.app directory will also contain classes.dex file which will be converted to JAR using the Dex2Jar tool.

Extract Dex2Jar archive.
Navigate to Dex2Jar’s directory using the command prompt (or terminal).
Run the following command:
d2j-dex2jar PATH_TO\com.example.app\classes.dex -o PATH_TO\com.example.app\src.jar
Step 4 – Extract Java sources

Run the JD-GUI tool.
Drap and drop the src.jar file onto the JD-GUI window.
Click on File » Save All Sources.
Navigate to where you want to save the sources.
Click save.
Done.
