# Instabug Expo Test

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
