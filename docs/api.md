# AppFriends API Documentation
AppFriends API can be used to authenticate user, open the widget to a certain view, control the data and interact with all the features of AppFriends. For example, some common tasks that developers can do includes:

- Signup/login users to AppFriends. See [Authentication](#authentication).
- Open AppFriends widget to certain view. See [Navigation](#navigation).
- Search for users. See [Users](#Users).
- Post an activity for a user. See [Activities](activities).
- Create chat channels. See [Chat Channels](#chat-channels).
- Create chat groups. See [Chat Groups](#chat-groups).
- Send a notification to users. See [Notifications](#notifications).

## Navigation
You can use URL path to navigate inside AppFriends, very similar to how you navigate in a browser. This is a practice we want to encourage your app to adapt as well. It makes routing very easy and works well with deeplinks. If you use AppFriends' sharing and deeplink features, same routing scheme will be used to navigate inside your app.

For example, if you want to open a user's profile in AppFriends widget, you can use this URL: `/user/[:id]/profile` 

###Code Examples
You can use the following code to open a specific view of AppFriends widget. There are options to either open a single view or the entire widget. The difference is that if you open the entire widget, the user can navigate from the view opened to other AppFriends features. If you open a single view, the user will be limited to that one feature.

####Objective-C
	// open entire widget and 
	[HCWidget openView:@"/user/haowang/profile"]; 
	
####Swift
	// 
	HCWidget.openView:("/user/haowang/profile")
	
	//
	HCWidget.openSingleView:("/user/haowang/profile")
	
####Android
	//
	HCWidget.openSingleView:("/user/haowang/profile")

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
To access and modify data on AppFriends, you are ultilize our REST interfacve. 

## User
URL                    | URL           | Description
---------------------- | ------------- | -------------

## Activities
## Chat Channels
## Chat Groups
## Notifications
## Errors