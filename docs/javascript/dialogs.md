## Open Channels

### Getting a list of open channels
```javascript
af.PublicChannel.fetchChannels((channelList, error) => {
  if (error) {
    // handle error
  } else {
    // success, you get a list of channel dialogs objects
  }
});
```

## Private Dialogs

### Getting a list of dialogs that you are in
```javascript
af.Dialog.fetchAllDialogs((dialogList, error) => {
  if (error) {
    // handle error
  } else {
    // success, you get a list of private dialogs objects
  }
});
```
### Get information of one dialog
```javascript
af.Dialog.getDialogInfo(dialogID, function(dialog, error) {
  if (error) {
    // handle error
  } else {
    // success, you get a list of private dialogs objects
  }
});
```

### Manage dialog members
To see the current users in a dialog, use `memberIDs` property of a dialog object.
```javascript
const memberIDs = dialog.memberIDs;
```

Invite someone to a group dialog
```javascript
af.Dialog.inviteWithMemberIds(dialogID, userIds, (response, error) => {
  if (error) {
    // handle error
  } else {
    // success, you get a list of private dialogs objects
  }
});
```

Leave a group dialog
```javascript
af.Dialog.leaveDialog(channel.id, (channel, error) => {
  if (error) {
    // handle error
  } else {
    // success, you get a list of private dialogs objects
  }
});
```

## Unread Message Count
To get unread message count of each dialog, use `unreadMessageCount` property of the a dialog object.
```javascript
const unreadMessageCount = dialog.unreadMessageCount
```

### Get total unread message count of all dialogs
```javascript
af.getTotalUnreadMessageCount((unreadCount) => {
  // returns the number of unread messages
});
```

### Clear dialog unread count
After you enter a dialog, you can clear the unread count by:
```javascript
dialog.markAsRead();
```
