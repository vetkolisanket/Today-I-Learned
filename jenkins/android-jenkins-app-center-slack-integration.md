# Build Android app on jenkins and notify on slack

## Build apk

- Select Freestyle project
- Make sure git and gradle plugins are installed
- Add appropriate description for your project
- Select discard old builds and select no. of days for which to keep the build or no. of builds to keep as per your requirement
- In source code management select git. Enter repository url and credentials if needed. Specify the branch you would like to build (e.g. */develop)
- In Build section, select 'Use Gradle Wrapper' 
- In tasks to build apk add 'clean assemble< Build Variant >< Build Type >' (e.g. clean assembleStagingDebug)
  
## To run unit tests
  
- To run unit tests 'test< Build Variant >< Build Type >UnitTest' (e.g. testStagingDebugUnitTest)
  
## To upload build to app center
  
- In your app's app center account, go to settings -> app api tokens and create a token which you'll be using in Jenkins
- In Jenkins click add post build action -> select Upload app to AppCenter -> add the token copied from app center to Api Token field
- Add the owner name and app name, path to apk in path to app field, add the appropriate distribution group, select notify testers

## Enable slack notifications

- Select 'Slack Notifications' as the post build action
- Select appropriate actions on which you'd like to get notified (e.g. build start, success, failure etc)
- Select appropriate notification message includes
- Select the channel on which you'd like to get notified

[Reference](https://bugfender.com/blog/how-to-add-your-first-android-job-to-jenkins/amp/)
