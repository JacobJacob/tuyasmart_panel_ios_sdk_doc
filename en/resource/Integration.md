## Fast Integration

### Use CocoaPods for quick integration

Add the following content in the `Podfile` file.

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

Then run the `pod update` command in the root directory of project.
For use of CocoaPods, please refer to the [CocoaPods Guides](https://guides.cocoapods.org/) It is recommended to update the CocoaPods to the latest version.

## Integrated SDK

### Import Header

Add the following header in Use for Objective-C project:

```objective-c
#import <TuyaSmartPanelSDK/TuyaSmartPanelSDK.h>
```

Add the following Bridge Header in Use for Swift project: 

```swift
#import <TuyaSmartPanelSDK/TuyaSmartPanelSDK.h>
```

Add the following header in Use for Swift project:

```swift
import TuyaSmartPanelSDK
```

