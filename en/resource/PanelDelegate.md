## iOS Panel SDK Delegate

After implementing the `TuyaSmartPanelSDKDelegate` Delegate, you can receive panel internal event.

#### Click Panel Toolbar Right Menu

**Sample Code** 

```objective-c
#pragma mark - TuyaSmartPanelSDKDelegate

// Click Panel Toolbar Right Menu
- (void)didPressedRightMenu {
  
}
```

#### Get the Panel Router Url

**Parameter Descrpition**

| Parameter      | Descrpition                 |
| --------- | -------------------- |
| device    | Device Model of the triggered panel |
| group     | Group Model of the triggered panel |
| urlString | The router url |

**代码示例**

```objective-c
#pragma mark - TuyaSmartPanelSDKDelegate

// Route events inside the panel
- (void)tyPanelDevice:(nullable TuyaSmartDeviceModel *)device
              orGroup:(nullable TuyaSmartGroupModel *)group
  handleOpenURLString:(nonnull NSString *)urlString {
    
  }
```

#### The callback for cannot find panel container

When you cannot find the panel container (IPC panel, native panel, etc.) corresponding to the device, you need to implement your own panel container VC according to the device.

**Parameter Description**

| Parameter   | Description     |
| ------ | -------- |
| device | TuyaSmartDeviceModel |
| group  | TuyaSmartGroupModel |

**Sample Code**

```objective-c
#pragma mark - TuyaSmartPanelSDKDelegate

- (nullable UIViewController *)requireSpecialPanelForDevice:(nullable TuyaSmartDeviceModel *)device orGroup:(nullable TuyaSmartGroupModel *)group {
  
}
```