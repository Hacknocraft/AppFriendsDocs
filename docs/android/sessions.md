## Login
Before an user can start using AppFriends features, he must first login to AppFriends. In your app, you could login your user to AppFriends as soon as the user is logged into your app. If the user has not previously registered with AppFriends, the user will be created on AppFriends.
To login an user, we require

1. **an username**, this value is also a nickname/display name of the user. It can contain space, and doesn't have to be unique.
2. **an unique user ID**, this should be the same user id that you use in your app to identify the user

```Java
AppFriends.getInstance().login(userID, username);
         .observeOn(AndroidSchedulers.mainThread())
         .subscribe(new Subscriber<Boolean>() {
             @Override
             public void onCompleted() {
             }

             @Override
             public void onError(Throwable e) {
                 // Handle any errors
             }

             @Override
             public void onNext(Boolean loggedIn) {
                 // Handle login status
             }
         });
```

You can check if a user has logged in to AppFriends or not by using:
```Java
if (AppFriends.getInstance().logOut()) {}
  // user has logged in to AppFriends
}
```

## Logout
When an user logs out from your app, you should also log him out from AppFriends, so that new users can login later. To logout an user:
```Java
AppFriends.getInstance().logOut();
```
