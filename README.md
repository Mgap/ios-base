# iOS Base Template
**iOS base** is a boilerplate project created by Rootstrap for new projects using Swift 3.2. The main objective is helping any new projects jump start into feature development by providing a handful of functionalities.

## Features
This template comes with:
#### Main
- Complete **API client** class to easily communicate with **REST services**.
- Examples for **account creation** and **Facebook integration**.
- Useful classes to **manage User and Session data**.
- **Secure** way to store keys of your **third party integrations**.
- Handy **helpers** and **extensions** to make your coding experience faster and easier.


#### Extensions
 This App Template also contains other branches with specific features that may be of use to you:

- [**feature/observe_root_vc**](https://github.com/rootstrap/ios-base/tree/feature/observe_root_vc): Detecting when **rootViewController** gets loaded.
- [**feature/util_gradients**](https://github.com/rootstrap/ios-base/tree/feature/util_gradients): Helper methods to easily add **color gradients**.
- [**feature/paginated_collections**](https://github.com/rootstrap/ios-base/tree/feature/paginated_collections): Adds **paginated** subclasses of **UITableView** and **UICollectionView**.
- [**feature/RX_Swift**](https://github.com/rootstrap/ios-base/tree/feature/RX_Swift) in case you want to work with **RxSwift** or **MVVM**.

To use them simply download the branch and locally rebase against master/develop from your initial **iOS base** clone.

## How to use
1. Clone repo.
2. Change the name of the project on the left sidebar in Xcode.
3. Go to Manage Schemes and change the name to the new one.
4. Search for the name `ios_base` in the entire project and replace all occurrences for the new name(If your project name contains a dash then use an underscore instead).
5. Close Xcode.
6. Rename the main and the source folder.
7. Right click the project bundle `.xcodeproj` file and select “Show Package Contents” from the context menu.
8. Open the `.pbxproj` file with any text editor.
9. Search and replace any occurrence of `ios-base` and `ios_base` and replace it with the new folder name. If the new folder name contains any dashes please use underscore instead when replacing `ios_base`.
10. Save the file.
11. Open the scripts folder, open the `acceptance-tests.sh` file with any text editor.
12. Search and replace any occurrence of the original folder name with the new folder name.
13. Save the file.
14. Open `Podfile` and change the target name with the new name of your project.
15. Delete the `*.workspace` file.
16. Run `pod install`.
17. Done :)

To manage user and session persistence after the original sign in/up we store that information in the native UserDefaults. The parameters that we save are due to the usage of [Devise Token Auth](https://github.com/lynndylanhurley/devise_token_auth) for authentication on the server side. Suffice to say that this can be modified to be on par with the server authentication of your choice.

## Pods
#### Main
 - [Alamofire](https://github.com/Alamofire/Alamofire) for easy and elegant connection with an API.
 - [SwiftyJSON](https://github.com/SwiftyJSON/SwiftyJSON) for easy JSON parsing.
 - [IQKeyboardManagerSwift](https://github.com/hackiftekhar/IQKeyboardManager) for auto-scrolling to current input in long views.
    Note: this pod is not fully working on iOS 11. [Here](https://github.com/hackiftekhar/IQKeyboardManager/issues/972) is the issue we encountered and the meantime solution.


#### Testing
 - [KIF](https://github.com/kif-framework/KIF) for UI testing.
 - [KIF/IdentifierTests](https://github.com/kif-framework/KIF) to have access to accesibility identifiers.
 - [OHHTTPStubs/Swift](https://github.com/AliSoftware/OHHTTPStubs) for network testing.

#### Optional
 - [FBSDKCoreKit](https://github.com/facebook/facebook-ios-sdk) facebook pods dependency.
 - [FBSDKLoginKit](https://github.com/facebook/facebook-ios-sdk) for facebook login.

## Optional configuration
#### facebook
1. In `info.plist` on the URL types array, find `fbXXXXXXXXXXX` and replace it for the string "fb" + the ID of your app. i.e: `fb435272928934`.
2. Change the `FacebookAppID` value for the same AppID that you replace above.
3. Change the `FacebookDisplayName` value for the name of the app on Facebook.
4. Done :)

## Security recommendations
#### Third Party Keys

We strongly recommend that all private keys be added to a `.plist` file that will remain localy and not be commited to your project repo. An example file is already provided, this are the final steps to setting it up:

1. Rename the `ThirdPartyKeys.example.plist` file on your project so that it is called `ThirdPartyKeys.plist`.
  To add a set of keys simply add a dictionary with the name you want the key to have and add the corresponding **Debug**, **Staging** and **Release** keys as items.
2. Remove the reference of `ThirdPartyKeys.plist` from XCode but do not delete the file. This way, you will keep the file locally(it is already in the .gitignore list) in the project directory.
  **Note: Do NOT move the file from the current location, the script uses the $(PROJECT_DIR) directory.**
3. Go to **Product** -> **Scheme** -> **Edit scheme**. Then select **Pre-actions** for the Build stage and make sure that the `Provided build setting` is set to your current target.
**Repeat this step for the Post-actions script.**
4. Done :)

## License

iOS-Base is available under the MIT license. See the LICENSE file for more info.

## Credits

**iOS Base** is maintained by [Rootstrap](http://www.rootstrap.com) with the help of our [contributors](https://github.com/rootstrap/ios-base/contributors).

[<img src="https://s3-us-west-1.amazonaws.com/rootstrap.com/img/rs.png" width="100"/>](http://www.rootstrap.com)
