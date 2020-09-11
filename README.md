# Flutter Google Auth Template

The goal, reduce the friction of starting an app that requires Google auth.

## Getting Started

The instructions below come from the [google_sign_in](https://pub.dev/packages/google_sign_in) package with a few tweaks.

* TODO: Update Android applicatoinId
* TODO: Update iOS bundle ID

Create a project on [Firebase](https://console.firebase.google.com). 
* This will also register your project on [GCP](https://console.developers.google.com) (under the ALL projects tab).

Enable the OAuth APIs that you want, using the [Google Cloud Platform API manager](https://console.developers.google.com/). 

Configure the [OAuth consent screen](https://console.developers.google.com/apis/credentials/consent).
* Setting the logo will require your app to be validated.

### Android Specific

Click the Android icon to register the app.
* SHA certificate fingerprints are required for Google auth.
* You can grab your debug fingerprints like this `keytool -list -v -alias androiddebugkey -keystore ~/.android/debug.keystore`. (Password is blank.)
* You don't need to include the google-services.json file in your app unless you are using Google services that require it.

Troubleshooting `APIException` errors.
* Have the saved the OAuth consent config?
* Have you set SHA certificate fingerprints?

### iOS Specific Steps

Click the iOS icon to register the app.

Download GoogleService-Info.plist.

Open xCode and drag the file into [my_project]/ios/Runner. Accept defaults.

Add this to [my_project]/ios/Runner/Info.plist and update the value.

```xml
<!-- Google Sign-in Section -->
<key>CFBundleURLTypes</key>
<array>
	<dict>
		<key>CFBundleTypeRole</key>
		<string>Editor</string>
		<key>CFBundleURLSchemes</key>
		<array>
			<!-- TODO Replace this value: -->
			<!-- Copied from GoogleService-Info.plist key REVERSED_CLIENT_ID -->
			<string>com.googleusercontent.apps.861823949799-vc35cprkp249096uujjn0vvnmcvjppkn</string>
		</array>
	</dict>
</array>
<!-- End of the Google Sign-in Section -->
```

Note, apps that use login services must also offer a "Sign in with Apple" option when submitting to the Apple App Store. [More info.](https://developer.apple.com/sign-in-with-apple/get-started)
* Consider also using an Apple sign in plugin from pub.dev.
* The Flutter Favorite [sign_in_with_apple](https://pub.dev/packages/sign_in_with_apple) plugin could be an option.
