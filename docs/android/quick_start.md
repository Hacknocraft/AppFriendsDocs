# AppFriends Android SDK

## 1. Create an AppFriends Application
Before start using AppFriends, you need to create an application on the [dashboard](http://appfriends.hacknocraft.com/landing/index) Users in the same application can talk to each other and you only need one application for all the platforms you want to support.
To see an sample app of how to use AppFriendsUI, please checkout our repo:

<a href="https://github.com/hacknocraft/AppfriendsAndroidSample">
<button class="btn btn-info">Android Sample App</button>  
</a>

## 2. Integrate AppFriends SDK

### Gradle Integration
AppFriends Android SDK is available as a Gradle dependency, add the following to your application's `build.gradle` file:

```Groovy
repositories {
   maven {
       maven { url 'https://raw.githubusercontent.com/Hacknocraft/AppFriendsAndroidCore/master/' }
   }
}

dependencies {
   // AppFriends
   compile 'me.appfriends.sdk:ui:3.2.2'
}
```

### Other Dependencies
AppFriends Android SDK leverages several commonly used 3rd party libraries to provide easy to use programming interface as well as a powerful set of UI components. Below is a list of important ones you should be aware of:

- RxJava 1.x (2.x support is coming soon!) to perform many of the asynchronous operations in order to be compatible with application architectures utilizing MVP or MVVM.

- Android Support library version 25.1.0

- OKHttp version 3.6.0

It is recommended that you use the same or more recent versions of these libraries in order to maintain compatibility.

However, if your application uses a version of of the libraries that result in conflicts and you would like to maintain your version:

```Groovy
compile ('com.android.support:support-v4:23.4.0') {
 force = true;
}
```

## 3. AppFriends SDK Initialization
After logging into your admin panel on [AppFriends.me](http://appfriends.me/) and creating an application, you can find your ``App ID`` and ``App Secret``. Add them to your ```AndroidManifest.xml``` file under ```<application>```.
```XML
<meta-data
   android:name="me.appfriends.AppID"
   android:value="[APPFRIENDS_ID]" />

<meta-data
   android:name="me.appfriends.AppSecret"
   android:value="[APPFRIENDS_SECRET]" />
```

AppFriends SDK must be initialized in your custom ``Application`` class:
```Java
public class MyApplication extends Application {
   @Override
   public void onCreate() {
       super.onCreate();

       AppFriends instance = AppFriends.getInstance();
       instance.init(getApplicationContext());
   }
}
```
## 4. Login / Sign Up
AppFriends' user system augments your existing user system through unique user ids. Please see [sessions](sessions.md) for detail

## 5. UI
There are a lot of ready to use UI components in the AppFriendsUI SDK. They can save you hundreds of hours of development. To learn the UI components and how to use them, please see [ui components section](ui.md)

## 6. Full JavaDoc SDK Documentation
- [Javadoc](https://hacknocraft.github.io/AppFriendsAndroidCore/)

## Push Notifications
Please see [Push Notifications Guide](push.md)