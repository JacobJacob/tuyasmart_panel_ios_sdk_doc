## Open Panel

### About Jump to Panel

The panel jumps based on navigation controller push by default. When called, sdk will select the view controller on the top of the current app to jump.
**Note:** React-Native rendering of the panel view controller will hide the Navigation Bar. Please call `self.navigationController.navigationBarHidden = NO;` when you return to your view controller.

### Goto Device Panel

**Parameters**

| Parameter       | Description                                                     |
| ---------- | -------------------------------------------------------- |
| device     | TuyaSmartDeviceModel               |
| completion | Failed to open panel error callback. (NSError *error：Specific reference error code) |

**Example** 

```objective-c
// deviceModel class is TuyaSmartDeviceModel
[TuyaSmartPanelSDK sharedInstance].homeId = deviceModel.homeId; // must be set home id

// Method 1: Jump by default Push method
[[TuyaSmartPanelSDK sharedInstance] gotoPanelViewControllerWithDevice:deviceModel completion:^(NSError *error) {
     NSLog(@"load error: %@", error);
}];

// Method 2: Jump using Present
[[TuyaSmartPanelSDK sharedInstance] presentPanelViewControllerWithDevice:deviceModel completion:^(NSError *error) {
     NSLog(@"load error: %@", error);
}];
```

### Goto Group Panel

**Parameters**

| Parameter       | Description                                                     |
| ---------- | -------------------------------------------------------- |
| group      | TuyaSmartGroupModel                                    |
| completion | Failed to open panel error callback. (`NSError *error`：Specific reference error code) |

**Example** 

```objective-c
//  groupModel class is TuyaSmartGroupModel
[TuyaSmartPanelSDK sharedInstance].homeId = groupModel.homeId; // must be set home id

// Method 1: Jump by default Push method
[[TuyaSmartPanelSDK sharedInstance] gotoPanelViewControllerWithGroup:groupModel completion:^(NSError *error) {
     NSLog(@"load error: %@", error);
}];

// Method 2: Jump using Present
[[TuyaSmartPanelSDK sharedInstance] presentPanelViewControllerWithGroup:groupModel completion:^(NSError *error) {
     NSLog(@"load error: %@", error);
}];
```



## Panel SDK Delegate

After implementing the `TuyaSmartPanelSDKDelegate` Delegate, you can receive panel internal event.

### Click Panel Toolbar Right Menu

**Example** 

```objective-c
#pragma mark - TuyaSmartPanelSDKDelegate

// Click Panel Toolbar Right Menu
- (void)didPressedRightMenu {
  
}
```

### The Callback for Can Not Find Panel Container

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

### Get the Panel Router Url

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



## Clear Panel Cache

The panel resource is currently stored in the app sandbox. You can call this method if you need to clean up:

```objective-c
/**
 * clear cache
 */
- (void)clearPanelCache;
```