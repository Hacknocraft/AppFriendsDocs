## Sending Messages
Sending a message to dialog requires a dialog object. You can get dialog object by fetching all dialogs or creating one. For details on dialogs, please see [Dialogs](dialogs.md).

### Sending text:
```javascript
af.Dialog.sendTextMessage(
      dialog,          // dialog object
      text,            // text to be sent
      customData,      // optional, custom data, you can send a string with your message
      requireReceipt,  // if the message require receipt, default is false
      mentionUsers,    // optional, an array of user ids of users who you want to mention in the message
      sendPush,        // optional, if a message should trigger a push notification. Default is is true
      (message) => {
          // this is a callback, after the message is sent.
      }
);
```

### Sending an image:
```javascript
af.Dialog.sendTextMessage(
      dialog,          // dialog object
      imageURL,        // full image url
      thumbnailURL,    // thumbnail image url
      customData,      // optional, custom data, you can send a string with your message
      requireReceipt,  // if the message require receipt, default is false
      mentionUsers,    // optional, an array of user ids of users who you want to mention in the message
      sendPush,        // optional, if a message should trigger a push notification. Default is is true
      (message) => {
          // this is a callback, after the message is sent.
      }
);
```

### Sending a video:
```javascript
af.Dialog.sendTextMessage(
      dialog,          // dialog object
      videoStreamURL,  // video stream url
      thumbnailURL,    // thumbnail image url
      customData,      // optional, custom data, you can send a string with your message
      requireReceipt,  // if the message require receipt, default is false
      mentionUsers,    // optional, an array of user ids of users who you want to mention in the message
      sendPush,        // optional, if a message should trigger a push notification. Default is is true
      (message) => {
          // this is a callback, after the message is sent.
      }
);
```

### Sending a gif
```javascript
af.Dialog.sendTextMessage(
      dialog,          // dialog object
      gifURL,          // gif url
      customData,      // optional, custom data, you can send a string with your message
      requireReceipt,  // if the message require receipt, default is false
      mentionUsers,    // optional, an array of user ids of users who you want to mention in the message
      sendPush,        // optional, if a message should trigger a push notification. Default is is true
      (message) => {
          // this is a callback, after the message is sent.
      }
);
```

## Mentioning Users
You can mention other users by referencing their IDs in the message you compose.
```swift
af.Dialog.sendTextMessage(
      dialog,          // dialog object
      gifURL,          // gif url
      customData,      // optional, custom data, you can send a string with your message
      requireReceipt,  // if the message require receipt, default is false
      mentionUsers,    // optional, an array of user ids of users who you want to mention in the message
      sendPush,        // optional, if a message should trigger a push notification. Default is is true
      (message) => {
          // this is a callback, after the message is sent.
      }
);
```
