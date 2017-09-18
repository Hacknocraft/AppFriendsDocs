# Quick Start
Before start using AppFriends, you need to create an application on the [dashboard](http://appfriends.hacknocraft.com/landing/index) Users in the same application can talk to each other and you only need one application for all the platforms you want to support.
To see an sample app of how to use AppFriendsJS, please checkout our repo:

<a href="https://github.com/Hacknocraft/AppFriendsWebUI">
<button class="btn btn-info">Github Web Widget Sample App</button>  
</a>

## Integration
Please download `AppFriends.min.js` from [Github](https://github.com/Hacknocraft/AppFriendsJavascript.git). Then include the script on your website by:
```html
<script src="AppFriends.min.js"></script>
```

## Login
A user must be authenticated/logged in first before any interaction with AppFriends can begin. Please provide a userID and username when you login a user. If the user id isn't found on AppFriends, we will create a user and assign username to this user. If user id is found, we will login the user and return a token.

Login a user:
```javascript
const af = windoww.af;
// to login you need to provide a user id and a username
af.login(userId, nickname, (token, error) => {
  if (error) {
    // handle error
  }
});
```
