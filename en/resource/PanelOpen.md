## Open Panel

### 关于面板跳转

The panel jumps based on navigator push by default. When called, sdk will select the vc on the top of the current app to jump.
**Note:** React-Native rendering of the panel VC will hide the NavigationBar. Please call self.navigationController.navigationBarHidden = NO when you return to your VC.

### Goto device panel

**Parameter Description**

| Parameter       | Description                                                     |
| ---------- | -------------------------------------------------------- |
| device     | TuyaSmartDeviceModel               |
| completion | Failed to open panel error callback. (NSError *error：Specific reference error code) |

**Sample Code** 

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

### Goto group panel

**Parameter Description**

| Parameter       | Description                                                     |
| ---------- | -------------------------------------------------------- |
| group      | TuyaSmartGroupModel                                    |
| completion | Failed to open panel error callback. (NSError *error：Specific reference error code) |

**Sample Code** 

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