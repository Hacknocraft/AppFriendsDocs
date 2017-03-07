# Errors
AppFriends errors are managed with `AFError` class and API.

Error Code |    Type                  | Description
-----------| -------------            |-------------
90000      | .unknownError            | An unknown error has occurred
90001      | .invalidParams           | Invalid parameters supplied
90002      | .sdkNotInitialized       | SDK is not initialized properly
90003      | .userNotLoggedIn         | Need to login first
20005      | .dialogNotFound          | Dialog is not found
90007      | .userAlreadyLoggedIn     | Trying to login while there's already an user logged in
90009      | .logoutWhenNotLoggedIn   | Trying to logout while there isn't any user logged in
90500      | .serverError             | Server error
30001      | .userNotFound            | User not found
91000      | .requestIsTooFrequent    | Request is too frequent
