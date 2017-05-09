# AppFriends Android SDK

## Demo App
A simple demo app showing the integrated AppFriends SDK is available at: [Demo](https://github.com/hacknocraft/AppfriendsAndroidSample).

## SDK documentation
- [Javadoc](https://hacknocraft.github.io/AppFriendsAndroidCore/)

## Integration

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
    compile 'me.appfriends.sdk:ui:3.1.1'
}
```

#### Dependencies
AppFriends UI SDK uses Android Support library version 25.2.0 and Play Services version 10.2.0

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

## Additional APIs
- [Javadoc](https://hacknocraft.github.io/AppFriendsAndroidCore/)


