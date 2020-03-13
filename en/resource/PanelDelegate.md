## iOS Panel SDK Delegate

After implementing the `TuyaSmartPanelSDKDelegate` Delegate, you can receive panel internal event.

#### Click Panel Toolbar Right Menu

**Example** 

```objective-c
#pragma mark - TuyaSmartPanelSDKDelegate

// Click Panel Toolbar Right Menu
- (void)didPressedRightMenu {
  
}
```

#### Get the Panel Router Url

**Parameters**

| Parameter      | Descrpition                 |
| --------- | -------------------- |
| device    | Device Model of the triggered panel |
| group     | Group Model of the triggered panel |
| urlString | The router url |

**Example**

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

**Parameters**

| Parameter   | Description     |
| ------ | -------- |
| device | TuyaSmartDeviceModel |
| group  | TuyaSmartGroupModel |

**Example**

```objective-c
#pragma mark - TuyaSmartPanelSDKDelegate

- (nullable UIViewController *)requireSpecialPanelForDevice:(nullable TuyaSmartDeviceModel *)device orGroup:(nullable TuyaSmartGroupModel *)group {
  
}
```