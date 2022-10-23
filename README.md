# Google Maps Swift Package

Experimental support for Swift Package Manager and ARM64 simulator for Google Maps and Places SDK.

While Google provides XCFrameworks with ARM64 simulator support as a beta release, the frameworks do not work when added as a dependency to Swift Package Manager. Google still offers legacy fat frameworks that can be easily combined into XCFrameworks and used from Swift Package, but they lack support for the ARM64 simulator.

This project rebuilds Google's beta XCFrameworks so they can be added as a dependency to Swift Package, preserving support for the ARM64 simulator, which allows development on Apple Silicon (M1, etc.) computers.

## Requirements

* [iOS 13.0](https://wikipedia.org/wiki/IOS_13) or later.
* [Xcode 13.3.1](https://developer.apple.com/xcode) or later.
  * **Note:** Make sure BitCode is not enabled on your app target build setting (ENABLE_BITCODE = NO). 

## Add as a dependecy to your Swift Package

```swift
dependencies: [
  .package(url: "https://github.com/darrarski/GoogleMaps-SP.git", .upToNextMinor(from: "7.1.0"))
]
```

## Build XCFrameworks yourself

1. Clone this project.
2. Download official XCFrameworks from Google:
  - [GoogleMaps SDK](https://developers.google.com/maps/documentation/ios-sdk/config#install-the-xcframework)
  - [GooglePlaces SDK](https://developers.google.com/maps/documentation/places/ios-sdk/config#install-the-xcframework)
3. Unzip and put downloaded XCFrameworks inside `GoogleFrameworks` directory
4. Run `make_xcframeworks.sh` script.
5. You can find your new XCFrameworks in `Build` directory.

## License & Copyright

The **Google Maps iOS SDK** and **Google Places iOS SDK** libraries are the property of Google and are subject to *Google's Terms of Service*. See [LICENSE.google](LICENSE.google) for details.

This repo is a fork of [YAtechnologies/GoogleMaps-SP](https://github.com/YAtechnologies/GoogleMaps-SP) with some tweeks that adds support for ARM64 simulator.

This repo is provided as is, without any guarantee. It can (hopefully) become obsolete once Google fixes their SDKs.
