# Session
This page helps you with user register, login and logout. The user session API can be accessed from `AppFriends.session`.

## Login and Register
Before an user can start using AppFriends features, he must first login to AppFriends. In your app, you could login your user to AppFriends as soon as the user is logged into your app. If the user has not previously registered with AppFriends, the user will be created on AppFriends.
To login an user, we require

1. **an username**, this value is also a nickname/display name of the user. It can contain space, and doesn't have to be unique.
2. **an unique user ID**, this should be the same user id that you use in your app to identify the user

```javascript
import AppFriends from "react-native-appfriends-library";

// You need to provide a userid and username to login the user
AppFriends.session.login(userid, username).then(() => {
    // login success
}, (error) => {
    // login failed
});
```

## Logout
When an user logs out from your app, you should also log him out from AppFriends, so that new users can login later. To logout an user:
```javascript
import AppFriends from "react-native-appfriends-library";

AppFriends.session.logout().then(() => {
  // logout success;
}, (error) => {
  // logout failed
});
```
