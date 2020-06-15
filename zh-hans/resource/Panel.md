## 打开面板

**接口说明**

面板默认基于导航栏压栈方式进行跳转，调用时会选择最当前应用程序最顶上的视图控制器进行跳转
**注意:** 面板视图控制器使用 React-Native 渲染，会隐藏导航栏，请在回到自己的视图控制器时主动调用 `self.navigationController.navigationBarHidden = NO;`

**参数说明**

| 参数 | 说明 |
| --- | --- |
| device | 传入对应的 device 模型 |
| group | 传入对应的群组模型（`TuyaSmartGroupModel`） |
| completion | 打开面板失败的错误回调（`NSError *error`：具体参考错误码） |

**示例代码** 

Objc:

```objc
[TuyaSmartPanelSDK sharedInstance].homeId = homeId; // 必须设定 home id

// 方式一: 默认 Push 方式跳转
[[TuyaSmartPanelSDK sharedInstance] gotoPanelViewControllerWithDevice:deviceModel completion:^(NSError *error) {
     NSLog(@"load error: %@", error);
}];
// Or
[[TuyaSmartPanelSDK sharedInstance] gotoPanelViewControllerWithGroup:groupModel completion:^(NSError *error) {
     NSLog(@"load error: %@", error);
}];

// 方式二: 使用 Present 方式跳转
[[TuyaSmartPanelSDK sharedInstance] presentPanelViewControllerWithDevice:deviceModel completion:^(NSError *error) {
     NSLog(@"load error: %@", error);
}];
// Or
[[TuyaSmartPanelSDK sharedInstance] presentPanelViewControllerWithGroup:groupModel completion:^(NSError *error) {
     NSLog(@"load error: %@", error);
}];
```

Swift:

```swift
TuyaSmartPanelSDK.sharedInstance().homeId = homeId! // 必须设定 home id

// 方式一: 默认 Push 方式跳转
TuyaSmartPanelSDK.sharedInstance().gotoPanelViewController(withDevice: deviceModel!) { (error) in
    print("laod error: \(error)")
}
// Or
TuyaSmartPanelSDK.sharedInstance().gotoPanelViewController(withGroup: groupModel) { (error) in
    print("laod error: \(error)")
}

// 方式二: 使用 Present 方式跳转
TuyaSmartPanelSDK.sharedInstance().presentPanelViewController(withDevice: deviceModel!) { (error) in
    print("laod error: \(error)")
}

TuyaSmartPanelSDK.sharedInstance().presentPanelViewController(withGroup: groupModel!) { (error) in
    print("laod error: \(error)")
}
```



## 面板事件回调

实现 `TuyaSmartPanelSDKDelegate` 代理协议后，可以接收到面板内部事件变化

### 点击面板右上角事件

**示例代码** 

Objc:

```objc
#pragma mark - TuyaSmartPanelSDKDelegate
// 当右上角按钮点击时回调
- (void)tyPanelDidPressedRightMenuWithDevice:(nullable TuyaSmartDeviceModel *)device orGroup:(nullable TuyaSmartGroupModel *)group {
  
}
```

Swift:

```swift
/// 当右上角按钮点击时回调
func tyPanelDidPressedRightMenu(withDevice device: TuyaSmartDeviceModel?, orGroup group: TuyaSmartGroupModel?) {
        
}
```



### 找不到设备对应的面板容器的回调

当找不到设备对应的面板容器时（IPC 面板、原生面板等），需要根据设备实现你自己的面板容器 VC

**参数说明**

| 参数   | 说明     |
| ------ | -------- |
| device | 设备实体 |
| group  | 群组实体 |

**示例代码**

Objc:

```objc
#pragma mark - TuyaSmartPanelSDKDelegate

- (nullable UIViewController *)requireSpecialPanelForDevice:(nullable TuyaSmartDeviceModel *)device orGroup:(nullable TuyaSmartGroupModel *)group {
  
}
```

Swift:

```swift
func requireSpecialPanel(forDevice device: TuyaSmartDeviceModel?, orGroup group: TuyaSmartGroupModel?) -> UIViewController? {
        
}
```



### 获取面板内路由

**参数说明**

| 参数      | 说明                 |
| --------- | -------------------- |
| device    | 被触发面板的设备实体 |
| group     | 被触发面板的群组实体 |
| urlString | 跳转短链             |

**示例代码**

Objc:

```objc
#pragma mark - TuyaSmartPanelSDKDelegate

// 面板内部路由事件
- (void)tyPanelDevice:(nullable TuyaSmartDeviceModel *)device
              orGroup:(nullable TuyaSmartGroupModel *)group
  handleOpenURLString:(nonnull NSString *)urlString {
    
  }
```

Swift:

```swift
func tyPanelDevice(_ device: TuyaSmartDeviceModel?, orGroup group: TuyaSmartGroupModel?, handleOpenURLString urlString: String) {
        
}
```



## 清除所有面板缓存

面板文件目前会存放在应用程序沙盒内，若需要清理可调用此方法

**接口说明**

```objc
/**
 清理缓存
 */
- (void)clearPanelCache;
```

**示例代码**

Objc:

```objc
[[TuyaSmartPanelSDK sharedInstance] clearPanelCache];
```

Swift:

```swift
TuyaSmartPanelSDK.sharedInstance().clearPanelCache()
```

