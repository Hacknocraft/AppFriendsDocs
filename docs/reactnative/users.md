# Users
The users API interface is accessible via `AppFriends.user`. In order to use AppFriends and for all the AppFriends UI components to work properly, your users will need to be mirrored on AppFriends' system. It means you need to make sure all of your users are copied onto AppFriends' system and updates to the user information, such as username change and so on, are also make available to AppFriends, so your user will get consistent result in your app. Batch users import can be done via [admin API](/api/adminapi.md), and AppFriends SDK also provides a lot of convenient interface for you to work with.

## User Update
When user information is updated on your app, you need to update the same user on AppFriends, so the data is consistent. For example, if an user changed his profile on your app, and he/she chose a new username, or a different avatar picture, you will need to update the same user on AppFriends.

### Update Username:
```javascript
import AppFriends from "react-native-appfriends-library";

AppFriends.user.updateUserName(username).then(() => {
    // success
}, (error) => {
    // failed
});
```

### Update User Avatar:
```javascript
import AppFriends from "react-native-appfriends-library";

AppFriends.user.updateUserAvatar(username).then(() => {
    // success
}, (error) => {
    // failed
});
```

Update username and avatar at the same time:
```javascript
import AppFriends from "react-native-appfriends-library";

AppFriends.user.updateUser(username, avatar).then(() => {
    // success
}, (error) => {
    // failed
});
```

## Fetch Information of an User
You can fetch the information of an user.
```javascript
import AppFriends from "react-native-appfriends-library";

AppFriends.user.getUser(userid).then((user) => {
    // success
}, (error) => {
    // failed
});
```

## Search users
After you imported all of your users into AppFriends platform, you can perform search on usernames and get back a list of users.
```javascript
import AppFriends from "react-native-appfriends-library";

AppFriends.user.searchUser(query).then((users) => {
    // success
}, (error) => {
    // failed
});
```
