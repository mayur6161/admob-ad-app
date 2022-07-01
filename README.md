Installing
Versions
Scores
Looking for Maintainers.
Unfortunately I haven't been able to keep up with demand for features and improvments. If you are interested in helping maintain this repo please create an issue requesting maintainer status. Or consider using the new google_mobile_ads by Google.

admob_flutter
Build Status version version GitHub stars GitHub forks GitHub issues

Demo

A Flutter plugin that uses native platform views to show Admob banner ads!

This plugin also has support for Interstitial and Reward ads.

Installation
Add this to your package's pubspec.yaml file:
dependencies:
  admob_flutter: "<LATEST_VERSION>"

Install it - You can install packages from the command line:
flutter pub get
Android Specific Setup
Update your AndroidManifest.xml
Add your AdMob App ID to your app's AndroidManifest.xml file by adding the <meta-data> tag shown below. You can find your App ID in the AdMob UI. For android:value insert your own AdMob App ID in quotes, as shown below.

You can use these test App ID's from Admob for development:

Android: ca-app-pub-3940256099942544~3347511713
iOS: ca-app-pub-3940256099942544~1458002511
<manifest>
  <application>
    <meta-data
      android:name="com.google.android.gms.ads.APPLICATION_ID"
      android:value="ca-app-pub-3940256099942544~3347511713"/>
  </application>
</manifest>
iOS Specific Setup
Update your Info.plist per Firebase instructions.

<key>GADApplicationIdentifier</key>
<string>ca-app-pub-3940256099942544~1458002511</string>
and add

<key>io.flutter.embedded_views_preview</key>
<true/>
Starting from Beta 6, you also need to display the App Tracking Transparency authorization request for accessing the IDFA, so you have to update your Info.plist to add the NSUserTrackingUsageDescription key with a custom message describing your usage. Below is an example description text:

<key>NSUserTrackingUsageDescription</key>
<string>This identifier will be used to deliver personalized ads to you.</string>
See Prepare for iOS 14+ for more information. You also need to update your ios/Podfile by adding platform :ios, '9.0' at the very top of your file.

Initialize the plugin
First thing to do before attempting to show any ads is to initialize the plugin. You can do this in the earliest starting point of your app, your main function:

import 'package:admob_flutter/admob_flutter.dart';

void main() {
  WidgetsFlutterBinding.ensureInitialized();
  // Initialize without device test ids.
  Admob.initialize();
  // Or add a list of test ids.
  // Admob.initialize(testDeviceIds: ['YOUR DEVICE ID']);
}
If you're using iOS, you may also need to request the tracking authorization in order to display personalized ads:

// Run this before displaying any ad.
await Admob.requestTrackingAuthorization();
Supported Platforms
0.3.0 >= iOS
0.2.0 >= AndroidX
Supported Admob features
Banner Ads
Interstitial Ads
Reward Ads
Native Ads (Coming soon)
Check out the repository Wiki for more info!