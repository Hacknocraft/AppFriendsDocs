# Social API
AppFriends offers social features to help you build applications to connect users and store their social relationship.

## Follow/Unfollow and Friends
User can follow/unfollow one another.
To follow a user:
```swift
// userID is target user id
AFUser.followUser(userID: userID, completion: { (error) in
                if error != nil {
                  // handle error
                } else {
                  // success
                }
            })
```

To unfollow a user
```swift
// userID is target user id
AFUser.unfollowUser(userID: userID, completion: { (error) in
                if error != nil {
                  // handle error
                } else {
                  // success
                }
            })
```

To get a list of the followers of the current user
```swift
AFUser.getFollowers { (users, error) in
            if error == nil, let userIDs = users {
              // success, you get a list of user ids of the followers
            } else {
              // failed
            }
        }
```

To get a list of users that the current user is following
```swift
AFUser.getFollowing { (users, error) in
            if error == nil, let userIDs = users {
              // success, you get a list of user ids of the followers
            } else {
              // failed
            }
        }
```

In AppFriends, when two users follow one another, they become friends. To get a list of friends of the current user, you can use:
```swift
AFUser.getFriends { (users, error) in
            if error == nil, let userIDs = users {
              // success, you get a list of user ids of the followers
            } else {
              // failed
            }
        }
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
