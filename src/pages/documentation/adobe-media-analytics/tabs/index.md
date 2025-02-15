<Variant platform="android" task="add" repeat="5"/>

1. Add the Media extension and its dependencies to your project using the app's Gradle file.

```java
implementation 'com.adobe.marketing.mobile:sdk-core:1.+'
implementation 'com.adobe.marketing.mobile:analytics:1.+'
implementation 'com.adobe.marketing.mobile:media:2.+'
```

You can also manually include the libraries. Get `.aar` libraries from [Github](https://github.com/Adobe-Marketing-Cloud/acp-sdks/tree/master/android).

2. Import the Media extension in your application's main activity.

```java
import com.adobe.marketing.mobile.*;
```

<Variant platform="ios" task="add" repeat="8"/>

1. To add the Media library and its dependencies to your project, add the following pods to your `Podfile`:

```pod
pod 'ACPCore', '~> 2.0'
pod 'ACPAnalytics', '~> 2.0'
pod 'ACPMedia', '~> 2.0'
```

You can also manually include the libraries. Get `.a` libraries from [Github](https://github.com/Adobe-Marketing-Cloud/acp-sdks/tree/master/iOS).

2. In Xcode project, import Media extension:

**Swift**

```swift
import ACPMedia
```

**Objective-C**

```objectivec
#import "ACPMedia.h"
```

<Variant platform="react-native" task="add" repeat="11"/>

#### JavaScript

1. Install Media.

```bash
   npm install @adobe/react-native-acpmedia
```

1.1 Link

* **React Native 0.60+**

[CLI autolink feature](https://github.com/react-native-community/cli/blob/master/docs/autolinking.md) links the module while building the app.

* **React Native &lt;= 0.59**

```bash
   react-native link @adobe/react-native-acpmedia
```

_Note_ For `iOS` using `cocoapods`, run:

```bash
   cd ios/ && pod install
```

1. Import the extension.

```jsx
import {ACPMedia} from '@adobe/react-native-acpmedia';
```

2. Get the extension version.

```jsx
ACPMedia.extensionVersion().then(version => console.log("AdobeExperienceSDK: ACPMedia version: " + version));
```

<Variant platform="android" task="register" repeat="3"/>

#### Java

To register media with Mobile Core, call the `setApplication()` method in `onCreate()` and call set up methods, as shown in this sample:

```java
import com.adobe.marketing.mobile.*;

public class MobileApp extends Application {

  @Override
  public void onCreate() {
      super.onCreate();
      MobileCore.setApplication(this);

      try {
          Media.registerExtension();
          Analytics.registerExtension();
          Identity.registerExtension();
          MobileCore.start(new AdobeCallback () {
              @Override
              public void call(Object o) {
                  MobileCore.configureWithAppID("your-launch-app-id");
              }
          });
      } catch (InvalidInitException e) {

      }
  }
}
```

<Variant platform="ios" task="register" repeat="6"/>

#### Swift

In your app's `_:didFinishLaunchingWithOptions` function, register the Audience Manager extension with the Mobile Core:

```swift
import ACPCore
import ACPAnalytics
import ACPIdentity
import ACPMedia

func application(_ application: UIApplication,
                 didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
    ACPCore.setLogLevel(.debug)
    ACPCore.configure(withAppId: "your-launch-app-id")

    ACPAnalytics.registerExtension()
    ACPIdentity.registerExtension()
    ACPMedia.registerExtension()

    ACPCore.start {

    }

    return true;
}
```

#### Objective-C

In your app's `application:didFinishLaunchingWithOptions`, register Media with Mobile Core:

```objectivec
#import "ACPCore.h"
#import "ACPAnalytics.h"
#import "ACPIdentity.h"
#import "ACPMedia.h"

- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    [ACPCore setLogLevel:ACPMobileLogLevelDebug];
    [ACPCore configureWithAppId:@"your-launch-app-id"];

    [ACPAnalytics registerExtension];
    [ACPIdentity registerExtension];
    [ACPMedia registerExtension];

    [ACPCore start:^{

    }];

    return YES;
  }
```

<Variant platform="react-native" task="register" repeat="2"/>

#### JavaScript

When using React Native, registering Media with Mobile Core should be done in native code which is shown under the Android and iOS tabs.
