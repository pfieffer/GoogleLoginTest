# Google Login 
> Your best friend Google: https://developers.google.com/identity/sign-in/android/start-integrating

### Setup:
1. In your Android Studio, `Tools>Android>SDK Manager> SDK Tools>Google Play Services` Check this and update.
2. Go to https://developers.google.com/mobile/add?platform=android&cntapi=signin&cnturl=https:%2F%2Fdevelopers.google.com%2Fidentity%2Fsign-in%2Fandroid%2Fsign-in%3Fconfigured%3Dtrue&cntlbl=Continue%20Adding%20Sign-In and obtain `google-services.json` file.
3. You will need to provide a SHA1 fingerprint of your app that talks with the google sign in service. First you need to generate signed apk, in Android Studio `Build>Generate Signed APK>Create new>` Enter directory for the key, passwords wherever asked and the first and last name fields. Note the alias and key name. Then type `keytool -exportcert -list -v -alias <thing_you_put_in_alias> -keystore <directory_to_key>/key.jks` in your terminal. Make sure to enter directory correctly. ie. Home is `~/` in linux
4. Copy the SHA1 fingerprint and put it on the google developers console. Then you should be able to get the `google-services.json` file
5. Clone this repository. Type `git clone https://github.com/pfieffer/GoogleLoginTest.git`
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
buildscripts{
    dependencies{
        //classpath 'com.google.gms:google-services:3.1.2'
        classpath 'com.google.gms:google-services:3.1.0'
    }
}
allprojects{
    // Google Sign In SDK (only required for Google Sign In)
    compile 'com.google.android.gms:play-services-auth:11.6.0'
}
    
```



