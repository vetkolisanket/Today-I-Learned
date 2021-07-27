# Build Android app on jenkins and notify on slack

- Select Freestyle project
- Make sure git and gradle plugins are installed
- Add appropriate description for your project
- Select discard old builds and select no. of days for which to keep the build or no. of builds to keep as per your requirement
- In source code management select git. Enter repository url and credentials if needed. Specify the branch you would like to build (e.g. */develop)
- In Build section, select 'Use Gradle Wrapper' 
- In tasks to build apk add 'clean assemble<Build Variant><Build Type>' (e.g. clean assembleStagingDebug)
- To run unit tests 'test<Build Variant><Build Type>UnitTest' (e.g. testStagingDebugUnitTest)

[Reference](https://bugfender.com/blog/how-to-add-your-first-android-job-to-jenkins/amp/)
