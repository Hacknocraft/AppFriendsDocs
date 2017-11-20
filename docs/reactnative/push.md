AppFriends can send push notification to the device when there's a new message for a user or if the user is mentioned in a channel chat. Push notification API is accessible via `AppFriends.event`. Please make sure the user has already logged in before registering for push. Unregistering must also happen before the user logout.

## Register for Push
Registering for push notification
```javascript
import AppFriends from "react-native-appfriends-library";

AppFriends.push.registerDeviceForPushNotification(deviceToken)
.then(() => {
  // success
}, (error) => {
  // failed
});
```
## Unregister for Push
To unregister push notification:
```javascript
import AppFriends from "react-native-appfriends-library";

AppFriends.push.unregisterDeviceForPushNotification()
.then(() => {
  // success
}, (error) => {
  // failed
});
```
