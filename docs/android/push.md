# Receiving Message Push Notification
Once configuration for server side push notification is done on the AppFriends dashboard, you can easily register the app/client side push token with AppFriends and receive push notification:
```
AppFriends.getInstance().pushService().updatePushToken(userId,
        FirebaseInstanceId.getInstance().getToken())
        .subscribe(new Subscriber<Boolean>() {
            @Override
            public void onCompleted() {

            }

            @Override
            public void onError(Throwable e) {
                Log.d(TAG, e.getMessage());
            }

            @Override
            public void onNext(Boolean registered) {
                Log.d(TAG, "push token registered: " + registered);
            }
        });
```