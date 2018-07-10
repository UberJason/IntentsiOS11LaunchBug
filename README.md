## IntentsiOS11LaunchBug

[Apple documentation](https://developer.apple.com/documentation/sirikit/creating_an_intents_app_extension) states that watchOS Intent extensions must support a subset of iOS Intents. In this sample project, an iOS intent extension and watchOS intent extension *each support the same, single intent*, but the application fails to deploy to an iOS 11 device, failing with the following error:

```
This app contains a WatchKit app with one or more Siri Intents app extensions that declare IntentsSupported that are not declared in any of the companion app's Siri Intents app extensions. WatchKit Siri Intents extensions' IntentsSupported values must be a subset of the companion app's Siri Intents extensions' IntentsSupported values.
```

I may be doing something wrong, in which case I'm happy to be led in the right direction. My intention here is to run an app that supports Siri shortcuts in iOS 12, but which is also compatible with iOS 11 without Siri shortcuts. For this reason, the iOS Intent and IntentsUI extensions have a deployment target of 12.0, while the watchOS Intent extension has a deployment target of 5.0; the main iOS app and watchOS apps have deployment targets of 11.4 and 4.0, respectively. 

I believe this may be a bug related to the deployment targets. When I change the deployment targets of the Intents extensions to also be iOS 11.4 / watchOS 4.0, the app deploys to an iOS 11 device, but then an attempt to upload a build to App Store Connect results in an "Invalid Binary" related to "Invalid Intent Extension" (which is reasonable, since custom Intents weren't supported in iOS 11.4 / watchOS 4.0). Therefore, I'm stuck 
