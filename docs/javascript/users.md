# Users
The users API interface is in data model class `User`. In order to use AppFriends and for all the AppFriends UI components to work properly, your users will need to be mirrored on AppFriends' system. It means you need to make sure all of your users are copied onto AppFriends' system and updates to the user information, such as username change and so on, are also make available to AppFriends, so your user will get consistent result in your app. Batch users import can be done via [admin API](/api/adminapi.md), and AppFriends SDK also provides a lot of convenient interface for you to work with.

## User Update
When user information is updated on your app, you need to update the same user on AppFriends, so the data is consistent. For example, if an user changed his profile on your app, and he/she chose a new username, or a different avatar picture, you will need to update the same user on AppFriends.

Update Username:
```javascript
const username = "a new username"
af.User.updateCurrentUserName(username, (response, error) => {
  if (error) {
    // handle error
  } else {
    // success
  }
});
```

Update User Avatar:
```javascript
let avatarURL = "https://someavatar.jpg"
af.User.updateCurrentUserAvatar(avatarURL, (response, error) => {
  if (error) {
    // handle error
  } else {
    // success
  }
});
```

## Fetch Information of an User
You can fetch the information of an user. You need to pass a userID. It will return a user object.
```javascript
af.User.fetchUserInfo(userID, (user, error) => {
  if (error) {
    // handle error
  } else {
    // success, it returns a User object
  }
});
```

## Search users
After you imported all of your users into AppFriends platform, you can perform search on usernames and get back a list of users.
```javascript
af.User.searchUsersWithPager(
  searchKey,  // text to be searched
  page,       // page number
  perPage,    // number of results per page
  (pager, users, err) => {
    // callback, returns a pager object and an array of users
    // the pager object contains the page information
})
```
