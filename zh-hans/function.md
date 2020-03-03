### 关于面板跳转

面板默认基于 navigator push 进行跳转，调用时 sdk 会选择最当前 app 最顶上的 vc 进行跳转
**注意:** 面板 VC 使用 React-Native 渲染，会隐藏 NavigationBar，请在回到自己 VC 时主动调用 self.navigationController.navigationBarHidden = NO

### 进入设备面板

**参数说明**

| 参数       | 说明                                                     |
| ---------- | -------------------------------------------------------- |
| device     | 传入对应的 device 模型                                   |
| completion | 打开面板失败的错误回调（NSError *error：具体参考错误码） |

**代码示例** 

```objective-c
// deviceModel class is TuyaSmartDeviceModel
[TuyaSmartPanelSDK sharedInstance].homeId = deviceModel.homeId; // 必须设定 home id

// 方式一: 默认 Push 方式跳转
[[TuyaSmartPanelSDK sharedInstance] gotoPanelViewControllerWithDevice:deviceModel completion:^(NSError *error) {
     NSLog(@"load error: %@", error);
}];

// 方式二: 使用 Present 方式跳转
[[TuyaSmartPanelSDK sharedInstance] presentPanelViewControllerWithDevice:deviceModel completion:^(NSError *error) {
     NSLog(@"load error: %@", error);
}];
```

### 进入群组面板

**参数说明**

| 参数       | 说明                                                     |
| ---------- | -------------------------------------------------------- |
| group      | 传入对应的 group 模型                                    |
| completion | 打开面板失败的错误回调（NSError *error：具体参考错误码） |

**代码示例** 

```objective-c
//  groupModel class is TuyaSmartGroupModel
[TuyaSmartPanelSDK sharedInstance].homeId = groupModel.homeId; // 必须设定 home id

// 方式一: 默认 Push 方式跳转
[[TuyaSmartPanelSDK sharedInstance] gotoPanelViewControllerWithGroup:groupModel completion:^(NSError *error) {
     NSLog(@"load error: %@", error);
}];

// 方式二: 使用 Present 方式跳转
[[TuyaSmartPanelSDK sharedInstance] presentPanelViewControllerWithGroup:groupModel completion:^(NSError *error) {
     NSLog(@"load error: %@", error);
}];
```

### 面板内事件回调

实现 `TuyaSmartPanelSDKDelegate` 代理协议后，可以接收到面板内部事件变化

```objective-c
// 点击面板右上角事件
- (void)didPressedRightMenu;

// 面板内部路由事件
- (void)tuyaSmartPanelSDK:(TuyaSmartPanelSDK *)tuyaSmartPanelSDK handleOpenURLString:(NSString *)urlString;
```

### 清理面板缓存

面板文件目前会存放在 app 沙盒内，若需要清理可调用此方法

```objective-c
/**
 清理缓存
 */
- (void)clearPanelCache;
```