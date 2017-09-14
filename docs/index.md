# Welcome to AppFriends

The AppFriends plugin integrates public chat channels, private messaging, and social graphs into any app to increase user interaction and engagement. AppFriends supports multiple platforms.

AppFriends supports a number of features:
<ul>
<li>open channel, group and one on one chats</li>
<li>social features such as following and making friends</li>
<li>privacy features such as blocking/reporting an user</li>
<li>dialog conversation settings such as muting, changing dialog name</li>
<li>typing indicator</li>
<li>dialog media album</li>
<li>message receipts</li>
<li>video and image messages</li>
<li>...</li>
</ul>

If you are interested in our product or have ideas on how we can improve it, please send emails to [support@hacknocraft.com](SUPPORT@HACKNOCRAFT.COM); we would love to hear from you.

## Chat and Dialogs
AppFriends offers three types of chat:

There are three types of dialogs. Depending on your use case, please choose the appropriate type to use:

1. *Private one on one dialog*. This is a conversation between two users. You can't add more users to private one on one dialog. This type of dialog is only visible to the two users in it.
2. *Private group dialog*. This is a conversation between multiple users. You can add up to a few hundred users to a private group chat. This type of dialog is only visible to users in the group.
3. *Open channel dialog*. This is an open conversation. It is visible to everyone. You can add up to a few thousand users to an open channel. Each user can only be in one channel at a time.

Feature Type              |    Open Channels    |     Private Group Chat     |     One on One Private Chat
-------------             | -----------------   | ------------------------   | -----------------------------
Typing Indicator          | ✘                   | ✔                          | ✔
Message Delivery Receipts | ✘                   | ✔                          | ✔
Message Read Receipts     | ✘                   | ✔                          | ✔
Video and Image           | ✔                   | ✔                          | ✔
Create in app             | ✘                   | ✔                          | ✔
Create in control panel   | ✔                   | ✘                          | ✘
Mute                      | ✔                   | ✔                          | ✔
Blocks user               | ✔                   | ✔                          | ✔
Push notifications        | ✔                   | ✔                          | ✔
Members limit             | 5000                | 100                        | 2

## Social
AppFriends offers social features to help you build applications to connect users and store their social relationship. A user can *follow* another user, and if that user follows back, they become *friends*. You can query a list of the user's followers or the users being followed the user.

## Mobile
AppFriends has native and javascript SDKs and that make integration for iOS, Android and web much easier.

### iOS
The iOS SDK can be integrated into existing Xcode iOS projects. There are two SDK frameworks for you to use. If you don't want to use our provided UI, you can integrate the [AppFriendsCore](https://github.com/laeroah/AppFriendsCoreFramework) framework, which has no UI components but helps you communicate with the AppFriends platform. There is also the [AppFriendsUI](https://github.com/laeroah/AppFriendsUI) framework, which contains a lot of convenient UI components for you to quickly implement chat in your app. For details, please read the [iOS SDK guide](ios/quick_start.md).

### Android
The Android SDK can be integrated into existing Android projects. For details,
please read [Android SDK guide](android/quick_start.md). A sample android application can be found [here](https://github.com/hacknocraft/AppfriendsAndroidSample).

## Server API
AppFriends has comprehensive REST APIs for you to use. There are two types of APIs: [Application API](api/applicationapi.md) and [Admin API](api/adminapi.md).

## Admin Portal
You can control the widget by logging into the [admin portal](https://appfriends.hacknocraft.com/) with your AppFriends account.
