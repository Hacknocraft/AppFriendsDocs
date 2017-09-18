# Social API
AppFriends offers social features to help you build applications to connect users and store their social relationship.

## Follow/Unfollow and Friends
User can follow/unfollow one another.
To follow a user:
```javascript
// userID is target user id
af.User.followUser(userID, (response, error) => {
  // callback function
});
```

To unfollow a user
```javascript
// userID is target user id
af.User.unfollowUser(userID, (response, error) => {
  // callback function
});
```

To get a list of the followers of the current user
```javascript
af.User.getFollowers(userID, function (users, error) {
  // callback function
  if (error) {
    // handle
  } else {
    // you get a array of user objects
  }
});
```

To get a list of users that the current user is following
```javascript
af.User.getFollowings(userID, function (users, error) {
  // callback function
  if (error) {
    // handle
  } else {
    // you get a array of user objects
  }
});
```

In AppFriends, when two users follow one another, they become friends. To get a list of friends of the current user, you can use:
```javascript
af.User.getFriends(userID, function (users, error) {
  // callback function
  if (error) {
    // handle
  } else {
    // you get a array of user objects
  }
});
```

## Block/Unblock
An user can block other users. If user A blocks user B, B will no longer be able to send any private message to A.
You can block a user by:
```javascript
af.User.blockUser(userID, function (response, error) {
  // callback function
});
```

Unblock a user:
```javascript
af.User.unBlockUser(userID, function (response, error) {
  // callback function
});
```
