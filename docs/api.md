# AppFriends API Documentation
AppFriends API can be used to authenticate user, send messages, search for user, update user information, create social relationship and etc.

- For user related APIs and users search. See [Users](#Users).
- For open chat channels. See [Channels](#Channels).
- For messaging. See [Messaging](#Messaging).
- For admin API's, see [Admin API](#Admin-APIs).

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

## Followers and Friends

### 1. Get a user's followers
Endpoint      | Method        | API Type      | Description      
------------- | ------------- | ------------- | -------------
`/users/[:id]/followers`   | GET | Application | Get all the followers of the user.

#### Response
```javascript
{
[
    {
      "id": "782",
      "user_name": "wshucn7",
      "avatar": "https://cdn1.iconfinder.com/data/icons/user-pictures/100/male3-128.png"
    	"custom_data": string,		// optional , custom data of the user
    },
    {
      "id": "3",
      "user_name": "haowang",
      "avatar": "https://robohash.org/3"
    	"custom_data": string,		// optional , custom data of the user
    },
    ...
  ]
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
------

### 3. Make the current user follow a user
Endpoint      | Method        | API Type      | Description      
------------- | ------------- | ------------- | -------------
`/me/:id/follow`  | PUT | Application | Make the current user follow a user

------

### 4. Make the current user unfollow a user
Endpoint      | Method        | API Type      | Description      
------------- | ------------- | ------------- | -------------
`/me/:id/unfollow`  | PUT | Application | Make the current user unfollow a user

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

## Channels
Chat channels are open to any user.
### 1. Get all chat channels
Endpoint      | Method        | API Type      | Description     
------------- | ------------- | ------------- | -------------
`/channels` | GET | Application | get all the public chat channels

#### Response
```javascript
[
{
	"name": string,						// chat channel name
	"title": string, 					// title of the activity
	"cover_image_url": string,			// the cover image of the channel
	"custom_data": string, 				// custom data. If you want to send object or json, please convert to string
},
....
]
```
------

### 2. Create a chat channel
Endpoint      | Method        | API Type      | Description     
------------- | ------------- | ------------- | -------------
`/channels` | POST | Application | create a chat channel

#### Request
```javascript
{
	"name": string,						// chat channel name
	"title": string, 					// title of the activity
	"cover_image_url": string,			// the cover image of the channel
	"custom_data": string, 				// custom data. If you want to send object or json, please convert to string
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

### 3. Modify a chat channel
Endpoint      | Method        | API Type      | Description     
------------- | ------------- | ------------- | -------------
`/channels/[:id]` | PUT | Application | modify a chat channel

#### Request
```javascript
{
	"name": string,						// optional, chat channel name
	"title": string, 					// optional, title of the activity
	"cover_image_url": string,			// optional, the cover image of the channel
	"custom_data": string, 				// custom data. If you want to send object or json, please convert to string
}
```
------

### 4. Delete a chat channel
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
### 3. Modify a dialog
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

### 4. Add users to a group chat dialog
Endpoint      | Method        | API Type      | Description     
------------- | ------------- | ------------- | -------------
`/dialogs/[:id]/members` | POST | Application | add users to a dialog. After they users are added to the dialog, they will start receiving new messages from this dialog.

#### Request Parameters
```javascript
{
	"members": array,		// required, the id's of the users who you want to add to the dialog
}
```

### 5. Remove users from a chat group
Endpoint      | Method        | API Type      | Description     
------------- | ------------- | ------------- | -------------
`/dialogs/[:id]/members ` | DELETE | Application | remove users from a dialog.

#### Request Parameters
```javascript
{
	"members": array,		// required, the id's of the users who you want to add to remove from the dialog
}
```

### 6. Delete a chat group
this api is only available to the owner of the group or using the admin secret

Endpoint      | Method        | API Type      | Description     
------------- | ------------- | ------------- | -------------
`/dialogs/[:id]` | DELETE | Application | The owner or admin can delete a dialog

## Admin APIs
### 1. Batch create and update users
Endpoint      | Method        | API Type      | Description
------------- | ------------- | ------------- | -------------
`/users/batch_import`   | POST           | Admin   | create multiple users
`/users/batch_change`   | PUT            | Admin   | update multiple users

#### Request Body
```javascript
// array of users
[
  {
    "id": "1235",
    "user_name": "kejia",
    "avatar": "https://avatar.appfriends.me/kejia.png",
    "email": "kejia@gmail.com",
    "custom_data": "champion" // custom data of the user
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
  },``
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
