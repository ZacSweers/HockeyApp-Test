Here are the results of the spike test:

* In the `app`'s `build.gradle`, I customize the zipaligned APK name to my liking. In this example, I give it a cool name and some extra metadata about the version. [Code here](https://github.com/hzsweers/HockeyApp-Test/blob/master/app/build.gradle#L23-L30)
  * I also print out what the old and new APK names are, for reference later.
* In the plugin's `HockeyAppUploadTask.groovy` file, I added a line to print out what its expected applicationFile name is. [Code here](https://github.com/hzsweers/HockeyApp-Test/blob/master/buildSrc/src/main/groovy/de/felixschulze/gradle/HockeyAppUploadTask.groovy#L71)
* Command used was `./gradlew uploadDebugToHockeyApp`.

With these printlns, I confirmed that while the default name of `app-debug.apk` was renamed to `cool-name-here-debug-1.0-1.apk`, the plugin itself still looks for `app-debug.apk`

    [hsweers@Henris-MacBook-Pro HockeyApp-Plugin-Test (master)]$ gw uploadDebugToHockeyApp
    :gradle-hockeyapp-plugin:compileJava UP-TO-DATE
    :gradle-hockeyapp-plugin:compileGroovy UP-TO-DATE
    :gradle-hockeyapp-plugin:processResources UP-TO-DATE
    :gradle-hockeyapp-plugin:classes UP-TO-DATE
    :gradle-hockeyapp-plugin:groovydoc UP-TO-DATE
    :gradle-hockeyapp-plugin:groovydocJar UP-TO-DATE
    :gradle-hockeyapp-plugin:jar UP-TO-DATE
    :gradle-hockeyapp-plugin:sourceJar UP-TO-DATE
    :gradle-hockeyapp-plugin:signArchives SKIPPED
    :gradle-hockeyapp-plugin:assemble UP-TO-DATE
    :gradle-hockeyapp-plugin:compileTestJava UP-TO-DATE
    :gradle-hockeyapp-plugin:compileTestGroovy UP-TO-DATE
    :gradle-hockeyapp-plugin:processTestResources UP-TO-DATE
    :gradle-hockeyapp-plugin:testClasses UP-TO-DATE
    :gradle-hockeyapp-plugin:test UP-TO-DATE
    :gradle-hockeyapp-plugin:check UP-TO-DATE
    :gradle-hockeyapp-plugin:build UP-TO-DATE
    Old file name is "app-debug.apk"
    New file name is "cool-name-here-debug-1.0-1.apk"
    :app:preBuild
    :app:compileDebugNdk UP-TO-DATE
    :app:preDebugBuild
    :app:checkDebugManifest
    :app:preReleaseBuild
    :app:prepareComAndroidSupportAppcompatV72102Library UP-TO-DATE
    :app:prepareComAndroidSupportSupportV42102Library UP-TO-DATE
    :app:prepareDebugDependencies
    :app:compileDebugAidl UP-TO-DATE
    :app:compileDebugRenderscript UP-TO-DATE
    :app:generateDebugBuildConfig UP-TO-DATE
    :app:generateDebugAssets UP-TO-DATE
    :app:mergeDebugAssets UP-TO-DATE
    :app:generateDebugResValues UP-TO-DATE
    :app:generateDebugResources UP-TO-DATE
    :app:mergeDebugResources UP-TO-DATE
    :app:processDebugManifest UP-TO-DATE
    :app:processDebugResources UP-TO-DATE
    :app:generateDebugSources UP-TO-DATE
    :app:compileDebugJava UP-TO-DATE
    :app:preDexDebug UP-TO-DATE
    :app:dexDebug UP-TO-DATE
    :app:processDebugJavaRes UP-TO-DATE
    :app:validateDebugSigning
    :app:packageDebug UP-TO-DATE
    :app:zipalignDebug UP-TO-DATE
    :app:assembleDebug UP-TO-DATE
    :app:uploadDebugToHockeyApp
    Expected APK file name is "app-debug.apk"
    :app:uploadDebugToHockeyApp FAILED
    
    FAILURE: Build failed with an exception.
    
    * What went wrong:
    Execution failed for task ':app:uploadDebugToHockeyApp'.
    > No appFileNameRegex provided.
    
    * Try:
    Run with --stacktrace option to get the stack trace. Run with --info or --debug option to get more log output.
    
    BUILD FAILED
    
    Total time: 5.321 secs
