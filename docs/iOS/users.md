# Users
The users API interface is in data model class `AFUser`. In order to use AppFriends and for all the AppFriends UI components to work properly, your users will need to be mirrored on AppFriends' system. It means you need to make sure all of your users are copied onto AppFriends' system and updates to the user information, such as username change and so on, are also make available to AppFriends, so your user will get consistent result in your app. Batch users import can be done via [admin API](/api/adminapi.md), and AppFriends SDK also provides a lot of convenient interface for you to work with.

## User Update
When user information is updated on your app, you need to update the same user on AppFriends, so the data is consistent. For example, if an user changed his profile on your app, and he/she chose a new username, or a different avatar picture, you will need to update the same user on AppFriends.

Update Username:
```swift
let username = "a new username"
AFUser.updateUserName(username: username, completion: { (error) in
  if error != nil {
    //update failed
  } else {
    //update successful
  }
})
```
Update User Avatar:
```swift
let avatarURL = "https://someavatar.jpg"
AFUser.updateUserAvatar(avatar: avatarURL, completion: { (error) in
  if error != nil {
    //update failed
  } else {
    //update successful
  }
})
```

## Fetch Information of an User
You can fetch the information of an user.
```swift
AFUser.getUser(userID: userID, completion: { (user, error) in
               if error != nil {
                   // get user failed
               } else {
                   // fetch successful, you can now use the returned user object
               }
           })
```

## Block/Unblock
An user can block other users. If user A blocks user B, B will no longer be able to send any private message to A.
You can block a user by:
```swift
AFUser.blockUser(userID: userID, completion: { (error) in
                        if let err = error {
                            // block user failed
                        }
                        else {
                            // block user successful
                        }
                    })
```
Unblock a user:
```swift
AFUser.unblockUser(userID: userID, completion: { (error) in
                        if let err = error {
                            // unblock user failed
                        }
                        else {
                            // unblock user successful
                        }
                    })
```
