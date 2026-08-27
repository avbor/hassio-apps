# Changelog

## 10.3

Highlighted changes for Telegram Bot API:

- Add the option `--files-dir`.
- Update TDLib to 1.8.67.

Changelog for 10.0 API version is based on release notes at: <https://core.telegram.org/bots/api>:

**Rich Messages**

- Added the class RichMessageButton representing a button in a RichMessage.
- Added the class RichTextButton.
- Added the classes RichBlockButtons and InputRichBlockButtons.
- Added the field is_compact to the classes RichBlockTable and InputRichBlockTable.
- Added the classes RichBlockExpandableBlockQuotation and InputRichBlockExpandableBlockQuotation representing a block quotation, which can be expanded or collapsed back.
- Added the classes RichBlockDocument and InputRichBlockDocument, containing a file.
- Added support for links of the form tg://document?id= for general file uploads in rich messages.

**Ephemeral messages**

- Added the class EphemeralMessageParameters and replaced the parameters receiver_user_id and callback_query_id in the methods sendMessage, sendAnimation, sendAudio, sendDocument, sendLivePhoto, sendPhoto, sendSticker, sendVideo, sendVideoNote, sendVoice, sendContact, sendLocation and sendVenue with the parameter ephemeral_message_parameters.
- Added the parameter ephemeral_message_parameters to the method sendRichMessage.
- Added the field replace_callback_query_message to the class EphemeralMessageParameters, which allows bots to show an ephemeral message in place of the original message.
Supported upload of new files in editEphemeralMessageMedia.
- Added the parameter show_caption_above_media to the method editEphemeralMessageCaption.
- Added the parameter rich_message to the method editEphemeralMessageText.
- Added the field can_send_welcome_messages to the classes ChatAdministratorRights and ChatMemberAdministrator.
- Added the parameter can_send_welcome_messages to the method promoteChatMember.

**Reply markup**

- Added the class DisabledButton and the field disabled to the class InlineKeyboardButton.
- Added the field force_reply to the classes InlineKeyboardMarkup and ReplyKeyboardMarkup.

**General**

- Added the parameters can_stop and keep_on_stop to the methods sendMessageDraft and sendRichMessageDraft.
- Added updates about user stopping message generation, represented by the class MessageGenerationStopped and the field stopped_message_generation in the class Update.
- Added the class CommunityChatJoined and the field community_chat_joined to the class Message for service messages about join of a chat from a community.
- Added the fields text, entities and is_private to the class UniqueGiftInfo.

## 10.2

Highlighted changes for Telegram Bot API:

- Update TDLib to 1.8.66.

Changelog for 10.0 API version is based on release notes at: <https://core.telegram.org/bots/api>:

**Rich Messages**

- Added the class InputRichMessageMedia and the field media to the class InputRichMessage, allowing bots to explicitly specify media used in markdown or html formatting when sending a rich message.
- Added the class InputMediaVoiceNote, representing a voice message to be sent.
- Added the class InputRichBlockListItem, which represents an item in a list to be sent.
- Added the classes InputRichBlockParagraph, InputRichBlockSectionHeading, InputRichBlockPreformatted, InputRichBlockFooter, InputRichBlockDivider, InputRichBlockMathematicalExpression, InputRichBlockAnchor, InputRichBlockList, InputRichBlockBlockQuotation, InputRichBlockPullQuotation, InputRichBlockCollage, InputRichBlockSlideshow, InputRichBlockTable, InputRichBlockDetails, InputRichBlockMap, InputRichBlockAnimation, InputRichBlockAudio, InputRichBlockPhoto, InputRichBlockVideo, InputRichBlockVoiceNote and InputRichBlockThinking, which represent different types of blocks available to format an outgoing rich message.
- Added the field blocks to the class InputRichMessage, allowing bots to specify rich message formatting via block entities.

**Ephemeral Messages**

- Introduced support for Ephemeral Messages, allowing bots to send group messages and receive commands that are visible only to a specific user and the bot.
- Added the field is_ephemeral to the class BotCommand.
- Added the field receiver_user to the class Message.
- Added the field ephemeral_message_id to the class Message.
- Added the parameters receiver_user_id and callback_query_id to the methods sendMessage, sendAnimation, sendAudio, sendDocument, sendLivePhoto, sendPhoto, sendSticker, sendVideo, sendVideoNote, sendVoice, sendContact, sendLocation, sendVenue.
- Added the field ephemeral_message_id to the class ReplyParameters, allowing bots to reply to ephemeral messages.
Marked the field message_id in the class ReplyParameters as optional if the field ephemeral_message_id is present.
- Added the methods editEphemeralMessageText, editEphemeralMessageMedia, editEphemeralMessageCaption, and editEphemeralMessageReplyMarkup allowing bots to edit ephemeral messages.
- Added the method deleteEphemeralMessage allowing bots to delete ephemeral messages.

**Communities**

- Introduced initial support for Communities - several supergroups, channels, and bots linked together around a shared topic or audience.
- Added the class Community which represents a community.
- Added the class CommunityChatAdded and the field community_chat_added to the class Message.
- Added the class CommunityChatRemoved and the field community_chat_removed to the class Message.
- Added the field community to the class ChatFullInfo.

**General**

- Added updates about changes to a user payment subscription, represented by the class BotSubscriptionUpdated and the field subscription in the class Update.
- Hardened the security of Mini Apps by disallowing the usage of Mini App methods from origins different from the original Mini App domain. The protection will be automatically enabled for all Mini Apps on July 20, 2026. You can opt-out from the protection through the @BotFather Mini App. If you do so, you acknowledge that it is the responsibility of the bot to ensure that the Mini App has no links to untrusted sites.

