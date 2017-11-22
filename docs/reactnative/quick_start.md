# Getting Started
This page will help you install and integrate AppFriends into your ReactNative app.

## Install via NPM
You can install the library using npm:
```
$ npm install react-native-app-friends-library --save
```

## iOS integration
For iOS, we need to install the AppFriends Native library as a dependency using `Cocoapod`. Please go to your iOS folder at `{your project folder}/ios`, and run:
```
$ pod init
```
Then inside the Podfile, add:
```
pod 'AppFriendsUI', :git => 'https://github.com/Hacknocraft/AppFriendsUI.git', :branch => ‘swift4_0’
pod 'AppFriendsCore', :git => 'https://github.com/Hacknocraft/AppFriendsCore.git', :branch => ‘swift4_0’
pod 'CoreStore', :git => 'https://github.com/JohnEstropia/CoreStore.git', :branch => 'prototype/Swift_4_0’
```
Then run `pod install`. This will create a workspace file `{yourproject}.xcworkspace`. Please use the workspace file to open your iOS project from now on.
The last step is linking the library:
```
`$ react-native link react-native-app-friends-library`
```

## Android Integration
For Android, the native AppFriends Core library is a required dependency.
Add the following to your application's `build.gradle` file:

```Groovy
repositories {
    maven { url 'https://raw.githubusercontent.com/Hacknocraft/AppFriendsAndroidCore/master/' }
}

dependencies {
   // AppFriends
   compile 'me.appfriends.sdk:ui:3.2.4'
}
```

Once Gradle successfully syncs the library, a final linking step is required:
```
`$ react-native link react-native-app-friends-library`
```

## Initialization
Before using AppFriends features, you need to initialize the SDK:
```javascript
import AppFriends from "react-native-appfriends-library";

// you can get your AppFriends key and secret from AppFriends Dashboard.
AppFriends.initialize('{your application key}', 'your Application secret');
```
