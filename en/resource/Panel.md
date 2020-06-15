## Open Panel

**Declaration**

The panel jumps based on navigation controller push by default. When called, sdk will select the view controller on the top of the current app to jump.
**Note:** React-Native rendering of the panel view controller will hide the Navigation Bar. Please call `self.navigationController.navigationBarHidden = NO;` when you return to your view controller.

**Parameters**

| Parameter | Description |
| --- | --- |
| device | TuyaSmartDeviceModel |
| group | TuyaSmartGroupModel |
| completion | Failed to open panel error callback. (NSError *error：Specific reference error code) |

**Example** 

Objc:

```objective-c
// deviceModel class is TuyaSmartDeviceModel
[TuyaSmartPanelSDK sharedInstance].homeId = deviceModel.homeId; // must be set home id

// Method 1: Jump by default Push method
[[TuyaSmartPanelSDK sharedInstance] gotoPanelViewControllerWithDevice:deviceModel completion:^(NSError *error) {
     NSLog(@"load error: %@", error);
}];
// Or
[[TuyaSmartPanelSDK sharedInstance] gotoPanelViewControllerWithGroup:groupModel completion:^(NSError *error) {
     NSLog(@"load error: %@", error);
}];

// Method 2: Jump using Present
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
TuyaSmartPanelSDK.sharedInstance().homeId = homeId! // must be set home id

// Method 1: Jump by default Push method
TuyaSmartPanelSDK.sharedInstance().gotoPanelViewController(withDevice: deviceModel!) { (error) in
    print("laod error: \(error)")
}
// Or
TuyaSmartPanelSDK.sharedInstance().gotoPanelViewController(withGroup: groupModel) { (error) in
    print("laod error: \(error)")
}

// Method 2: Jump using Present
TuyaSmartPanelSDK.sharedInstance().presentPanelViewController(withDevice: deviceModel!) { (error) in
    print("laod error: \(error)")
}

TuyaSmartPanelSDK.sharedInstance().presentPanelViewController(withGroup: groupModel!) { (error) in
    print("laod error: \(error)")
}
```



## Panel Delegate

After implementing the `TuyaSmartPanelSDKDelegate` Delegate, you can receive panel internal event.

### Click Panel Toolbar Right Menu

**Example** 

Objc:

```objective-c
#pragma mark - TuyaSmartPanelSDKDelegate

// Click Panel Toolbar Right Menu
- (void)tyPanelDidPressedRightMenuWithDevice:(nullable TuyaSmartDeviceModel *)device orGroup:(nullable TuyaSmartGroupModel *)group {
  
}
```

Swift:

```swift
// Click Panel Toolbar Right Menu
func tyPanelDidPressedRightMenu(withDevice device: TuyaSmartDeviceModel?, orGroup group: TuyaSmartGroupModel?) {
        
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

Objc:

```objective-c
#pragma mark - TuyaSmartPanelSDKDelegate

- (nullable UIViewController *)requireSpecialPanelForDevice:(nullable TuyaSmartDeviceModel *)device orGroup:(nullable TuyaSmartGroupModel *)group {
  
}
```

Swift:

```swift
func requireSpecialPanel(forDevice device: TuyaSmartDeviceModel?, orGroup group: TuyaSmartGroupModel?) -> UIViewController? {
        
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

Objc:

```objective-c
#pragma mark - TuyaSmartPanelSDKDelegate

// Route events inside the panel
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



## Clear Panel Cache

**Declaration**

The panel resource is currently stored in the app sandbox. You can call this method if you need to clean up:

```objective-c
/**
 * clear cache
 */
- (void)clearPanelCache;
```

**Example**

Objc:

```objc
[[TuyaSmartPanelSDK sharedInstance] clearPanelCache];
```

Swift:

```swift
TuyaSmartPanelSDK.sharedInstance().clearPanelCache()
```