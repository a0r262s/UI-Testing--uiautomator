This is the project related to UI Testing regarding to this (http://developer.android.com/tools/testing/testing_ui.html)
The project is SkeletonApp from ~\Android\android-sdk\samples\android-17\SkeletonApp

Environment Specs:

Android Studio Preview 0.5.0 Build #AI-134.1058404

SDK API 17

Ant apache-ant-1.9.3-bin

JDK 1.7.0-b147 amd 64

To create UI Tester for sample project SkeletonApp in Android Studio, this project can be helpful. 
There were lots of errors b/c of conflicts of old project structure to Android Studio. 
For example : Just 'opening' the project in Android Studio, and following the instructions from UI Testing, 'Package R does not exist' error was occured. 
And then 'Importing' project, the error was "[dx] no classfiles specified".
I googled for these issues and it was hints that I tried but none was helpful. 
Then by following the steps below the errors and problems have been solved. 

Import project SkeletonApp in Android Studio with the default settings. Nothing has been changed.

in Terminal from Android Studio:

\tools>	android update project --path ~\SkeletonApp2\app\src\main --subprojects --target android-17

~\SkeletonApp2\app\src\main>	ant debug

\tools>	android create uitest-project -n SkeletonApp -t 1 -p ~\SkeletonApp2\app\src\androidTest\java\com\example\android\skeletonapp

Copy in Android Studio ~\SkeletonApp2\app\bin to ~\SkeletonApp2\app\src\androidTest\java\com\example\android\skeletonapp

~\SkeletonApp2\app\src\androidTest\java\com\example\android\skeletonapp>	ant build

Connect your Android device to your development machine

~\android-sdk\platform-tools>adb push ~\SkeletonApp2\app\src\androidTest\java\com\example\android\skeletonapp\bin\SkeletonApp.jar /data/local/tmp/

~\android-sdk\platform-tools> adb shell uiautomator runtest SkeletonApp.jar -c com.example.android.skeletonapp.SkeletonAppTest
