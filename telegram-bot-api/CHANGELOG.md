# Changelog

## 9.5

Highlighted changes for Telegram Bot API:

- Update TDLib to 1.8.62.
- Improve error message.

Changelog for 9.5 API version is based on release notes at: <https://core.telegram.org/bots/api>:

- Added the MessageEntity type “date_time”, allowing bots to show a formatted date and time to the user.
- Allowed all bots to use the method sendMessageDraft.
- Added the field tag to the classes ChatMemberMember and ChatMemberRestricted.
- Added the method setChatMemberTag.
- Added the field can_edit_tag to the classes ChatMemberRestricted and ChatPermissions.
- Added the field can_manage_tags to the classes ChatMemberAdministrator and ChatAdministratorRights.
- Added the parameter can_manage_tags to the method promoteChatMember.
- Added the field sender_tag to the class Message.
- Added the field iconCustomEmojiId to the class BottomButton.

## 9.4.1

App changes:

- Change repository and image names for Docker image.
- Fixes in documentation.
- Cosmetic fixes in app config.

Changelog for 9.4 API version is based on release notes at: https://core.telegram.org/bots/api

## 9.4

- Allowed bots to use custom emoji in messages directly sent by the bot to private, group and supergroup chats if the owner of the bot has a Telegram Premium subscription.
- Allowed bots to create topics in private chats using the method createForumTopic.
- Allowed bots to prevent users from creating and deleting topics in private chats through a new setting in the @BotFather Mini App.
- Added the field allows_users_to_create_topics to the class User.
- Added the field icon_custom_emoji_id to the classes KeyboardButton and InlineKeyboardButton, allowing bots to show a custom emoji on buttons if they are able to use custom emoji in the message.
- Added the field style to the classes KeyboardButton and InlineKeyboardButton, allowing bots to change the color of buttons.
- Added the class ChatOwnerLeft and the field chat_owner_left to the class Message.
- Added the class ChatOwnerChanged and the field chat_owner_changed to the class Message.
- Added the methods setMyProfilePhoto and removeMyProfilePhoto, allowing bots to manage their profile picture.
- Added the class VideoQuality and the field qualities to the class Video allowing bots to get information about other available qualities of a video.
- Added the field first_profile_audio to the class ChatFullInfo.
- Added the class UserProfileAudios and the method getUserProfileAudios, allowing bots to fetch a list of audios added to the profile of a user.
- Added the field rarity to the class UniqueGiftModel.
- Added the field is_burned to the class UniqueGift.
