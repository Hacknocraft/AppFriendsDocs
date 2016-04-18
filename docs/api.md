# AppFriends API Documentation
AppFriends API can be used to authenticate user, open the widget to a certain view, control the data and interact with all the features of AppFriends. For example, some common tasks that developers can do includes:

- Open AppFriends widget to certain view. See [Navigation](#navigation).
- Search for users. See [Users](#Users).
- Post an activity for a user. See [Activities](activities).
- Create chat channels. See [Chat Channels](#chat-channels).
- Create chat groups. See [Chat Groups](#chat-groups).
- Send a notification to users. See [Notifications](#notifications).

Most of the AppFriends APIs are accessed by using URL's, and all the URL's follow the standard REST API URL pattern, which is `[key]/[value]`. For example, the URL to access a user will be marked as `user/[:id]`, where `user` is the **key** and `[:id]` is the **value**. 

## Navigation
You can use URL path to navigate inside AppFriends, very similar to how you navigate in a browser. This is a practice we want to encourage your app to adapt as well. It makes routing very easy and works well with deeplinks. If you use AppFriends' sharing and deeplink features, same routing scheme will be used to navigate inside your app.

For example, if you want to open a user's profile in AppFriends widget, you can use this URL: `/user/[:id]/profile` 

###Code Examples
You can use the following code to open a specific view of AppFriends widget. There are options to either open a single view or the entire widget. The difference is that if you open the entire widget, the user can navigate from the view opened to other AppFriends features. If you open a single view, the user will be limited to that one feature.

####Objective-C
```objc
// open entire widget and go to user's profile
[HCWidget openView:@"/users/haowang/profile"]; 

// open user's profile alone
[HCWidget openSingleView:@"/users/haowang/profile"]; 
```
	
####Swift
```swift 
// open entire widget and go to user's profile
HCWidget.openView:("/users/haowang/profile")
	
// open user's profile alone
HCWidget.openSingleView:("/users/haowang/profile")
```
	
####Android
```java
HCWidget.openSingleView:("/users/haowang/profile")
```

### AppFriends Widget Views and Their URLs

Destination            | URL           | Description
---------------------- | ------------- | -------------
User profile page | /users/[:id]/profile | open the user's profile page. The id provided here is the user's id in your app.
Activities page | /activities | open the activities page
Activities page | /activities/trending | open the trending activities page.
User search view | /users/search | open the search user view
User followers list view | /users/[:id]/followers | open the user's followers list view. The id provided here is the user's id in your app.
User followings list view | /users/[:id]/followings | open the view that lists the users which this user is following. The id provided here is the user's id in your app.
User friends view | /users/[:id]/friends | open the user's friends list view. The id provided here is the user's id in your app. 
Private chat page | /users/[:id]/chat | open the private chat with the user. The id provided here is the user's id in your app.
Group chat page | /chat_groups/[:groupid] | open the group chat. The id provided is the group id.
Chat Channel | /chat_channels/[:channelid] | open the channel. The id provided is the channel id.
Message thread view | /chat_channels/[:channelid]/messages/[:messageid] | open the message threading view which contains the message. Provide both channel id and message id.
Notification view | /notifications | open the notifications view
Screen sharing view | /screen_share | open the screenshot sharing window

## REST API's
If you use our out of box UI, all functionalities are enabled and ready to use by default, but if you want to make a customized UI, we certainly facilitate that as well. To access and modify data on AppFriends, you can ultilize our REST interface. There are two types of REST API's:
>1. Application API
>2. Admin API

Have fun! and remember to tell us what you made, and how we can improve our product to better support you.

### Application API
Application API's can only be accessed via the SDK, using the application secret. 

### Admin API
The admin api's can be accessed via any http client, using the admin secret. 

### Response
All responses from the REST API will be in `JSON` format. When a request is successful, the REST api will respond with requested data. When request is failed, an error with appropriate error code and some description of the error will be returned.

#### Sample error response:
```javascript
{
    "error": {
        "code": 100,
        "reason": "invalid parameters"
        "detail": "user id cannot be empty"
        "more_info": "https://appfriends.me/documentation"
    }
}
```

## User

!!! note "**/me**, a shortcut for current user"
    */me*, is a shortcut for */user/[:current_user_id]*. For example, */me/profile* is equivalent to */user/[:current_user_id]/profile*. 
    
### 1. Use information
------

Endpoint      | Method        | API Type      | Description
------------- | ------------- | ------------- | -------------
`/users/[:id]`   | GET           | Application   | get the user's information
	
#### Response
```javascript
{
    "id": string, 							// user id provided by hosting app when sign up the user. Always use this id.
    "email": string,						// user's email if provided
    "user_name": string,					// username
    "avatar": string,						// user's avatar if provided
}
```
------
Endpoint      | Method        | API Type      | Description
------------- | ------------- | ------------- | -------------
`/users/[:id]`   | PUT           | Application   | update the user's information

#### Request Parameters
```javascript
{
	"id": string, 			// required, the name of the chat group
	"email": string, 		// optional, email of the user
	"user_name": string, 	// optional, username,
	"real_name": string, 	// optional, the real name of the user
	"avatar": string, 		// optional, the avatar of the user
}
```

#### Response
```javascript
{
    "id": string, 				// user id provided by hosting app 
    "email": string,			// user's email if provided
    "user_name": string,		// username
    "real_name": string,		// user's real name if provided
    "avatar": string,			// user's avatar if provided
}
```

## Followers and Friends

!!! note "who are my friends?"
    Friends are users who follow each other.
    
Endpoint      | Method        | API Type      | Description      
------------- | ------------- | ------------- | -------------
`/users/[:id]/followers`   | GET | Application | Get all the followers of the user.

#### Response
```javascript
// array of followers
[
	{
	    "id": string, 				// user id provided by hosting app 
	    "user_name": string,		// username
	    "avatar": string,			// user's avatar if provided
	}, 
	{
	    "id": string, 				
	    "user_name": string,		
	    "avatar": string,			
	}
	...
]
```
------

Endpoint      | Method        | API Type      | Description      
------------- | ------------- | ------------- | -------------
`/me/followings`  | GET | Application | Get all the users that the current user is following.

#### Response
```javascript
// array of users that the current user is following
[
	{
	    "id": string, 				// user id provided by hosting app 
	    "user_name": string,		// username
	    "avatar": string,			// user's avatar if provided
	}, 
	{
	    "id": string, 				
	    "user_name": string,		
	    "avatar": string,			
	}
	...
]
```
------
Endpoint      | Method        | API Type      | Description      
------------- | ------------- | ------------- | -------------
`/me/followings`  | POST | Application | Make the current user follow a user

#### Request Parameters
```javascript
{
	"id": string, 			// required, the id of the user to be followed
}
```
------
Endpoint      | Method        | API Type      | Description      
------------- | ------------- | ------------- | -------------
`/me/followings`  | DELETE | Application | Make the current user unfollow a user

#### Request Parameters
```javascript
{
	"id": string, 			// required, the id of the user to be unfollowed
}
```
------

Endpoint      | Method        | API Type      | Description     
------------- | ------------- | ------------- | ------------- 
`/users/[:id]/Friends`   | GET   | Application | Get the users friends

#### Response
```javascript
// array of users
[
	{
	    "id": string, 				// user id provided by hosting app 
	    "user_name": string,		// username
	    "avatar": string,			// user's avatar if provided
	}, 
	{
	    "id": string, 				
	    "user_name": string,		
	    "avatar": string,			
	}
	...
]
```
------

### 7. Blocks/unblocks
Endpoint      | Method        | API Type      | Description     
------------- | ------------- | ------------- | ------------- 
`/users/[:id]/block`   | POST   | Application | Block this user
`/users/[:id]/unblock` | POST   | Application | unblock this user

### 8. Reporting a user
Endpoint      | Method        | API Type      | Description     
------------- | ------------- | ------------- | ------------- 
`/users/[:id]/report`   | POST   | Application | report this user

### 9. Preferences
Endpoint      | Method        | API Type      | Description     
------------- | ------------- | ------------- | ------------- 
`/me/preferences`   | GET   | Application | get the current user's preferences
`/me/preferences`   | PUT   | Application | change the current user's preferences

## Activities
### 1. Get the user's activities
Endpoint      | Method        | API Type      | Description     
------------- | ------------- | ------------- | ------------- 
`/users/[:id]/activities`   | GET   | Application | get the user's activities

### 2. Get the current user's friends activities
Endpoint      | Method        | API Type      | Description     
------------- | ------------- | ------------- | ------------- 
`/users/[:id]/activities/friends`   | GET | Application | get the user's friends' activities

### 3. Create an activity for a user
Endpoint      | Method        | API Type      | Description     
------------- | ------------- | ------------- | ------------- 
`/users/[:id]/activities`  | POST | Admin | create an activity for a user
`/me/activities` | POST | Application | create an activity for the current user

### 4. Create a trending activity
Endpoint      | Method        | API Type      | Description     
------------- | ------------- | ------------- | ------------- 
`/activities/trending`  | POST | Admin | create a trending activity

### 5. Get the the trending activities
Endpoint      | Method        | API Type      | Description     
------------- | ------------- | ------------- | ------------- 
`/activities/trending`  | GET | Application | get the trending activities

## Public Chat Channels
Public chat channels are open to any user. 
### 1. Get all chat channels
Endpoint      | Method        | API Type      | Description     
------------- | ------------- | ------------- | ------------- 
`/chat_channels` | GET | Application | get all the public chat channels

### 2. Favorite/unfavorite a chat channel
Endpoint      | Method        | API Type      | Description     
------------- | ------------- | ------------- | ------------- 
`/chat_channels/[:id]/favorite` | PUT | Application | favorite a chat channel for the current user
`/chat_channels/[:id]/unfavorite` | PUT | Application | unfavorite a chat channel for the current user

### 3. Get online users in a chat channel
Endpoint      | Method        | API Type      | Description     
------------- | ------------- | ------------- | ------------- 
`/chat_channels/[:id]/users` | GET | Application | get the current online users in the chat channel
`/chat_channels/[:id]/users/count` | GET | Application | get the count of the online users in the chat channel
`/chat_channels/user_counts` | GET | Application | get the count of the online users in all of the chat channels

### 4. Create a chat channel
Endpoint      | Method        | API Type      | Description     
------------- | ------------- | ------------- | ------------- 
`/chat_channels` | POST | Application | create a chat channel

### 5. Modify a chat channel
Endpoint      | Method        | API Type      | Description     
------------- | ------------- | ------------- | ------------- 
`/chat_channels/[:id]` | PUT | Application | modify a chat channel

### 6. Delete a chat channel
`/chat_channels/[:id]` | DELETE | Application | delete a chat channel

## Chat Groups
Chat groups are created by users or the admin, and other users can only join the group if they are invited by users in the group or the admin.

### 1. Create a chat group
Endpoint      | Method        | API Type      | Description     
------------- | ------------- | ------------- | ------------- 
`/chat_groups`| POST          | Application   | create a chat group

#### Request Parameters
```javascript
{
	"id": string,			// required, id of the chat group
	"name": string,			// required, the name of the chat group
	"memebers": string,		// required, an array of the id's of the users who you want to be in this group
	"owner_id"				// optional, the user id of the owner of the group
}
```

#### JSON Response
```javascript
{
	"id": string,
	"name": string,
	"members": array,
	"owner_id": string,
	"dialog_id": string		// the id of the chat dialog of this group.
}
```

### 2. Modify a chat group
Endpoint      | Method        | API Type      | Description     
------------- | ------------- | ------------- | ------------- 
`/chat_group/[:id]` | PUT | Application | modify a chat group

#### Request Parameters
```javascript
{
	"name": string,			// optional, the name of the chat group
	"owner_id"				// optional, the user id of the owner of the group
}
```

### 3. Add users to a chat group
Endpoint      | Method        | API Type      | Description     
------------- | ------------- | ------------- | ------------- 
`/chat_group/[:id]/add_users` | POST | Application | add users to a chat group. After they users are added to the group, they will start receiving new messages from this group.

#### Request Parameters
```javascript
{
	"new_members": array,		// required, the id's of the users who you want to add to the chat group
}
```

### 4. Remove users from a chat group
Endpoint      | Method        | API Type      | Description     
------------- | ------------- | ------------- | ------------- 
`/chat_group/[:id]/remove_users` | POST | Application | add users to a chat group. After they users are added to the group, they will start receiving new messages from this group.

#### Request Parameters
```javascript
{
	"new_members": array,		// required, the id's of the users who you want to add to remove from the chat group
}
```

### 5. Delete a chat group
Endpoint      | Method        | API Type      | Description     
------------- | ------------- | ------------- | ------------- 
`/chat_group/[:id]` | DELETE | Application | The owner or admin can delete a chat group

## Messaging
### 1. Sending a message
Endpoint      | Method        | API Type      | Description     
------------- | ------------- | ------------- | ------------- 
`/dialogs/[:id]/messages` | POST | Application | Send a message in a dialog
`/users/[:id]/messages` | POST | Application | Send a message to a user
`/chat_groups/[:id]/messages` | POST | Application | Send a message to a chat group
`/chat_channels/[:id]/messages` | POST | Application | Send a message to a chat channel

### 2. Receiving a message
Messages are received in real time via native callbacks. 

## Dialogs
### 1. Get all dialogs that the user is in
Endpoint      | Method        | API Type      | Description     
------------- | ------------- | ------------- | ------------- 
`/dialogs` | GET | Application | get All dialogs that the user is currently in


### 2. Create a dialog (start chat)
Endpoint      | Method        | API Type      | Description     
------------- | ------------- | ------------- | ------------- 
`/dialogs` | POST | Application | create a chat dialog with other users

## Notifications
### 1. Create a notification
Endpoint      | Method        | API Type      | Description    
------------- | ------------- | ------------- | -------------
`/notifications`  | POST | Admin | Create a notification

### 2. Get all notifications for a user
Endpoint      | Method        | API Type      | Description        
------------- | ------------- | ------------- | ------------
`/users/[:id]/notifications`  | GET | Application | fetch all notifications for the user

## Constants
## Admin APIs
### 1. Batch create users
Endpoint      | Method        | API Type      | Description
------------- | ------------- | ------------- | -------------
`/users/batch_create`   | POST           | Admin   | create multiple users

### 2. Export and import social graph
Endpoint      | Method        | API Type      | Description
------------- | ------------- | ------------- | -------------
`/social_graph`   | GET           | Admin   | export social graph
`/social_graph`   | POST          | Admin   | export social graph

### 3. Update user token
Endpoint      | Method        | API Type      | Description
------------- | ------------- | ------------- | -------------
`/users/[:id]/update_token`   | PUT | Admin, Application   | change the user's token

## Errors
When errors are returned, they will be in a JSON object that contains information you need to interpret them.
Sample error json:

```javascript
{
    "error": {
        "code": 100,
        "reason": "invalid parameters"
        "detail": "user id cannot be empty"
        "more_info": "https://appfriends.me/documentation"
    }
}
``` 
### Error Codes
Error Code | Description
-----------|-------------
1          | unknown error
4          | application request limit reached
5          | application does not have permission
6          | requests are too frequent
100        | invalid parameters
104        | incorrect signature
190			 | need to login to perform this request
200        | need user to agree to permissions first 
202        | operation cannot complete 
203			 | navigation url not found
405			 | user authentication failed
406			 | your account is logged in on another device
502			 | under maintenance
503 		 | verify new device failed 

