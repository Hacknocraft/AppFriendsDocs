# Events
Your app can subscribe to events from AppFriends using `AFEvent` class and its API. Objects that implement `AFEventSubscriber` protocol can subscribe to AppFriends events.

## Subscribe to AppFriends Events
To get notified by AppFriends about events, you can subscribe to the event postings by:
```swift
// subscribe, we will only hold a weak reference to subscriber
AFEvent.subscribe(subscriber: self)

// unsubscribe
AFEvent.unsubscribe(subscriber: self)
```

## Process Event
To process posted events, please implement
```swift
func emitEvent(_ event: AFEvent) {
  if eventName == .eventTypingStatusUpdated {
    let typingStatus = event.data as? AFTypingStatus {
      // process typing event
    }
  } else if
    ...
}
```
Each `AFEvent` object contains an event name and a data object. The type of the data object depends on the type of event. For example, an `AFEventName.eventDialogUpdated` event will contain an `AFDialog`

## Event List
Event name                |    Data                     |     Description            
-------------             | -----------------           | ------------------------   
.eventDialogCreated       | `AFDialog` object           | dialog created, the newly created dialog will be the data                       
.eventDialogLeft          | `AFDialog` object           | the current user has left the dialog                         
.eventDialogUpdated       | `AFDialog` object           | dialog updated, the dialog that is updated will be the data                      
.eventTypingStatusUpdated | `AFTypingStatus` object     | typing status updated, the `AFTypingStatus` object will be the data                
.eventMessageReceived     | `AFMessage` object          | new message received, the new `AFMessage` object will be the data                        
.eventUserSelected        | `String` userID             | user selected by the user from within the AppFriends UI. You can use this event to open user profile in your app.                    
