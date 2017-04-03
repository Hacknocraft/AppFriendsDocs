Session API can be access using `AFSession` class.
## Login
Before an user can start using AppFriends features, he must first login to AppFriends. In your app, you could login your user to AppFriends as soon as the user is logged into your app. If the user has not previously registered with AppFriends, the user will be created on AppFriends.
To login an user, we require

1. **an unique username**
2. **an unique user ID**, this should be the same user id that you use in your app to identify the user

```swift
AFSession.login(username: username, userID: userID, completion: { (token, error) in
  if let err = error {
    // login failed
  } else {
    // login is successful
  }
})
```

You can check if a user has logged in to AppFriends or not by using:
```swift
if AFSession.isLoggedIn() {
  // user has logged in to AppFriends
}
```

## Logout
When an user logs out from your app, you should also log him out from AppFriends, so that new users can login later. To logout an user:
```swift
AFSession.logout { (error) in
  if let err = error {
    // logout failed
  } else {
    // logout is successful
  }
}
```
