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