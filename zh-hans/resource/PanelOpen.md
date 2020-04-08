## 打开面板

### 关于面板跳转

面板默认基于导航栏压栈方式进行跳转，调用时会选择最当前应用程序最顶上的视图控制器进行跳转
**注意:** 面板视图控制器使用 React-Native 渲染，会隐藏导航栏，请在回到自己的视图控制器时主动调用 `self.navigationController.navigationBarHidden = NO;`

### 进入设备面板

**参数说明**

| 参数       | 说明                                                     |
| ---------- | -------------------------------------------------------- |
| device     | 传入对应的 device 模型                                   |
| completion | 打开面板失败的错误回调（NSError *error：具体参考错误码） |

**示例代码** 

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

| 参数       | 说明                                                       |
| ---------- | ---------------------------------------------------------- |
| group      | 传入对应的群组模型（`TuyaSmartGroupModel`）                |
| completion | 打开面板失败的错误回调（`NSError *error`：具体参考错误码） |

**示例代码** 

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