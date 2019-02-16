# How to provide sign in hints to the user?

If your app has a sign-in/sign-up option which involves taking users email or phone number, for a better user experience you can use the [Credentials API](https://developers.google.com/identity/smartlock-passwords/android/retrieve-hints) to provide sign-in hints to the user. You can add Credentials API to your app using the below steps:

1. Add the following dependency in your gradle
`'com.google.android.gms:play-services-auth:x.x.x'`
You might also need to setup google-services in your app if you haven't done so already

2. Next implement `GoogleApiClient.ConnectionCallbacks` and `GoogleApiClient.OnConnectionFailedListener` in your LoginActivity.

3. Initialise google sign-in options and google api client.
```
val gso = GoogleSignInOptions.Builder(GoogleSignInOptions.DEFAULT_SIGN_IN)
  .requestEmail()
  .build()

val googleApiClient = GoogleApiClient.Builder(this)
  .addConnectionCallbacks(this)
  .enableAutoManage(this, this)
  .addApi(Auth.GOOGLE_SIGN_IN_API, gso)
  .addApi(Auth.CREDENTIALS_API)
  .build()
```

4. Next use this google api client to construct a hint request object
```
val hintRequest = HintRequest.Builder()
  .setHintPickerConfig(
    CredentialPickerConfig.Builder()
      .setShowCancelButton(true)
      .setPrompt(CredentialPickerConfig.Prompt.SIGN_IN)
      .build()
    )
    .setEmailAddressIdentifierSupported(true)
//  .setPhoneNumberIdentifierSupported(true)
    .build()
```

5. Next request for hint requests by calling `startIntentSenderForResult()`
```
val intent = Auth.CredentialsApi.getHintPickerIntent(googleApiClient, hintRequest)
  try {
    startIntentSenderForResult(intent.intentSender, Companion.RC_HINT_REQUEST, null, 0, 0, 0)
  } catch (e: IntentSender.SendIntentException) {
    emailHintRequestFailure(e)
  }
  
private fun emailHintRequestFailure(e: IntentSender.SendIntentException) {
  snack(getString(R.string.error_suggesting_email_hint) + e.localizedMessage)
}
```

6. Finally you will get the requested `email` or `phone number` in onActivityResult
```
    override fun onActivityResult(requestCode: Int, resultCode: Int, data: Intent?) {
        super.onActivityResult(requestCode, resultCode, data)

        when (requestCode) {
            RC_HINT_REQUEST -> handleEmailHintRequestResolution(resultCode, data)
        }
    }

    private fun handleEmailHintRequestResolution(resultCode: Int, data: Intent?) {
        if (resultCode == AppCompatActivity.RESULT_CANCELED) {
            emailHintRequestCancelled()
        } else {
            emailHintRequestSuccess(data)
        }
    }

    private fun emailHintRequestCancelled() {
        // do nothing
    }

    private fun emailHintRequestSuccess(data: Intent?) {
        val credential: Credential? = data?.getParcelableExtra(Credential.EXTRA_KEY)
        credential?.let {
            setEmail(it.id)
        }
    }

    private fun setEmail(id: String) {
        etEmail.setText(id)
    }
```
