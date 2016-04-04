# AppFriends Android SDK

## Integration

### Maven / jCenter / Bintray
To integerate AppFriends Android SDK to your Android Studio project, add the
following to your application's `build.gradle` file:

```
repositories {
    maven {
        url 'https://dl.bintray.com/mikedw/maven/'
    }
}
```
and add the appfriends SDK as part of your app's dependencies:
```
dependencies {
    compile 'me.appfriends.android:appfriends:1.4.+'
}
```

## Initialization and customization
After logging into your admin panel, and created your application, you can find your ``App ID`` and ``App Secret``. Add them to your ```AndroidManifest.xml``` file under ```<application>```.
```
   <meta-data
        android:name="me.appfriends.AppID"
        android:value="[APPFRIENDS_ID]" />

    <meta-data
        android:name="me.appfriends.AppSecret"
        android:value="[APPFRIENDS_SECRET]" />
```

In your ``Application`` class, you have the option to customize the AppFriends SDK with ```AppFriendsConfiguration.Builder```. You must call ```AppFriendsUIKit.init(this, configuration);``` to properly initialize the SDK:
```
public class MyApplication extends Application {
    @Override
    public void onCreate() {
        super.onCreate();

        AppFriendsConfiguration configuration = new AppFriendsConfiguration.Builder()
                .appName("Name of app") // Name of your app that shows up on the privacy agreement screen
                .appIcon(R.drawabl.app_icon) // Icon resource of your app that shows up on the privacy agreement screen
                .debugMode(true)
                .gravity(Gravity.RIGHT) // Which way the widget should open from
                .build();

        AppFriendsUIKit.init(this, configuration);
    }
}

```

### Add floating widget icon to layout
To add the default widget icon to your ``Activity`` or ``Fragment``, add the
following to your ``layout xml``:
```
<me.appfriends.android.widget.AppFriendsWidget
    android:id="@+id/appfriends_icon"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    app:bragIcon="[BRAG ICON DRAWABLE]"
    app:deeplink="[DEEPLINK]"/>
```
You may specify the "brag" icon (which allows users to share a screenshot) and the deeplink path of the current fragment/activity.

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

The AppFriends Android SDK should now be integrated and ready to go!
