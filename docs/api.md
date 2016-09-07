# AppFriends API Documentation
AppFriends API can be used to authenticate user, send messages, search for user, update user information, create social relationship and etc.

- For user related APIs and users search. See [Users](#Users).
- For messaging. See [Messaging](#Messaging).

Most of the AppFriends APIs are accessed by using REST API

## REST API's

Base URL: **https://appfriends-api.hacknocraft.com/api/v3/**

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
    
### 1. Get User information
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
    "custom_data": string,					// custom data of the user
}
```
------
### 2. Update User information
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
   "custom_data": string,					// optional , custom data of the user
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
    "custom_data": string,		// optional , custom data of the user
}
```

### 3. Online Users
Endpoint      | Method        | API Type      | Description
------------- | ------------- | ------------- | -------------
`/users/online`   | GET           | Application   | Get the users who are currently online

#### Response
```javascript
// array of online users
[
	{
	    "id": string, 				// user id provided by hosting app 
	    "user_name": string,		// username
	    "avatar": string,			// user's avatar if provided
    	 "custom_data": string,		// optional , custom data of the user
	}, 
	{
	    "id": string, 				
	    "user_name": string,		
	    "avatar": string,	
    	 "custom_data": string,		// optional , custom data of the user		
	}
	...
]
```

### 3. Online Users
Endpoint      | Method        | API Type      | Description
------------- | ------------- | ------------- | -------------
`/users/online/count`   | GET           | Application   | Get the count of the users who are currently online


## Followers and Friends

### 1. Get a user's followers
Endpoint      | Method        | API Type      | Description      
------------- | ------------- | ------------- | -------------
`/users/[:id]/followers`   | GET | Application | Get all the followers of the user.

#### Response
```javascript
{
  "users": [
    {
      "id": "782",
      "user_name": "wshucn7",
      "avatar": "https://cdn1.iconfinder.com/data/icons/user-pictures/100/male3-128.png"
    },
    {
      "id": "3",
      "user_name": "haowang",
      "avatar": "https://robohash.org/3"
    },
    ...
  ],
  "paging": {
    "cursors": {
      "after": 1463167249339,
      "before": 1463252914178
    },
    "next": "https://appfriends-staging-api.hacknocraft.com/api/v3/users/online?limit=25&after=1463167249339",
    "previous": "https://appfriends-staging-api.hacknocraft.com/api/v3/users/online?limit=25&before=1463252914178"
  }
}
```
------

### 2. Get the users who a user is following
Endpoint      | Method        | API Type      | Description      
------------- | ------------- | ------------- | -------------
`/users/[:id]/followings`  | GET | Application | Get all the users that the user is following.

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

### 3. Make the current user follow a user
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

### 4. Make the current user unfollow a user
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

### 5. Get the friends of a user
Endpoint      | Method        | API Type      | Description     
------------- | ------------- | ------------- | ------------- 
`/users/[:id]/Friends`   | GET   | Application | Get the user's friends

!!! note "who are my friends?"
    Friends are users who follow each other.
    
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

## Block/unblock users
Endpoint      | Method        | API Type      | Description     
------------- | ------------- | ------------- | ------------- 
`/users/[:id]/block`   | POST   | Application | Block this user
`/users/[:id]/unblock` | POST   | Application | Unblock this user

------

## Reporting a user
Endpoint      | Method        | API Type      | Description     
------------- | ------------- | ------------- | ------------- 
`/users/[:id]/report`   | POST   | Application | report this user

#### Request Parameters
```javascript
{
	"reason": string, 			// the reason why the user is being reported
}
```
------

## Chat Channels
Chat channels are open to any user. 
### 1. Get all chat channels
Endpoint      | Method        | API Type      | Description     
------------- | ------------- | ------------- | ------------- 
`/channels` | GET | Application | get all the public chat channels

#### Response
```javascript
[
{
	
},
....
]
```
------


### 4. Get online users in a chat channel
Endpoint      | Method        | API Type      | Description     
------------- | ------------- | ------------- | ------------- 
`/channels/[:id]/users` | GET | Application | get the current online users in the chat channel

#### Response
```javascript
// array of users
{
  "total_count": 2,
  "total_page": 1,
  "current_page": 1,
  "users": [
		{
		    "id": string, 				// user id 
		    "user_name": string,		// username
		    "avatar": string,			// user's avatar if provided
		},
		{
			...
		},
		...
	]
}
```
------

### 5. Get online user count for a channel
Endpoint      | Method        | API Type      | Description     
------------- | ------------- | ------------- | ------------- 
`/channels/[:id]/users/count` | GET | Application | get the count of the online users in the chat channel

#### Response
```javascript
{
	"id": int,			// channel id
	"count": int		// online user count
}
```
------

### 6. Get online user count for all the channels
Endpoint      | Method        | API Type      | Description     
------------- | ------------- | ------------- | ------------- 
`/channels/user_counts` | GET | Application | get the count of the online users in all of the chat channels

#### Response
```javascript
[
	{
		"id": int,			// channel id
		"count": int		// online user count
	},
	{
		...
	},
	....
]
```
------

### 7. Create a chat channel
Endpoint      | Method        | API Type      | Description     
------------- | ------------- | ------------- | ------------- 
`/channels` | POST | Application | create a chat channel

#### Request
```javascript
{
	"name": string,						// chat channel name
	"title": string, 					// title of the activity
	"cover_image_url": string,			// the cover image of the channel
}
```
#### Response
```javascript
{
	"id": int, 							// chat channel id
	"name": string,						// chat channel name
	"title": string, 					// title of the activity
	"create_time": int,					// create time of the channel
	"cover_image_url": string,			// the cover image of the channel
}
```
------

### 8. Modify a chat channel
Endpoint      | Method        | API Type      | Description     
------------- | ------------- | ------------- | ------------- 
`/channels/[:id]` | PUT | Application | modify a chat channel

#### Request
```javascript
{
	"name": string,						// optional, chat channel name
	"title": string, 					// optional, title of the activity
	"cover_image_url": string,			// optional, the cover image of the channel
}
```
------

### 10. Delete a chat channel
`/channels/[:id]` | DELETE | Application | delete a chat channel


## Messaging
### 1. Sending a message
Endpoint      | Method        | API Type      | Description     
------------- | ------------- | ------------- | ------------- 
`/dialogs/[:id]/messages` | POST | Application | Send a message in a dialog
`/users/[:id]/messages` | POST | Application | Send a message to a user
`/channels/[:id]/messages` | POST | Application | Send a message to a chat channel

#### Request
```javascript
{
	"text": string,						// message content
	"custom_data": string, 				// custom data. If you want to send object or json, please convert to string
}
```

#### Response
```javascript
{
	"text": string,						// message content
	"custom_data": string, 				// custom data. If you want to send object or json, please convert to string
	"meta_data": string, 				// meta data. Reserved field
	"dialog_id": string,				// dialog id
	"dialog_type": string,				// dialog type: i (individual), g (group), c (channel), s (system)
}
```

### 2. Receiving messages
To receive messages, you need to use the native code:

```javascript
// iOS Swift
HCSDKCore.sharedInstance.syncDelegate = self
```

Then implement:

```
public func messagesReceived(messages: [[String : AnyObject]]) 
```

## Dialogs
### 1. Create a dialog
To start a new conversation, call this method to create a dialog with users. You can then add or remove users from it.

Endpoint      | Method        | API Type      | Description     
------------- | ------------- | ------------- | ------------- 
`/dialogs`    | POST          | Application   | create a chat dialog

#### Request Parameters
```javascript
{
	"name": string,			// required, the name of the dialog
	"members": array,		// required, an array of the id's of the users who you want to be in this dialog
	"owner_id"				// optional, the user id of the owner of the dialog
}
```

#### JSON Response
```javascript
{
	"id": string,			// the id of the newly created chat dialog.
	"name": string,			// the name of the dialog
	"members": array,		// members in the dialog
	"owner_id": string		// owner id, if provided
}
```

### 2. Get all dialogs that the user is in 
When you want to start chat for user, you need to call this api to create a dialog first. 
 
Endpoint      | Method        | API Type      | Description     
------------- | ------------- | ------------- | ------------- 
`/dialogs`    | GET           | Application   | get All dialogs that the user is currently in

#### JSON Response
```javascript
// an array of dialogs
[
	{
		"id": string,			// the id of the chat dialog
		"name": string,			// the name of the dialog		"members": array,		// members in the dialog
		"owner_id": string		// owner id, if provided
	},
	{
	...
	}
	...
]
```
### 2. Modify a dialog
Endpoint      | Method        | API Type      | Description     
------------- | ------------- | ------------- | ------------- 
`/dialogs/[:id]` | PUT | Application | modify a dialog

#### Request Parameters
```javascript
{
	"name": string,			// optional, the name of the dialog
	"owner_id"				// optional, the user id of the owner of the dialog
}
```

### 3. Add users to a chat group
Endpoint      | Method        | API Type      | Description     
------------- | ------------- | ------------- | ------------- 
`/dialogs/[:id]/members` | POST | Application | add users to a dialog. After they users are added to the dialog, they will start receiving new messages from this dialog.

#### Request Parameters
```javascript
{
	"members": array,		// required, the id's of the users who you want to add to the dialog
}
```

### 4. Remove users from a chat group
Endpoint      | Method        | API Type      | Description     
------------- | ------------- | ------------- | ------------- 
`/dialogs/[:id]/members ` | DELETE | Application | remove users from a dialog. 

#### Request Parameters
```javascript
{
	"members": array,		// required, the id's of the users who you want to add to remove from the dialog
}
```

### 5. Delete a chat group
this api is only available to the owner of the group or using the admin secret

Endpoint      | Method        | API Type      | Description     
------------- | ------------- | ------------- | ------------- 
`/dialogs/[:id]` | DELETE | Application | The owner or admin can delete a dialog

## Admin APIs
### 1. Batch create and update users
Endpoint      | Method        | API Type      | Description
------------- | ------------- | ------------- | -------------
`/users/batch_create`   | POST           | Admin   | create multiple users
`/users/batch_update`   | PUT            | Admin   | update multiple users

#### Request Body
```javascript
// array of users
[
  {
    "id": "1235",
    "user_name": "kejia",
    "avatar": "https://avatar.appfriends.me/kejia.png",
    "email": "kejia@gmail.com",
    "note": "champion" // notes for this user, if it has value, it will be displayed below the user name in the default UI
  },
  {
    "id": "1236",
    "user_name": "shuwei",
    "avatar": "https://avatar.appfriends.me/shuwei.png"
  },
  {
    "id": "1237",
    "user_name": "mike",
    "avatar": "https://avatar.appfriends.me/mike.png"
  },
  ...
 ]

```

### 2. Export and import social graph
**Import social graph**

Endpoint      | Method        | API Type      | Description
------------- | ------------- | ------------- | -------------
`/social_graph`   | POST          | Admin   | export social graph

#### Request Body
```javascript
// id is the user, and followers and followings contains the id's
[
  {
    "id": "16",
    "followers": ["11","12" ...],
    "followings": ["11, "12" ...]
  },
  {
    "id": "19",
    "followers": ["11","12" ...],
    "followings": ["11, "12" ...]
  },
  ....
]

```
**Export social graph**

Endpoint      | Method        | API Type      | Description
------------- | ------------- | ------------- | -------------
`/social_graph`   | GET           | Admin   | export social graph

#### Response Body
```javascript
// id is the user, and friend id is the friend of the user
[
  {
    "id": "16",
    "followers": ["11","12" ...],
    "followings": ["11, "12" ...]
  },
  {
    "id": "19",
    "followers": ["11","12" ...],
    "followings": ["11, "12" ...]
  },
  ....
]

```

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
504        | internet not available

