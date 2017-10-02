## Open Channels
Open channel is a public chat, where all of your users can participate. It can handle thousands of users in one channel. ex) Twitch-style public chat.
You can create open channel from your AppFriends web control panel. After a channel is created, all of your users can see all the channels with `GET /channels` API. A user can only be inside one channel at a time.

List all channels:
```Java
AppFriends.getInstance().channelService().getChannels()
        .subscribe(new Subscriber<List<Channel>>() {
            @Override
            public void onCompleted() {

            }

            @Override
            public void onError(Throwable e) {

            }

            @Override
            public void onNext(List<Channel> channels) {

            }
        });
```

The easiest way to use open channel is by using `ChannelActivity` from your current activity.
```Java
startActivity(ChannelActivity.actionView(this, channel.id));
```

## Private Dialogs

### Listing All Private Dialogs
AppFriends SDK remembers all the private dialogs and you can get the list of private dialogs by:
```Java
AppFriends.getInstance().dialogService().getDialogs()
        .subscribe(new Subscriber<List<Dialog>>() {
            @Override
            public void onCompleted() {

            }

            @Override
            public void onError(Throwable e) {

            }

            @Override
            public void onNext(List<Dialog> dialogs) {

            }
        });
```
### Group Dialog
A group dialog is a private dialog which is only visible to users in it. You can add more users or remove users from the dialog. To start a group dialog, you need to first create a group dialog:
```Java
List<String> dialogMemberIds = new ArrayList<>();
dialogMemberIds.add("user id of user you would like to invite");

AppFriends.getInstance().dialogService().createDialog("dialog title", dialogMemberIds)
        .subscribe(new Subscriber<Dialog>() {
            @Override
            public void onCompleted() {

            }

            @Override
            public void onError(Throwable e) {

            }

            @Override
            public void onNext(Dialog dialog) {

            }
        });
})
```

### Individual Dialog
An individual dialog is a private dialog between two users. If you create a group dialog with only 1 user id as member id, then it defaults to an individual dialog.

## Mute/Unmute
You can mute/unmute a dialog by:
```Java
AppFriends.getInstance().dialogService().muteDialog("dialog id", true) // or false
        .subscribe(new CompletableSubscriber() {
            @Override
            public void onCompleted() {

            }

            @Override
            public void onError(Throwable e) {

            }

            @Override
            public void onSubscribe(Subscription d) {

            }
        });
```

## Sending Messages
Sending text:
```Java
String dialogId = "some dialog id";
Dialog.DialogType type = Dialog.DialogType.INDIVIDUAL; // or Dialog.DialogType.GROUP
String message = "message body";

AppFriends.getInstance().chatService.sendTextMessage(dialogId, type, message)
        .subscribe(new CompletableSubscriber() {
            @Override
            public void onCompleted() {
                // Success
            }

            @Override
            public void onError(Throwable e) {
                // Error
            }

            @Override
            public void onSubscribe(Subscription d) {

            }
        });
```

Sending an image:
```Java
String dialogId = "some dialog id";
Dialog.DialogType type = Dialog.DialogType.INDIVIDUAL; // or Dialog.DialogType.GROUP
String imageUrl = "URL of image";
String thumbUrl = "URL of thumbnail";

AppFriends.getInstance().chatService.sendImageMessage(dialogId, type, imageUrl, thumbUrl)
        .subscribe(new CompletableSubscriber() {
            @Override
            public void onCompleted() {
                // Success
            }

            @Override
            public void onError(Throwable e) {
                // Error
            }

            @Override
            public void onSubscribe(Subscription d) {

            }
        });
```

Sending a video:
```Java
// dialog is an AFDialog instance
String dialogId = "some dialog id";
Dialog.DialogType type = Dialog.DialogType.INDIVIDUAL; // or Dialog.DialogType.GROUP
String videoMediaUrl = "URL of video";
String thumbUrl = "URL of thumbnail";

AppFriends.getInstance().chatService.sendVideoMessage(dialogId, type, videoMediaUrl, thumbUrl)
        .subscribe(new CompletableSubscriber() {
            @Override
            public void onCompleted() {
                // Success
            }

            @Override
            public void onError(Throwable e) {
                // Error
            }

            @Override
            public void onSubscribe(Subscription d) {

            }
        });
```

Sending a gif
```Java
String dialogId = "some dialog id";
Dialog.DialogType type = Dialog.DialogType.INDIVIDUAL; // or Dialog.DialogType.GROUP
String gifImageUrl = "URL of gif image";
String thumbUrl = "URL of thumbnail";

AppFriends.getInstance().chatService.sendImageMessage(dialogId, type, gifImageUrl, thumbUrl)
        .subscribe(new CompletableSubscriber() {
            @Override
            public void onCompleted() {
                // Success
            }

            @Override
            public void onError(Throwable e) {
                // Error
            }

            @Override
            public void onSubscribe(Subscription d) {

            }
        });
```

## Message Receipts
You can check the receipts of a message by using:
```Java
AppFriends.getInstance().chatService().getReadReceipts(messageTempID)
        .subscribe(new Subscriber<List<String>>() {
            @Override
            public void onCompleted() {

            }

            @Override
            public void onError(Throwable e) {

            }

            @Override
            public void onNext(List<String> receivedUserIds) {

            }
        });
```
Sending Receipts:
If you use the chat view provided in AppFriendsUI SDK, you do not need to manually send the receipts. The UI SDK automatically handles it. If you wish to send receipts yourself, it can be done via `ChatService`:
```Java
// message is of Message type
AppFriends.getInstance().chatService().readMessage(message);
```
