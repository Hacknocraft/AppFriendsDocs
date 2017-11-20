# Messaging
Sending message to a dialog requires the id of the dialog you are sending the message to and the content of the message. AppFriends supports sending text, image, video gif and location out of box, and you can expand to implement more message types.

## Sending Text
```javascript
import AppFriends from "react-native-appfriends-library";

/// Sending text in the dialog
///
/// - Parameters:
///   - text: the text to be sent
///   - dialogID: id of the dialog
///   - requireReceipt: require receipts for this messaeg. default is false
///   - mentionedUsers: the ids of the users mentioned in the message
///   - customData: custom data you want to attach to the message
///   - sendPush: whether or not send push notification for this message
AppFriends.dialog.sendText(text, dialogID, requireReceipt, sendPush, mentionedUsers, customData)
.then(() => {
  // success
}, (error) => {
  // failed
});
```

## Sending gif
```javascript
import AppFriends from "react-native-appfriends-library";

/// - Parameters:
///   - url: the url of the gif
///   - dialogID: id of the dialog
///   - customData: custom data you want to attach to the message
///   - requireReceipt: require receipts for this message. default is false
///   - sendPush: whether or not send push notification for this message
///   - completion: completion block which contains the error if the sending failed
AppFriends.dialog.sendText(url, dialogID, requireReceipt, sendPush, mentionedUsers, customData)
.then(() => {
  // success
}, (error) => {
  // failed
});
```

## Sending image
```javascript
import AppFriends from "react-native-appfriends-library";

/// - Parameters:
///   - base64DataString: base64 encoded image data
///   - dialogID: id of the dialog
///   - customData: custom data you want to attach to the message
///   - requireReceipt: require receipts for this message. default is false
///   - sendPush: whether or not send push notification for this message
///   - completion: completion block which contains the error if the sending failed
AppFriends.dialog.sendImageFromBase64(base64DataString, dialogID, requireReceipt, sendPush, mentionedUsers, customData)
.then(() => {
  // success
}, (error) => {
  // failed
});
```

## Sending Video
```javascript
import AppFriends from "react-native-appfriends-library";

/// - Parameters:
///   - base64DataString: base64 encoded video data
///   - dialogID: id of the dialog
///   - customData: custom data you want to attach to the message
///   - requireReceipt: require receipts for this message. default is false
///   - sendPush: whether or not send push notification for this message
///   - completion: completion block which contains the error if the sending failed
AppFriends.dialog.sendVideo(base64DataString, dialogID, requireReceipt, sendPush, mentionedUsers, customData)
.then(() => {
  // success
}, (error) => {
  // failed
});
```
