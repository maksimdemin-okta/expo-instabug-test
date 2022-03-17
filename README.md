# Instabug Expo Test

## IOS

Steps to reproduce issue

Create bare workflow with Expo

```
expo init instabug-test
```

Follow directions from here https://dashboard.instabug.com/applications/atmosphere/beta/settings/sdk-integrations

```
yarn add instabug-reactnative
sudo gem install xcodeproj
yarn react-native add-instabug
cd ios && pod install && cd..
```

Try to generate a build

```
expo run:ios
```

Get error

```
› Compiling instabug-reactnative Pods/RNInstabug » RCTConvert+InstabugEnums.m

❌  (node_modules/react-native/React/Base/RCTConvert.h:27:1)

  25 |  * custom RCTViewManager setter methods.
  26 |  */
> 27 | @interface RCTConvert : NSObject
     | ^ duplicate interface definition for class 'RCTConvert'
  28 |
  29 | + (id)id:(id)json;
  30 |


❌  (node_modules/react-native/React/Base/RCTConvert.h:137:12)

  135 | @end
  136 |
> 137 | @interface RCTConvert (Deprecated)
      |            ^ definition of 'RCTConvert' must be imported from module 'React.RCTConvert' before it is required
  138 |
  139 | /**
  140 |  * Use lightweight generics syntax instead, e.g. NSArray<NSString *>
```

## Android

add a local.properties to the android folder with the following info

```
sdk.dir = /Users/YOUR_NAME/Library/Android/sdk
```

Follow directions here: https://dashboard.instabug.com/applications/atmosphere/beta/settings/sdk-integrations

1. Navigate to android/app/src/main/java/[...]/MainApplication.java

2. Import the Instabug package:

```
import com.instabug.reactlibrary.RNInstabugReactnativePackage;
```

3. Add the integration code to the onCreate() method like the below snippet.

```java
@Override
public void onCreate() {
super.onCreate();
new RNInstabugReactnativePackage
.Builder("YOUR_APP_TOKEN", MainApplication.this)
.setInvocationEvent("none")
.build();
}
```

enable replies

```javascript
useEffect(() => {
  Replies.setEnabled(true);
}, []);
```

show instabug button

```javascript
<Button
  title="Open Instabug"
  onPress={() => {
    Instabug.show();
  }}
></Button>
```
