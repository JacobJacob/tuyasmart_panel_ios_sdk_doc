# 快速集成

## 使用 CocoaPods 集成

在 `Podfile` 文件中添加以下内容：

```ruby
source "https://github.com/TuyaInc/TYPublicSpecs.git"
source 'https://cdn.cocoapods.org/'

platform :ios, '9.0'

target 'your_target_name' do
   pod "TuyaSmartPanelSDK"
end
```

然后在项目根目录下执行 `pod update` 命令，集成第三方库。

CocoaPods 的使用请参考：[CocoaPods Guides](https://guides.cocoapods.org/)s.cocoapods.org/)

## 集成 SDK

### 头文件导入

Objective-C 项目在需要使用的地方添加

```objective-c
#import <TuyaSmartPanelSDK/TuyaSmartPanelSDK.h>
```

Swift 请现在 `xxx_Bridging-Header.h` 桥接文件中添加以下内容

```swift
#import <TuyaSmartPanelSDK/TuyaSmartPanelSDK.h>
```

然后在项目在需要使用的地方添加

```swift
import TuyaSmartPanelSDK
```