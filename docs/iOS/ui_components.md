# UI Components and Customization
`AppFriendsUI` provides a lot of useful and convenient UI components for you to use. It can save a lot of your time developing the app. Our [demo app](https://github.com/Hacknocraft/AppFriendsiOSSample) takes full advantage of the `AppFriendsUI`. You could clone the demo app repo from github to see how it uses, interact and customizes the UI components provided by `AppFriendsUI`.

## Basic Customization
`HCUIConfiguration` gives you easy access to customize AppFriends UI components. For example, if you want to change the background color of the chat view, you can simply do it by changing the value of `HCColorPalette.chatBackgroundColor`

### List of Customizable Values

HCSettingsConfiguation    |
-------------             |   -------------  |   -------------     |   -------------
**Variable Name**         |    **Type**      |  **Default Value**  |     **Description**
badgeDisplayIfMuted       |     Boolean      |     false     | turn this to true if you want to keep badge for a conversation after it's muted.
showNewMessageLine        |     Boolean      |     true      | switch for new message line display on private dialogs
supportedMessageTypes     | ChatSupportedMessageDataTypes |     .all    |  The types of messages you want to support in your chat. This value will apply to all chat. You can also change the types of messages you want to support for each dialog when you initialize the chat view

HCFont                    |
-------------             |   -------------  |   -------------     |   -------------
**Variable Name**         |    **Type**      |  **Default Value**  |     **Description**
segmentSelectorFont       |     UIFont       |  UIFont.systemFont(ofSize: 15)  | segmented control button title font
chatCellContentFont       |     UIFont       |  UIFont.systemFont(ofSize: 15)  | chat message content text font
chatCellSystemMessageFont |     UIFont       |  UIFont.systemFont(ofSize: 15)  | chat system message content text font
boldButtonFont            |     UIFont       |  UIFont.boldSystemFont(ofSize: 16) |  button bold font
dialogSettingFont         |     UIFont       |  UIFont.systemFont(ofSize: 15)  | dialog setting UI text font
navigationBarTitleFont    |     UIFont       |  UIFont.systemFont(ofSize: 17)  | navigation bar title font
chatDialogListSectionTitleFont    |     UIFont       |  UIFont.systemFont(ofSize: 15)  | dialog list section title font
chatTimestampFont         |     UIFont       |  UIFont.systemFont(ofSize: 13)  | chat message time label
chatDateLabelFont         |     UIFont       |  UIFont.systemFont(ofSize: 15)  | chat system date label
