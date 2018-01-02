# Google Login 
> Your best friend Google: https://developers.google.com/identity/sign-in/android/start-integrating

### Setup:
1. In your Android Studio, `Tools>Android>SDK Manager> SDK Tools>Google Play Services` Check this and update.
2. Clone this repository. Type `git clone https://github.com/pfieffer/GoogleLoginTest.git` and change the package name.
3. Go to https://developers.google.com/mobile/add?platform=android&cntapi=signin&cnturl=https:%2F%2Fdevelopers.google.com%2Fidentity%2Fsign-in%2Fandroid%2Fsign-in%3Fconfigured%3Dtrue&cntlbl=Continue%20Adding%20Sign-In and obtain `google-services.json` file.
4. You will need to provide a SHA1 fingerprint of your app that talks with the google sign in service. First you need to generate signed apk, open a terminal in your project's root directory and type `keytool -genkey -v -keystore my-release-key.jks -keyalg RSA -keysize 2048 -validity 10000 -alias my-alias`, this will create a key with name my-release-key.jks and alias my-alias or myKey, look out for it on the terminal. Enter your name(compulsory, i think) for signing in the certificate.
5. Then type `keytool -exportcert -list -v \ -alias <your-alias-name> -keystore my-release-key.jks`. Copy the SHA1 fingerprint and put it on the google developers console. Then you should be able to get the `google-services.json` file. 
6. Move the `google-services.json` file and paste it in your `project_name/app/` directory.
7. Open the project in your Android Studio and run. Good luck, I hope it works!!!

#### If you are here only to setup the dependencies.
`build.gradle` app 
```dependencies{
    // Google Sign In SDK (only required for Google Sign In)
    compile 'com.google.android.gms:play-services-auth:11.6.0'
    }
```
`build.gradle` project
```
buildscript {
    repositories {
        jcenter()
    }
    dependencies {
        classpath 'com.android.tools.build:gradle:2.3.3'

        // NOTE: Do not place your application dependencies here; they belong
        // in the individual module build.gradle files

        //classpath 'com.google.gms:google-services:3.1.2'
        classpath 'com.google.gms:google-services:3.1.0'
    }
}

allprojects {
    repositories {
        jcenter()
        maven { url 'https://maven.google.com' }
    }
}

task clean(type: Delete) {
    delete rootProject.buildDir
}
    
```



