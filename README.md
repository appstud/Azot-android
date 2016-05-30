<p align="center" >
  <img src="https://board.azot.io/img/icons/logo_azot.svg" alt="Azot" title="Azot" width="300" height="300">
</p>

![Platform](https://img.shields.io/badge/platform-android-green.svg)
![Maven](https://img.shields.io/badge/Maven-1.0.0-lightgrey.svg)
[![Facebook](https://img.shields.io/badge/Facebook-Azot%20Ltd-blue.svg)](https://www.facebook.com/uxanalysis)

Azot is a mobile analysis SDK that runs directly inside phones or tablets. This repository holds the framework for the android version of Azot written in Java.

## Features

- [x] Gesture analysis
- [x] Embed feedback
- [x] Crashs analysis
- [x] Sessions analysis
- [x] Heatmaps

##Supported OS & SDK Versions

* Supported build target - android 23
* Earliest supported deployment target - android 18
* Earliest compatible deployment target - android 16

**NOTE**: 'Supported' means that the library has been tested with this version. 'Compatible' means that the library should work on this OS version (i.e. it doesn't rely on any unavailable SDK features) but is no longer being tested for compatibility.

##Thread Safety

Azot uses threading internally to avoid blocking the UI, but none of the Azot external interfaces are thread safe and you should not call any methods on Azot except from the main thread.

##Installation

Repository URL: 

     maven {url 'http://artifactory.toulouse.appstud.me/artifactory/azot-android'}

**Maven**

    <dependency>
      <groupId>io.azot.sdk.android</groupId>
      <artifactId>azot</artifactId>
      <version>1.0</version>
      <type>aar</type>
    </dependency>
    
**Gradle**

    compile('io.azot.sdk.android:azot:1.0@aar')

**Ivy**

     <dependency org="io.azot.sdk.android" name="azot" rev="1.0">
        <artifact name="azot" ext="aar"/>
    </dependency>
    
**Sbt**

    libraryDependencies += "io.azot.sdk.android" % "azot" % "1.0"

**Or**

Install Azot manually into your app by dragging the Azot.aar file into your project. You can download it from <a href="http://artifactory.toulouse.appstud.me/artifactory/azot-android" target="_blank">here</a>

##Start

Add the following code to the onCreate function of your Application class :

    Azot.start(this, "AZOT_APP_TOKEN");
       
  **NOTE**: To get your "AZOT_APP_TOKEN", register <a href="https://board.azot.io" target="_blank">here</a> and create an app.
    
##Important notes

The SDK does not generate videos on simulator.

##Methods

####start:

    public static void start(@NonNull Context context, @NonNull String apiKey)

Start analysis in the app with video and medium confidentiality level. Call it in your app delegate.
It is the only mandatory function that has to be used.

####event: 

    public static void event(String tag)
    
Track events you care about in your app.
    
####feedback:

    public static void feedback(String feedback, String category)

This function is used to collect user feedbacks. The feedbacks will be saved in the session report.
It is the one used in our feedback feature.

####Log:

    public static LogExternal log()

This function prints and saves your logs, simply use Azot.log() instead of Log function.

##Configuration

You can acces sdk parameters through your dashboard on https://board.azot.io

###General Parameters
___

####Use feedback
Activate or desactivate the "shake for feedback" functionality. (Activated by default)

####Session recording
Activate or desactivate session recording. (Activated by default)

####Location recording
Activate or desactivate location tracking. (Activated by default)

####Record on debug mode
If activated only session from apps downloaded through the Appstore will be retrieved. (Activated by default)

####Only upload on wifi
If activated datas will only be sent when the user is connected to wifi. (Desactivated by default)

####Use auto pages tracking
If activated pages will be automatically tracked. (Activated by default)

####Use date range
Allows you to set a date range in which the SDK will be on. (Desactivated by default)

###Video Parameters
___

####Video recording
Activate or desactivate the video. (Desactivated by default)

####Only upload on wifi
If activated videos will only be sent when the user is connected to wifi. (Activated by default)

####Confidentiality
Set the video confidentiality level. (MEDIUM by default)

####Use date range
Allows you to set a date range in which the Video will be on. (Desactivated by default)

###Feedback Parameters
___

####Use feedback
Activate or Desactivate the "Shake for feedback" gesture. (Activated by default)

####Question for your users
Define the question you want us to ask your users on the top of the feedback page.

####Categories
Define different feedback categories. (Max. 5)
