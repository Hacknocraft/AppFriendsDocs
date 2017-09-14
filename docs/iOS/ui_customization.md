# UI Customization
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
gifContentRating          |     AFGifContentRating      |     .parentalGuide13      | change this value to control the gif
showDialogAlbum           |     Boolean      |     true      | change to false if you don't want to use the dialog album
enableContentFlagging     |     Boolean      |     false     | change to true if you want to be able to flag content on the chat view

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
locationTitleFont         |     UIFont       |  UIFont.boldSystemFont(ofSize: 16)  | location message title font
locationSubtitleFont      |     UIFont       |  UIFont.systemFont(ofSize: 15)  | location message description label font
emptyTableLabelFont       |     UIFont       |  UIFont.systemFont(ofSize: 15)  | the font for the label to use when the table is empty
albumSectionTitleFont     |     UIFont       |  UIFont.systemFont(ofSize: 15)  | album date title label font
chatDialogListSectionTitleFont    |     UIFont       |  UIFont.systemFont(ofSize: 15)  | dialog list section title font
chatDialogListCellTitleFont       |     UIFont       |  UIFont.systemFont(ofSize: 16)  | dialog list cell title (user name or dialog title) font
chatDialogListCellTimestampFont   |     UIFont       |  UIFont.systemFont(ofSize: 13)  | dialog list cell timestamp label font
chatDialogListCellLastMessageFont |     UIFont       |  UIFont.systemFont(ofSize: 13)  | dialog list cell last message label font

HCColorPalette                 |
-------------                  |   -------------   |   -------------     |   -------------
**Variable Name**              |    **Type**       |  **Default Value**  |     **Description**
chatBackgroundColor            |     UIColor       |  #0d0e28            | the background color of the chat views
chatOutMessageContentTextColor |     UIColor       |  white              | outgoing message content text color
chatInMessageContentTextColor  |     UIColor       |  black              | received message content text color
chatUserNamelTextColor         |     UIColor       |  white              | the user name label color in the chat view
chatTimeLabelTextColor         |     UIColor       |  lightgray          | time stamp label color in chat view
chatDateLabelTextColor         |     UIColor       |  lightgray          | date label color in chat view
chatSystemMessageColor         |     UIColor       |  lightgray          | system message text color in chat view
chatSendButtonColor            |     UIColor       |  #0d0e28            | chat send button color
chatOutMessageBubbleColor      |     UIColor       |  #5e62bc            | outgoing message bubble color
chatInMessageBubbleColor       |     UIColor       |  #93d4f0            | received message bubble color
chatMessageFailedButtonColor   |     UIColor       |  #f2433d            | color of the button to resend message when message failed to send
chatVideoPlayIconColor         |     UIColor       |  black              | video play icon color
chatLeaveConversationColor     |     UIColor       |  #f2433d            | color of the button to leave a dialog
chatNewMessageDividerColor     |     UIColor       |  #f5a59a            | color of the new message divider
chatInMessageLinkColor         |     UIColor       |  #437fb4            | color of the links in received messages
chatOutMessageLinkColor        |     UIColor       |  #f2433d            | color of the links in outgoing messages
chatAttachmentIconColor        |     UIColor       |  #f2433d            | color of the button to add attachment
chatMediaMessageButtonColor    |     UIColor       |  #707378            | color of the media buttons on the media input panel
chatMediaMessageButtonBgColor  |     UIColor       |  #f9fbfb            | background color of the media buttons on the media input panel
chatMediaMessageButtonBorderColor    |     UIColor       |  #e6e8e7      | color of the border of media buttons on the media input panel
chatMediaMessageSelectionPanelColor  |     UIColor       |  #f5f8fa      | color of the media input panel

## Album
Album is a feature including UI components which group all the images and videos sent inside a dialog in chronological order.
To display the album UI, simply use the HCAlbumViewController:
```swift
let albumVC = HCAlbumViewController(dialogID: [dialog id]])
self.navigationController?.pushViewController(albumVC, animated: true)
```
There are some UI configuration you can do on the `HCAlbumViewController`:

HCColorPalette                 |
-------------                  |   -------------   |   -------------     |   -------------
**Variable Name**              |    **Type**       |  **Default Value**  |     **Description**
albumBackgroundColor           |     UIColor       |  #252326 alpha:0.5  | album view background color
albumSectionBackgroundColor    |     UIColor       |  #252326            | album section background color
albumNavigationBarIconColor    |     UIColor       |  #ffffff alpha:0.9  | album navigationbar icon color
albumNavigationBarTitleColor   |     UIColor       |  white              | album navigationbar title color
albumNavigationBackgroundColor |     UIColor       |  #252326            | album navigation background color
albumSectionTitleColor         |     UIColor       |  white              | album section view background color
