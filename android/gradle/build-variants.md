# How to have build variants for different stages of development?

Android Studio and Gradle by default provides `release` and `debug` build types which appear in your build variants without you having to do anything.

    buildTypes {
        release {
            minifyEnabled true
            shrinkResources true
            proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'

            signingConfig signingConfigs.production
            debuggable false
        }
        debug {
            minifyEnabled false
            shrinkResources false
            proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'

            signingConfig signingConfigs.production
            debuggable true
        }
    }
    
You can extend onto this to provide a `mock` build type variant so that now you can have mock variant for writing your tests (if you write them that is :stuck_out_tongue_winking_eye:), debug for staging and release for production.

## todo use product flavors to have an even better build variant combination
