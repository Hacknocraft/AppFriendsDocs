# Integrating AppFriends UI into your application
AppFriends Android SDK provides a full suite of ready-to-use UI components for simplified UI integrations.

There are 3 UI integration modes, in order to decreasing difficulty but increased customization:
### 1. Simple / Standalone Mode (Recommended)
Launching standalone AppFriends UI after a user has logged in, this will launch the full AppFriends UI with channel, group and private conversation views in separate activities (fullscreen or partial slide out).
```
Intent intent = new Intent(getContext(), ConversationsActivity.class);
startActivity(intent);
```         

The views can be configured and customized to match your app's style guide through style configurations as well as overriding XML attribute. Please see the [UI Customization Guide](customization.md) for full list of values you can override as well as the sample app for a customization example.

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