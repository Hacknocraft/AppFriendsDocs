# Social API
AppFriends offers social features to help you build applications to connect users and store their social relationship.

## Follow/Unfollow and Friends
User can follow/unfollow one another.
To follow a user:
```Java
String userId = "another user's id";
AppFriends.getInstance().userService().followUser(userId)
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

To unfollow a user
```Java
String userId = "another user's id";
AppFriends.getInstance().userService().followUser(userId)
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

To get a list of the followers of the current user
```Java
AppFriends.getInstance().userService().getFollowers()
        .subscribe(new Subscriber<List<String>>() {
            @Override
            public void onCompleted() {
                
            }

            @Override
            public void onError(Throwable e) {

            }

            @Override
            public void onNext(List<String> strings) {

            }
        });
```

To get a list of users that the current user is following
```java
AppFriends.getInstance().userService().getFollowing()
        .subscribe(new Subscriber<List<String>>() {
            @Override
            public void onCompleted() {
                
            }

            @Override
            public void onError(Throwable e) {

            }

            @Override
            public void onNext(List<String> strings) {

            }
        });
```

In AppFriends, when two users follow one another, they become friends. To get a list of friends of the current user, you can use:
```Java
AppFriends.getInstance().userService().getFriends()
        .subscribe(new Subscriber<List<String>>() {
            @Override
            public void onCompleted() {
                
            }

            @Override
            public void onError(Throwable e) {

            }

            @Override
            public void onNext(List<String> strings) {

            }
        });
```

## Block/Unblock
An user can block other users. If user A blocks user B, B will no longer be able to send any private message to A.
You can block a user by:
```Java
String userId = "another user's id";
AppFriends.getInstance().userService().blockUser(userId)
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
Unblock a user:
```Java
String userId = "another user's id";
AppFriends.getInstance().userService().unblockUser(userId)
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
