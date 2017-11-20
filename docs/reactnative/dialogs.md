# Chat Dialogs
Each conversation between users is a dialog.

## Private Dialogs
Private dialogs are dialogs only visible to the participates of the dialog. Users need to be joined to the dialog before chatting in it.

### Listing All Private Dialogs
AppFriends SDK remembers all the private dialogs and you can get the list of private dialogs by:
```javascript
import AppFriends from "react-native-appfriends-library";

AppFriends.dialog.getDialogs().then((fetchedDialogs) => {
  // fetch successful with an array of dialog objects
}, (error) => {
  // fetch failed
});
```

#### Get a Dialog Info
```javascript
/// - Parameters:
///   - dialogID: id of the dialog
AppFriends.dialog.getDialog(dialogID)
.then((dialog) => {
    // getting dialog info successful
}, (error) => {
    // failed
});
```

#### Typing
You can send typing event when a user is typing or stopped typing
```javascript
/// start typing
AppFriends.dialog.startTyping(dialogID);

/// end typing
AppFriends.dialog.endTyping(dialogID);
```

#### Unread Message Count
For each dialog, you can get the unread message count by accessing the dialog's `unreadMessageCount` property.
To get the total number of unread message count:
```javascript
import AppFriends from "react-native-appfriends-library";

AppFriends.dialog.totalUnreadMessageCount()
.then((number) => {
    // number is the total unread count
}, (error) => {
    // failed
});
```

### Group Dialog
A group dialog is a private dialog which is only visible to users in it. You can add more users or remove users from the dialog.
Please note that you can provide an id to this dialog. It is optional, and if you do not provide an id, AppFriends will assign an unique id to this dialog. This is a good way for you to bind the dialog with certain feature or part of your app. To start a group dialog, you need to first create a group dialog:

```javascript
import AppFriends from "react-native-appfriends-library";

/// - Parameters:
///   - id: Optional, but you can choose to provide an unique id to the dialog yourself. If this value is not provided, we will create an unique id for you. This is a good way for you to bind the dialog with certain feature or part of your app.
///   - members: an array of user IDs of the users who you want to include in the dialog.
///   - customData: the custom data string of the user. You can use this to attach additional information of the dialog.
///   - pushData: additional data you can include to the push notification generated inside this dialog.
///   - title: dialog title, if not provided, the default dialog title will be used.
AppFriends.dialog.createGroupDialog(dialogID, members, customData, pushData, title)
.then((dialogID) => {
    // dialog created
}, (error) => {
    // dialog create failed
});
```

#### Adding a Member to a Dialog
```javascript
/// - Parameters:
///   - userIDs: an array of userIDs
AppFriends.dialog.addMembers(userIDs, members)
.then(() => {
    // adding members successful
}, (error) => {
    // failed to add the members
});
```

#### Getting Members of a Dialog
```javascript
/// - Parameters:
///   - dialogID: id of the dialog
AppFriends.dialog.getMembers(dialogID)
.then((members) => {
    // getting members successful
}, (error) => {
    // failed to get the members
});
```

#### Update a Dialog name
```javascript
/// - Parameters:
///   - dialogID: id of the dialog
///   - dialogName: new name of the dialog
AppFriends.dialog.updateDialogName(dialogID, dialogName)
.then(() => {
    // getting members successful
}, (error) => {
    // failed to get the members
});
```

### Individual Dialog
An individual dialog is a private dialog between two users. You cannot add more users to this dialog. To start an individual dialog:

#### Create a One on One Dialog
```javascript
import AppFriends from "react-native-appfriends-library";

/// - Parameters:
///   - userID: id of the other user
AppFriends.dialog.createIndividualDialog(userID)
.then((dialogID) => {
    // dialog created
}, (error) => {
    // dialog create failed
});
```
