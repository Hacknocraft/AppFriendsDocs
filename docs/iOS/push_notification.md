AppFriends can send push notification to the device when there's a new message for a user or if the user is mentioned in a channel chat. Push notification API is accessible via `AFPushNotification` class. Please make sure the user has already logged in before registering for push. Unregistering must also happen before the user logout.

## Register for Push
To enable push notification, you need to first register the push token with AppFriends:
```swift
AFPushNotification.registerDeviceForPushNotification(pushToken: pushToken, completion: { (error) in
})
```
## Unregister for Push
To unregister push notification:
```swift
AFPushNotification.unregisterDeviceForPushNotification(pushToken: pushToken, completion: { (error) in
})
```
## Process Push
After you received remote push notification, please pass it to the SDK for better user experience. Especially if you are entering the app using the push notification sent by AppFriends. We will only look at push notification coming from AppFriends.
```swift
// true if AppFriends SDK used the push notification
let pushHandled = AFPushNotification.processPushNotification(notificationUserInfo: userInfo)
```
