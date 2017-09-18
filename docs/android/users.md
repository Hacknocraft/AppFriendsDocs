# Users
The users API interface is provided by `UserService`. In order to use AppFriends and for all the AppFriends UI components to work properly, your users will need to be mirrored on AppFriends' system. It means you need to make sure all of your users are copied onto AppFriends' system and updates to the user information, such as username change and so on, are also make available to AppFriends, so your user will get consistent result in your app. Batch users import can be done via [admin API](/api/adminapi.md), and AppFriends SDK also provides a lot of convenient interface for you to work with.

## User Update
When user information is updated on your app, you need to update the same user on AppFriends, so the data is consistent. For example, if an user changed his profile on your app, and he/she chose a new username, or a different avatar picture, you will need to update the same user on AppFriends.

Update Username:
```Java
String username = "a new username"

AppFriends.getInstance().userService().updateUserName(username)
                .subscribe(new CompletableSubscriber() {
                    @Override
                    public void onCompleted() {
                        
                    }

                    @Override
                    public void onError(Throwable e) {
                        // Error
                    }

                    @Override
                    public void onSubscribe(Subscription d) {
                        // Success
                    }
                });
```

Update User Avatar:
```Java
String avatarURL = "https://someavatar.jpg"

AppFriends.getInstance().userService().updateUserAvatar(avatarURL)
                .subscribe(new CompletableSubscriber() {
                    @Override
                    public void onCompleted() {
                        
                    }

                    @Override
                    public void onError(Throwable e) {
                        // Error
                    }

                    @Override
                    public void onSubscribe(Subscription d) {
                        // Success
                    }
                });
```

## Fetch Information of an User
You can fetch the information of an user.
```Java

AppFriends.getInstance().userService().getUser("some_user_id")
                .subscribe(new Subscriber<User>() {
                    @Override
                    public void onCompleted() {
                        
                    }

                    @Override
                    public void onError(Throwable e) {
                        // Error
                    }

                    @Override
                    public void onNext(User user) {
                        // Success
                    }
                });
```
