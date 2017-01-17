Useful snippets for Cocoapods

## Install from podspec file

I had to install a beta version of Mapbox. I am using Cocoapods to install the Mapbox iOS SDK. I have a line in my Podfile with 
`pod 'Mapbox-iOS-SDK'`

This beta version said the following: 

```
To install this prerelease via CocoaPods, point your Podfile to either of these URLs:

    https://raw.githubusercontent.com/mapbox/mapbox-gl-native/ios-v3.4.0-beta.7/platform/ios/Mapbox-iOS-SDK.podspec
    https://raw.githubusercontent.com/mapbox/mapbox-gl-native/ios-v3.4.0-beta.7/platform/ios/Mapbox-iOS-SDK-symbols.podspec.
```

To get this podspec file in your Podfile and install that version from it you have to add this: 

`pod 'Mapbox-iOS-SDK', :podspec => 'https://raw.githubusercontent.com/mapbox/mapbox-gl-native/ios-v3.4.0-beta.7/platform/ios/Mapbox-iOS-SDK.podspec'`

So basically **name of the pod**, *:podspec =>* **URL of the podspec file**

If you have that *.podspec* file in local, you can use `:path =>`since that command searches in the local filesystem.