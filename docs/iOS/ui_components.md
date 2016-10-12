# UI Components
`AppFriendsUI` provides a lot of useful and convenient UI components for you to use. It can save a lot of your time developing the app. Our [demo app](https://github.com/laeroah/AppFriendsUI/tree/master/Example/AFChatUISample) takes full advantage of the `AppFriendsUI`. You could clone the demo app repo from github to see how it uses, interact and customizes the UI components provided by `AppFriendsUI`.

## Basic Customization
`HCUIConfiguration` gives you easy access to customize AppFriends UI components. For example, if you want to change the background color of the chat view, you can simply do it by changing the value of `HCColorPalette.chatBackgroundColor`

## Advanced Customization
For advanced customization, we recommend you inherit our UI component classes. For example, if you want to change the behavior when the user clicks on a message, you can inherit `HCBaseChatViewController`, and override the implementation of `func tableView(tableView: UITableView, didSelectRowAtIndexPath indexPath: NSIndexPath)`
