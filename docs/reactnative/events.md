# Events
Your app can subscribe to events from AppFriends using `AppFriends.event` apis. Objects that implement `AFEventSubscriber` protocol can subscribe to AppFriends events.

## Subscribe to AppFriends Events
To get notified by AppFriends about events, you can subscribe to the event postings by:
```javascript
import AppFriends from "react-native-appfriends-library";

const afEventEmitter = new NativeEventEmitter(AppFriends.event);

// Message Received
afEventEmitter.addListener(
    AppFriends.event.AFEvent_Message_Received,
    (message) => {
      // message that was received
    }
);

// Dialog Updated
afEventEmitter.addListener(
    AppFriends.event.AFEvent_Dialog_Updated,
    (dialog) => {
      // dialog was updated
    }
);

// Dialog Created
afEventEmitter.addListener(
    AppFriends.event.AFEvent_Dialog_Created,
    (dialog) => {
      // dialog was created
    }
);

// Some user left a dialog
afEventEmitter.addListener(
    AppFriends.event.AFEvent_Dialog_Left,
    (dialog) => {
      // dialog was created
    }
);

// Typing event
afEventEmitter.addListener(
    AppFriends.event.AFEvent_Typing_Status,
    (dialog) => {
      // typing event
    }
);

// Unread message count number changed
afEventEmitter.addListener(
    AppFriends.event.AFEvent_Unread_Count_Change,
    (number) => {
      // the new number
    }
);
```
