# Errors & Exceptions
AppFriends errors are managed with `AppFriendsException` class and API, a detailed description of the error occurred will be provided along with a possible error code

Error Code                     | Description
-----------           |-------------
90000                  | An unknown error has occurred
90001                 | Invalid parameters supplied
90002           | SDK is not initialized properly
90003              | Need to login first
20005            | Dialog is not found
90007          | Trying to login while there's already an user logged in
90009        | Trying to logout while there isn't any user logged in
90500                  | Server error
30001              | User not found
91000         | Request is too frequent
