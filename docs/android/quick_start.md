# AppFriends Android SDK

## Demo App
A simple demo app showing the integrated AppFriends SDK is available at: [Demo](https://github.com/hacknocraft/AppfriendsAndroidSample).

## SDK Documentation
- [Javadoc](https://hacknocraft.github.io/AppFriendsAndroidCore/)

## Integration

### General Information
AppFriends Android SDK utilizes RxJava 1.x (2.x support is coming soon!) to perform many of the asynchronous operations in order to be compatible with application architectures utilizing MVP or MVVM.

### Gradle Integration
To integrate AppFriends Android SDK to your Android Studio project, add the
following to your application's `build.gradle` file:

#### App Level Gradle
```
repositories {
   maven {
       maven { url 'https://raw.githubusercontent.com/Hacknocraft/AppFriendsAndroidCore/master/' }
   }
}

dependencies {
   // AppFriends
   compile 'me.appfriends.sdk:ui:3.2.0'
}
```

#### Dependencies
AppFriends UI SDK uses Android Support library version 25.1.0

AppFriends Core SDK uses OKHttp version 3.6.0

It is recommended that you use the same or more recent versions to maintain compatibility.

However, if your application uses a version of of the libraries that result in conflicts and you would like to maintain your version:

```
compile ('com.android.support:support-v4:23.4.0') {
 force = true;
}
```

## Initialization
After logging into your admin panel, and created your application, you can find your ``App ID`` and ``App Secret``. Add them to your ```AndroidManifest.xml``` file under ```<application>```.
```
<meta-data
   android:name="me.appfriends.AppID"
   android:value="[APPFRIENDS_ID]" />

<meta-data
   android:name="me.appfriends.AppSecret"
   android:value="[APPFRIENDS_SECRET]" />
```

AppFriends SDK must be initialized in your custom ``Application`` class:
```
public class MyApplication extends Application {
   @Override
   public void onCreate() {
       super.onCreate();

       AppFriends instance = AppFriends.getInstance();
       instance.init(getApplicationContext());
   }
}

```
## User Authentication
Before your users can start enjoying AppFriends, they need to have an
AppFriends account. Create or login the user by invoking:
```
AppFriends.getInstance().login(userID, username);
         .observeOn(AndroidSchedulers.mainThread())
         .subscribe(new Subscriber<Boolean>() {
             @Override
             public void onCompleted() {
             }

             @Override
             public void onError(Throwable e) {
                 // Handle any errors
             }

             @Override
             public void onNext(Boolean loggedIn) {
                 // Handle login status
             }
         });
```

## Push Notification
You can register the device with AppFriends and receive push notification by:
```
AppFriends.getInstance().pushService().updatePushToken(userId,
        FirebaseInstanceId.getInstance().getToken())
        .subscribe(new Subscriber<Boolean>() {
            @Override
            public void onCompleted() {

            }

            @Override
            public void onError(Throwable e) {
                Log.d(TAG, e.getMessage());
            }

            @Override
            public void onNext(Boolean registered) {
                Log.d(TAG, "push token registered: " + registered);
            }
        });
```


## UI Integration
AppFriends Android SDK provides a full suite of ready-to-use UI components for simplified UI integrations.

There are 3 UI integration modes, in order to decreasing difficulty but increased customization:
### 1. Simple / Standalone Mode (Recommended)
Launching standalone AppFriends UI after a user has logged in, this will launch the full AppFriends UI with channel, group and private conversation views in separate activities (fullscreen or partial slide out).
```
Intent intent = new Intent(getContext(), ConversationsActivity.class);
startActivity(intent);
```         

The views can be configured and customized to match your app's style guide. Please see the customization guide for full list of values you can override as well as the sample app for a customization example.

```
<style name="AppFriends.DialogList">
   <item name="dialogTitleTextColor">@android:color/holo_red_light</item>
   <item name="dialogUnreadTitleTextColor">@android:color/holo_red_light</item>
   <item name="dialogUnreadTitleTextStyle">italic</item>
</style>

<style name="AppFriends.Toolbar">
   <item name="android:textColorPrimary">@android:color/holo_red_dark</item>
   <item name="android:textColorSecondary">@android:color/background_dark</item>
   <item name="android:background">@color/orange</item>
   <item name="colorControlNormal">#FF0000</item>
</style>

<style name="AppFriends.Popup">
   <item name="android:layout_marginStart">32dp</item>
   <item name="android:layout_marginEnd">32dp</item>
   <item name="android:layout_marginTop">32dp</item>
   <item name="android:layout_marginBottom">32dp</item>
   <item name="entranceOrigin">bottom</item>
</style>
```     

### 2. Embedded Mode
It is also possible to embed AppFriends UI components into your existing application UI flow such as fragments. The AppFriends views all have integrated SDK linking thus reducing the need for you to connect with the core network and caching SDK.

The following views can be directly embedded into your XML layouts:
- `me.appfriends.ui.dialoglist.DialogListRecyclerView`
- `me.appfriends.ui.channellist.ChannelListRecyclerView`

The chat window is a separate activity that you can either launch or extend called `DialogActivity`.

Our sample app also provides extensive details on how to embedded these UI components.

### 3. Custom Mode
If components supplied by the AppFriends UI SDK does not meet your needs, you may elect not to use the UI library and directly interact with the core library. To do so, replace `compile 'me.appfriends.sdk:ui:3.2.0'` with `compile 'me.appfriends.sdk:core:3.2.0'` in your `build.gradle` configuration file. The core SDK provides no UI elements but contains full asynchronous network, caching and persistence functionalities.


## Additional API / Functionalities
Should you decide to forego using AppFriends UI components or integrate additional functionalities such as dialog creation, member management, user operations, and etc. Please check out the full [Javadoc](https://hacknocraft.github.io/AppFriendsAndroidCore/) API documentation and the sample app for their usages. Please don't hesitate to contact us should you have additional questions / requests.