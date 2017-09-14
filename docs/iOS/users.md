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

Update username and avatar at the same time:
```swift
let username = "a new username"
let avatarURL = "https://someavatar.jpg"
AFUser.updateUser(username: username, avatar: avatarURL, completion: { (error) in
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

## Search users
After you imported all of your users into AppFriends platform, you can perform search on usernames and get back a list of users.
```swift
AFUser.search(query: text, completion: { (users, error) in
                if error != nil {
                  // search failed, please handle error here
                } else if let friends = users {
                  // you get back an array of user ids
                }
                self.tableView.reloadData()
            })
```

## Get online user count
Our SDK can report how many users are online to your application. Your application can implement `HCSDKCoreOnlineUserObserver` and then register to receive the update by `HCSDKCore.sharedInstance.subscribeToOnlineUsers(self)`
```swift
// MARK: HCSDKCoreOnlineUserObserver
public func onlineUserCountChanged(count: NSInteger) {
  self.collectionView?.reloadData()
}
```
