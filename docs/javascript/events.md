# Events
Your app can subscribe to events from AppFriends SDK. The events/callback we will provide are:

Event name            |    Data                                |     Description            
-------------         | -----------------                      | ------------------------   
onMessageReceived     | `Dialog` object and `Message` object   | a new message is received
onDialogCreated       | `Dialog` object                        | a new dialog is created      
onDialogChanged       | `Dialog` object                        | a dialog has been changed                     
onBadgeUpdated        | n/a                                    | unread message count changed    
onUserJoined          | `Dialog` object and 'User' object      | new user joined a dialog                      
onUserLeft            | `Dialog` object and 'User' object      | a user left a dialog  

## Subscribe to the new event
Here's a sample code to create a event handler. You can register multiple event handlers, and the SDK will callback each one of them.
```javascript

// You can create a function like this which takes other functions as parameters
// Then assign the functions to the handler object and register it with AppFriends SDK
createHandlerGlobal(...args) {

    // message received handle
    let messageReceivedFunc = args[0];

    // dialog created handle
    let dialogCreatedFunc = args[1];

    // dialog updated handle
    let dialogChangedFunc = args[2];

    // unread message count change handle
    let badgeChangedFunc = args[3];

    // user joined a dialog
    let userJoinFunc = args[4];

    // user left a dialog
    let userLeftFunc = args[5];

    let DialogHandler = {
      onMessageReceived: (dialog, message) => {
        messageReceivedFunc(dialog, message);
      },
      onDialogCreated: (dialog) => {
        dialogCreatedFunc(dialog);
      },
      onDialogChanged: (dialog) => {
        dialogChangedFunc(dialog);
      },
      onBadgeUpdated: () => {
        badgeChangedFunc();
      },
      onUserJoined: (dialog, user) => {
        userJoinFunc(dialog, user);
      },
      onUserLeft: (dialog, user) =>
      {
        userLeftFunc(dialog, user);
      }
    };

    // adding a handler and provide a name to the handler
    af.addDialogHandler("GLOBAL_HANDLER", DialogHandler);
}
```
