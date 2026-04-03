# Changelog

## 9.6

Highlighted changes for Telegram Bot API:

- Update TDLib to 1.8.63.

Changelog for 9.6 API version is based on release notes at: <https://core.telegram.org/bots/api>:

**Managed Bots**

- Added the field can_manage_bots to the class User.
- Added the class KeyboardButtonRequestManagedBot and the field request_managed_bot to the class KeyboardButton.
- Added the class ManagedBotCreated and the field managed_bot_created to the class Message.
- Added updates about the creation of managed bots and the change of their token, represented by the class ManagedBotUpdated and the field managed_bot in the class Update.
- Added the methods getManagedBotToken and replaceManagedBotToken.
- Added the class PreparedKeyboardButton and the method savePreparedKeyboardButton, allowing bots to request users, chats and managed bots from Mini Apps.
- Added the method requestChat to the class WebApp.
- Added support for https://t.me/newbot/{manager_bot_username}/{suggested_bot_username}[?name={suggested_bot_name}] links, allowing bots to request the creation of a managed bot via a link.

**Polls**

- Added support for quizzes with multiple correct answers.
- Replaced the field correct_option_id with the field correct_option_ids in the class Poll.
- Replaced the parameter correct_option_id with the parameter correct_option_ids in the method sendPoll.
- Allowed to pass allows_multiple_answers for quizzes in the method sendPoll.
- Increased the maximum time for automatic poll closure to 2628000 seconds.
- Added the field allows_revoting to the class Poll.
- Added the parameter allows_revoting to the method sendPoll.
- Added the parameter shuffle_options to the method sendPoll.
- Added the parameter allow_adding_options to the method sendPoll.
- Added the parameter hide_results_until_closes to the method sendPoll.
- Added the fields description and description_entities to the class Poll.
- Added the parameters description, description_parse_mode, and description_entities to the method sendPoll.
- Added the field persistent_id to the class PollOption, representing a persistent identifier for the option.
- Added the field option_persistent_ids to the class PollAnswer.
- Added the fields added_by_user and added_by_chat to the class PollOption, denoting the user and the chat which added the option.
- Added the field addition_date to the class PollOption, describing the date when the option was added.
- Added the class PollOptionAdded and the field poll_option_added to the class Message.
- Added the class PollOptionDeleted and the field poll_option_deleted to the class Message.
- Added the field poll_option_id to the class ReplyParameters, allowing bots to reply to a specific poll option.
- Added the field reply_to_poll_option_id to the class Message.
- Allowed “date_time” entities in checklist title, checklist task text, TextQuote, ReplyParameters quote, sendGift, and giftPremiumSubscription.

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