## 10.1

Highlighted changes for Telegram Bot API:

- Update TDLib to 1.8.65.

Changelog for 10.0 API version is based on release notes at: <https://core.telegram.org/bots/api>:

**Rich Messages**

- Added support for Rich Messages, allowing bots to send highly structured text and stream AI-generated replies with seamless rich formatting.
- Added the classes RichTextBold, RichTextItalic, RichTextUnderline, RichTextStrikethrough, RichTextSpoiler, RichTextDateTime, RichTextTextMention, RichTextSubscript, RichTextSuperscript, RichTextMarked, RichTextCode, RichTextCustomEmoji, RichTextMathematicalExpression, RichTextUrl, RichTextEmailAddress, RichTextPhoneNumber, RichTextBankCardNumber, RichTextMention, RichTextHashtag, RichTextCashtag, RichTextBotCommand, RichTextAnchor, RichTextAnchorLink, RichTextReference and RichTextReferenceLink, which represent different types of rich formatted text.
- Added the class RichText, which represents rich formatted text.
- Added the class RichBlockCaption, which represents the caption of a rich formatted text.
- Added the class RichBlockTableCell, which represents a cell in a table.
- Added the class RichBlockListItem, which represents an item in a list.
- Added the classes RichBlockParagraph, RichBlockSectionHeading, RichBlockPreformatted, RichBlockFooter, RichBlockDivider, RichBlockMathematicalExpression, RichBlockAnchor, RichBlockList, RichBlockBlockQuotation, RichBlockPullQuotation, RichBlockCollage, RichBlockSlideshow, RichBlockTable, RichBlockDetails, RichBlockMap, RichBlockAnimation, RichBlockAudio, RichBlockPhoto, RichBlockVideo, RichBlockVoiceNote and RichBlockThinking, which represent different types of blocks in a rich formatted message.
- Added the class RichBlock, which represents a block in a rich formatted message.
- Added the class RichMessage, which represents a rich formatted message.
- Added the field rich_message to the class Message.
- Added the class InputRichMessage, describing a rich message to send.
- Added the class InputRichMessageContent and allowed it to be used as InputMessageContent in results of inline, guest, and Web App queries.
- Added the method sendRichMessage, allowing bots to send rich messages.
- Added the method sendRichMessageDraft, allowing bots to stream partial rich messages.
- Added the parameter rich_message to the method editMessageText, allowing bots to edit rich messages.

**Join Request Queries**

- Added the field supports_join_request_queries to the class User.
- Added the field guard_bot to the class ChatFullInfo.
- Added the field query_id to the class ChatJoinRequest.
- Added the method answerChatJoinRequestQuery.
- Added the method sendChatJoinRequestWebApp.

**Polls**

- Added the class Link and the field link to the class PollMedia.
- Added the class InputMediaLink and allowed it to be used as InputPollOptionMedia.

## 10.0

Highlighted changes for Telegram Bot API:

- Update TDLib to 1.8.64.

Changelog for 10.0 API version is based on release notes at: <https://core.telegram.org/bots/api>:

**Guest Mode**

- Introduced support for guest mode, allowing bots to receive certain messages and issue replies within chats they are not a member of.
- Added the field supports_guest_queries to the class User.
- Added the fields guest_bot_caller_user and guest_bot_caller_chat to the class Message.
- Added the field guest_query_id to the class Message.
- Added the field guest_message to the class Update.
- Added the class SentGuestMessage and the method answerGuestQuery.

**Chat Management**

- Added the field can_react_to_messages to the classes ChatMemberRestricted and ChatPermissions.
- Added the parameter return_bots to the method getChatAdministrators.
- Added the method deleteAllMessageReactions.
- Added the method deleteMessageReaction.
- Added the ability to see certain messages sent by other bots in groups.

**Polls**

- Added the classes InputMediaSticker, InputMediaLocation, and InputMediaVenue.
- Added the class PollMedia, representing a media in a poll.
- Added the field media to the class Poll, allowing bots to see media in polls.
- Added the field explanation_media to the class Poll, allowing bots to see media in quiz explanations.
- Added the field media to the class PollOption, allowing bots to see media in poll options.
- Added the class InputPollMedia and the parameters media and explanation_media to the method sendPoll, allowing bots to add media to polls.
- Added the class InputPollOptionMedia and the field media to the class InputPollOption, allowing bots to add media to poll options.
- Added the field members_only to the class Poll.
- Added the parameter members_only to the method sendPoll.
- Added the field country_codes to the class Poll.
- Added the parameter country_codes to the method sendPoll.
- Decreased the minimum number of poll options from 2 to 1.

**Live photos**

- Added the class LivePhoto, which represents a photo with a short video.
- Added the class InputMediaLivePhoto.
- Added the field live_photo to the classes Message and ExternalReplyInfo.
- Added the method sendLivePhoto, allowing bots to send live photos.
- Added the class PaidMediaLivePhoto, which describes a paid media with a live photo.
- Added the class InputPaidMediaLivePhoto, allowing bots to send live photos as paid media.
- Allowed to use live photos in sendMediaGroup and editMessageMedia,

**General**

- Allowed Business Bots to manage user accounts without a Telegram Premium subscription.
- Added the ability to send messages to other bots via username if both bots enabled bot-to-bot communication.
- Added the ability to reply to other bots from a business bot if the business bot enabled bot-to-bot communication.
- Allowed bots to pass an empty text in the method sendMessageDraft.
- Added the class BotAccessSettings and the method getManagedBotAccessSettings.
- Added the method setManagedBotAccessSettings.
- Added the method getUserPersonalChatMessages.

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
