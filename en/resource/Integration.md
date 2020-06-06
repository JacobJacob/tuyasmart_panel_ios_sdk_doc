## Integration

### Using CocoaPods

Add the following content in file `Podfile`:

```ruby
source "https://github.com/TuyaInc/TYPublicSpecs.git"
source 'https://cdn.cocoapods.org/'

platform :ios, '9.0'

target 'your_target_name' do
   pod "TuyaSmartPanelSDK"
   # If you need the sweeper, please rely on the relevant plug-in of the sweeper
   pod "TuyaRNApi/Sweeper"
end
```

Execute command `pod update` in the project's root directory to begin integration.

For the instructions of CocoaPods, please refer to: [CocoaPods Guides](https://guides.cocoapods.org/) 

### Initializing SDK

1. Open project setting, `Target => General`, edit `Bundle Identifier` to the value from Tuya develop center.
2. Import security image to the project and rename as `t_s.bmp` from [Preparation Work](https://tuyainc.github.io/tuyasmart_home_ios_sdk_doc/en/resource/Preparation.html), then add it into `Project Setting => Target => Build Phases => Copy Bundle Resources`.
3. Add the following to the project file `PrefixHeader.pch`：

```objc
#import <TuyaSmartBaseKit/TuyaSmartBaseKit.h>
#import <TuyaSmartPanelSDK/TuyaSmartPanelSDK.h>
```

Swift project add the following to the `xxx_Bridging-Header.h` file:

```swift
#import <TuyaSmartBaseKit/TuyaSmartBaseKit.h>
#import <TuyaSmartPanelSDK/TuyaSmartPanelSDK.h>
```

1. Open file `AppDelegate.m`，and use the `App Key` and `App Secret` obtained from the development platform in the `[AppDelegate application:didFinishLaunchingWithOptions:]`method to initialize SDK:

**Declaration**

Init SDK

```objc
- (void)startWithAppKey:(NSString *)appKey secretKey:(NSString *)secretKey;
```

**Parameters**

| **Parameter** | **Description** |
| ------------- | --------------- |
| appKey        | App key         |
| secretKey     | App secret key  |

**Example**

Objc:

```objc
[[TuyaSmartSDK sharedInstance] startWithAppKey:<#your_app_key#> secretKey:<#your_secret_key#>];
```

Swift:

```swift
 TuyaSmartSDK.sharedInstance()?.start(withAppKey: <#your_app_key#>, secretKey: <#your_secret_key#>)
```

Now all the prepare work has been completed. You can use the sdk to develop your application now.