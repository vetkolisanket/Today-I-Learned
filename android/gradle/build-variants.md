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
        mock {
            minifyEnabled false
            shrinkResources false
            proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'

            signingConfig signingConfigs.production
            debuggable true
        }
    }

A little more complex way would be to use product flavors in combination with build variants to provide an even better build variant.

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

    flavorDimensions "version"

    // If you need to add more flavors, consider using flavor dimensions.
    productFlavors {
        mock {
            manifestPlaceholders = [appName: "MyApp-M"]
            applicationIdSuffix ".debugMock"
            // Assigns this product flavor to the "version" flavor dimension.
            // This property is optional if you are using only one dimension.
            dimension "version"
        }
        staging {
            manifestPlaceholders = [appName: "MyApp-D"]
            applicationIdSuffix ".debug"
            dimension "version"
        }
        prod {
            manifestPlaceholders = [appName: "MyApp"]
            dimension "version"
        }
    }

    // Remove mockRelease and stagingRelease as it's not needed.
    android.variantFilter { variant ->
        if (variant.buildType.name == 'release' && variant.getFlavors().get(0).name != 'prod') {
            variant.setIgnore(true)
        }
    }
    
Now you will have 4 build variants namely prodRelease, prodDebug, stagingDebug and mockDebug.    
