# AppFriends Android SDK

## Demo App
A simple demo app showing the integrated AppFriends SDK is available at: [Demo](https://github.com/AppFriendsMe/AndroidDemo).

## Integration

### Maven / jCenter / Bintray
To integrate AppFriends Android SDK to your Android Studio project, add the
following to your application's `build.gradle` file:

#### Project Level Gradle
```
allprojects {
    repositories {
        jcenter()
        maven { url 'https://jitpack.io' }
    }
}
```
#### App Level Gradle
```
repositories {
    maven {
        url 'https://dl.bintray.com/appfriends/maven/'
    }
}

dependencies {
    // AppFriends
    compile 'me.appfriends.sdk:ui:3.0.5'
}
```

If your application uses a version of the Android support libraries that results in conflicts, you can force Gradle to build with your version with:

```
compile ('com.android.support:support-v4:23.4.0'){
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

AppFriends SDK and the corresponding UI Kit must be initialized prior to usage. In your custom ``Application`` class, you have the option to customize the AppFriends SDK with ```AppFriendsConfiguration.Builder```. You must call ```AppFriendsUIKit.init(this, configuration);``` to properly initialize the SDK:
```
public class MyApplication extends Application {
    @Override
    public void onCreate() {
        super.onCreate();

        AppFriendsConfiguration configuration =
          new AppFriendsConfiguration.Builder()
                                     .gravity(Gravity.RIGHT) // Which way the widget should open from
                                     .build();

        AppFriendsUIKit.init(this, configuration);
    }
}

```
## User Authentication
Before your users can start enjoying AppFriends, they need to have an
AppFriends account. Login the user by invoking:
```
AppFriends.login(userID, username, avatarURL, userEmail);
```
where the parameters as as follows:

Parameter | Type | Description
--------- | ---- | -----------
userID    | String | the user's userID in your own app.
username  | String | the username
avatarURL | String | the full URL of the user's avatar
userEmail | String | user's email address

## Display Widget Bubble
To add the default widget icon to your ``Activity`` or ``Fragment``, add the
following to your ``layout xml``:
```
<me.appfriends.android.widget.AppFriendsWidget
    android:id="@+id/appfriends_icon"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    app:bragIcon="[Custom Brag Icon Drawable]"
    app:deeplink="[Deeplink]"/>
```
You may specify the "brag" icon (which allows users to share a screenshot) and the deeplink path of the current fragment/activity.

The AppFriends Android SDK should now be integrated and ready to go!

## Styling

AppFriends Android UI Kit will soon support customizing the UI matching your app's style, stay tuned for an update.

## Deeplinks
When a user shares screenshot from your app, a deeplink will be generated and shared with the screenshot. If the screenshot is taken from a place you have assign a path and parameters to, the information will also be included in the deeplink. When users clicks on the deeplink and install/open the app, we will trigger the callback with the path and parameters you provided.

To receive deeplink actions, you need to implement the `OnAppFriendsNotificationListener` interface register the listener with the UI Kit:
```
  AppFriendsUIKit.addOnAppFriendsNotificationListener(new OnAppFriendsNotificationListener() {
      @Override
      public boolean onDeeplinkClicked(String deeplink) {
          // Perform deeplink action
          return true; // If handled, return true
      }
  });
```

## Public Chat Channels
By default, we create a global public chat channel for all of your users to chat. You can create, edit and remove public chat channels. You can either do it from the AppFriends admin panel or via our [API](server/index.html).

## Other dependencies
```
https://github.com/splitwise/TokenAutoComplete
```
