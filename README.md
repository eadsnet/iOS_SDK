# EADS iOS SDK
EadsSDK is an ad network sdk written in Swift. Also, it's completely compatible with Objective-C projects.

- [Features](#features)
- [Who Uses It](#who-uses-it)
- [Requirements](#requirements)
- [Communications](#communications)
- [Installation](#installation)
- [How To Use](#how-to-use)
- [Credits](#credits)

## Features
- [x] Native banner ad in four sizes
- [x] Native Fullscreen banner ad
- [x] Video ad with native banner
- [x] Fullscreen video ad with optional banner ad

## Who Uses It
- Anyone who has an iOS application can register for this sdk in our website. We will provide step by step guide for you.

## Requirements
- iOS 8.0+ 
- Xcode 8.3+
- Swift 3.1+

## Communications
- If you **need help with SDK**, contact us from our [website](https://eads.ir/mobads/guide).
- If you need **a SDK feature**, open a feature request.
- If you'd like to **discuss SDK best practices**, use our [website](https://eads.ir/mobads/guide).
- If you **found a bug**, open an issue and follow the guide. The more detail the better!

## Installation

### CocoaPods
[CocoaPods](https://cocoapods.org/) is a dependency manager for Cocoa projects. You can install it with the following command:

```
$ gem install cocoapods
```

CocoaPods 1.1+ is required to build eadsSDK.
To integrate SDK into your Xcode project using CocoaPods, specify it in your Podfile:

```
source 'https://github.com/CocoaPods/Specs.git'
platform :ios, '8.0'
use_frameworks!

target '<Your Target Name>' do
    pod 'eadsSDK'
end
```
Then, run the following command:

```
$ pod install
```

### Manually
If you prefer not to use any of the aforementioned dependency managers, you can integrate SDK into your project manually.

## How To Use

### Sample Code

- Getting Started
  >You should add these lines of code in **AppDelegate**
  >You change the environment to either Sandbox or Production
   - *Objective-C*
     ```objective-c
     - (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
         ARConfig *config = [[ARConfig alloc] initWithAppToken:@""##YOUR_APP_TOKEN##"" environment:AREnvironmentProduction];
         [AroundAd didLaunchWith: config];
         return YES;
     }
     ```
   - *Swift*
     ```swift
     func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions:      [UIApplicationLaunchOptionsKey: Any]?) -> Bool {
        let config = ARConfig(appToken: "##YOUR_APP_TOKEN##", environment: .Production)
        AroundAd.didLaunch(with: config)
        return true
     }
     ```
- Native banner 
   - *Objective-C*
     ```objective-c
     _nativeBannerAd = [[ARNativeBannerView alloc] initWithFrame:CGRectMake size:ARBannerSizeBANNER_320x50 zone:ZoneAll];
     _nativeBannerAd.delegate = self;
     [self.view addSubview:_nativeBannerAd];
     [_nativeBannerAd execute];
     
      _nativeBannerAd.clicked = ^{
        NSLog(@"Native banner clicked.");
     };
     ```
   - *Swift*
     ```swift
     let nativeBannerAd = ARNativeBannerView(frame: CGRect, size: .BANNER_320x50)
     nativeBannerAd.delegate = self
     view.addSubview(nativeBannerAd)
     nativeBannerAd.execute()
     
     nativeBannerAd.clicked = { () -> Void in
         print("Native banner clicked.")
     }
     ```
- Fullscreen native banner
   - *Objective-C*
     ```objective-c
     ARFullscreenBannerView *banner = [[ARFullscreenBannerView alloc] initWithZone:ZoneAll];
     banner.delegate = self;
     [banner execute];
     
     banner.clicked = ^{
        NSLog(@"Fullscreen banner clicked.");
     };
     ```
   - *Swift*
     ```swift
     let banner = ARFullscreenBannerView()
     banner.delegate = self
     banner.execute()
     
     banner.clicked = { () -> Void in
         print("Fullscreen banner clicked.")
     }
     ```
- Video ad
   - *Objective-C*
     ```objective-c
     _nativeVideoBannerAd = [[ARNativeVideoAd alloc] initWithFrame:CGRectMake zone:ZoneAll cache:FALSE];
     _nativeVideoBannerAd.delegate = self;
     [self.view addSubview:_nativeVideoBannerAd];
     [_nativeVideoBannerAd execute];
     
     _nativeVideoBannerAd.clicked = ^{
        NSLog(@"Video banner clicked.");
     };
     ```
   - *Swift*
     ```swift
     let nativeVideoBannerAd = ARNativeVideoAd(frame: CGRect)
     nativeVideoBannerAd.delegate = self
     view.addSubview(nativeVideoBannerAd)
     nativeVideoBannerAd.execute()
     
     nativeVideoBannerAd.clicked = { () -> Void in
         print("Video banner clicked.")
     }
     ```
- Fullscreen video banner
   - *Objective-C*
     ```objective-c
     ARFullscreenVideoAd *banner = [[ARFullscreenVideoAd alloc] initWithZone:ZoneAll cache:FALSE];
     banner.delegate = self;
     [banner execute];
     
     banner.clicked = ^{
        NSLog(@"Fullscreen video banner clicked.");
     };
    
     banner.viewCompleted = ^{
        NSLog(@"Fullscreen video banner content did finish displaying.");
     };
     ```
   - *Swift*
     ```swift
     let banner = ARFullscreenVideoAd(zone: .All)
     banner.delegate = self
     banner.execute()
     
     banner.viewCompleted = { () -> Void in
         print("Fullscreen video banner content did finish displaying.")
     }
        
     banner.clicked = { () -> Void in
         print("Fullscreen video banner clicked.")
     }
     ```

### Ad Protocol
    - func aroundAd(_ adView: ARAdView, didCompleteWithError error: SplitError?)
    - func aroundAd(_ adView: ARAdView, ARAdDidFinishLoadWithTag tag: Int, contentAvailable: Bool)
    - func aroundAd(_ adView: ARAdView, didDismissWithTag tag: Int)
    - func aroundAd(_ adView: ARAdView, willDismissWithTag tag: Int) -> Bool


## Credits
eadsSDK is owned and maintained by the Eads Electronic Advertising Agency.

### Security Disclosure
If you believe you have identified a security vulnerability with SDK, you should report it as soon as possible via email to dev@eads.ir. Please do not post it to a public issue tracker.
