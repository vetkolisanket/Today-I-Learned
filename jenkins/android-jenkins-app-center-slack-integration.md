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

## Auto-trigger job on push to the repository (bitbucket)
- Go to your job, select. Select 'Generic Webhook Trigger'. Add a token to identify your job in the token field. Copy the complete url alongwith token something like this -> http://JENKINS_URL/generic-webhook-trigger/invoke?token=TOKEN_HERE
- Go to your bitbucket repository. Make sure you have admin access.
- Go to repository settings. Click on Webhooks. Click on add webhook. Enter a title and copy the url you got from your job.
- Select status active. From triggers, make sure push is selected. Save the webhook.
- Your job should trigger now on every push to the repository.

## Auto-trigger job on push to a specific branch
- In you job, below generic web hook trigger in post content parameters. In variable field enter 'branch' as the variable name
- In expression add '$.push.changes[0].new.name'. Select JSONPath
- Now in optional filters in expression enter '^develop$' and in text enter '$branch'to indicate the branch variable we declared in step one.
- Click on save. Now only push to develop branch should trigger your job. 

[Reference](https://bugfender.com/blog/how-to-add-your-first-android-job-to-jenkins/amp/)
