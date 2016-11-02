# Users
In order to use AppFriends and for all the AppFriends UI components to work properly, your users will need to be mirrored on AppFriends' system. It means you need to make sure all of your users are copied onto AppFriends' system and updates to the user information, such as username change and so on, are also make available to AppFriends, so your user will get consistent result in your app. AppFriends SDK provides a lot of convenient interface for you to work with.

## Account Create and Login
AppFriends users are mirror images of the users in your app. To create or login a user on AppFriends, you need to provide at least

1. an unique username
2. an unique user ID

To learn how to import all of your existing users onto AppFriends system all together, please refer to the API document.

### Example
#### Swift
```
let userInfo = [HCSDKConstants.kUserID: "e575be0fef6c24041a1749da54ece501", HCSDKConstants.kUserName: "John Doe"]
HCSDKCore.sharedInstance.loginWithUserInfo(userInfo)
{ (response, error) in
  	if let err = error {
  			// handle login error
  	}
  	else {
			// login is successful here
  	}
}
```

## User Update
When user information is updated on your app, you need to update the same user on AppFriends, so the data is consistent. For example, if an user changed his profile on your app, and he/she chose a new username, or a different avatar picture, you will need to update the same user on AppFriends.

### Example
#### Swift
```
AppFriendsUserManager.sharedInstance.updateUserInfo(currentUserID,
  userInfo: [HCSDKConstants.kUserAvatar: avatar, HCSDKConstants.kUserName: username],
  completion: { (response, error) in

      // handle error or success here
  })
```

## Social
`AppFriends` provides service to help your app to create a social graph in your app. Using social features, your users can follow one another and become friends in your app.

### Follow/Unfollow
Social graph is made by users following each other. If two users follow each other, they become `friends` in AppFriends.
You can follow a user by:
```
AppFriendsUserManager.sharedInstance.followUser(userID, completion: { (response, error) in
      // handle error or success here
})
```
Unfollow a user:
```
AppFriendsUserManager.sharedInstance.unfollowUser(userID, completion: { (response, error) in
      // handle error or success here
})
```

### Blocking/Unblocking
An user can block other users. If user A blocks user B, B will no longer be able to send any private message to A.
You can block a user by:
```
AppFriendsUserManager.sharedInstance.blockUser(userID, completion: { (response, error) in
      // handle error or success here
})
```
Unblock a user:
```
AppFriendsUserManager.sharedInstance.unblockUser(userID, completion: { (response, error) in
      // handle error or success here
})
```

## Constants

Parameter | Type | Description
--------- | ---- | -----------
HCSDKConstants.kUserID        | String | the user's userID of this user in the host app.
HCSDKConstants.kUserAvatar    | String | the avatar url of this user in the host app.
HCSDKConstants.kUserName      | String | the username
