# User Create and Login
AppFriends users are mirrors of the users in your app. To create or login a user on AppFriends, you need to provide at least

1. an unique username
2. an unique user ID

### Example
#### Swift
<pre><code class="swift">
let userInfo = [HCSDKConstants.kUserID: "e575be0fef6c24041a1749da54ece501", HCSDKConstants.kUserName: "John Doe"]
HCSDKCore.sharedInstance.loginWithUserInfo(userInfo)
{ (response, error) in
  	if let err = error {
  			// handle login error
  	}
  	else {
			// login is successful here
  	}
}
</code></pre>
