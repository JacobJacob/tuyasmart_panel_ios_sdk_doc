## 面板事件回调

实现 `TuyaSmartPanelSDKDelegate` 代理协议后，可以接收到面板内部事件变化

#### 点击面板右上角事件

**示例代码** 

```objective-c
#pragma mark - TuyaSmartPanelSDKDelegate

// 点击面板右上角事件
- (void)didPressedRightMenu {
  
}
```

#### 当面板触发短链跳转时触发

**参数说明**

| 参数      | 说明                 |
| --------- | -------------------- |
| device    | 被触发面板的设备实体 |
| group     | 被触发面板的群组实体 |
| urlString | 跳转短链             |

**示例代码**

```objective-c
#pragma mark - TuyaSmartPanelSDKDelegate

// 面板内部路由事件
- (void)tyPanelDevice:(nullable TuyaSmartDeviceModel *)device
              orGroup:(nullable TuyaSmartGroupModel *)group
  handleOpenURLString:(nonnull NSString *)urlString {
    
  }
```

#### 找不到设备对应的面板容器的回调

当找不到设备对应的面板容器时（IPC 面板、原生面板等），需要根据设备实现你自己的面板容器 VC

**参数说明**

| 参数   | 说明     |
| ------ | -------- |
| device | 设备实体 |
| group  | 群组实体 |

**示例代码**

```objective-c
#pragma mark - TuyaSmartPanelSDKDelegate

- (nullable UIViewController *)requireSpecialPanelForDevice:(nullable TuyaSmartDeviceModel *)device orGroup:(nullable TuyaSmartGroupModel *)group {
  
}
```