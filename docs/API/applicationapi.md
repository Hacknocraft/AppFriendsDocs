# Application API
AppFriends API can be used to authenticate user, send messages, search for user, update user information, create social relationship and etc. Application API's can only be accessed via the SDK, using the application secret.

## REST APIs
Please see our application REST APIs [here](https://documenter.getpostman.com/view/154000/appfriends-application-api/2MrYL7).

### Error Codes
Error Code     |    Description
-----------    |    -------------
9000           | operation not allowed
10000          | parameter required
10001          | need to login
10002          | missing app ID
10003          | invalid app ID
10004          | no permission
10005          | admin user not found
10007  			   | no Authorization header found
10008          | invalid Authorization header found
10009          | invalid request path or method
10010 			   | invalid params
10011 			   | admin server api secret required
30007 			   | exceed max import users per request
