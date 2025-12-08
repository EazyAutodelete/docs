---
title: Filters
description: The filters allow you to set exactly which messages are deleted.
published: true
date: 2025-12-08T09:10:53.490Z
tags: 
editor: markdown
dateCreated: 2025-11-02T19:52:27.380Z
---

# 🔎 Filters

Filters give you precise control over which messages EazyAutodelete will target for deletion. Choose from a wide variety of filters to match exactly the type of content you want to remove from your channels.

Filters work seamlessly with all [Modes](/config/mode) and can be combined to create sophisticated deletion rules. Use [Filter Behavior](/config/filter-behavior) to control whether messages must match ALL filters (AND logic) or just ONE filter (OR logic) to be deleted.

> **💡 Tip**: Start with simple filters and test in a dedicated channel before applying complex filter combinations to production channels.

## Available Filters

The following table lists all available message filters. Each filter has a unique ID and is designed to target specific message characteristics:

### Type Filters

These filters target messages based on their type and origin characteristics.

| Filter ID | Filter Name | Explanation |
| --------- | ----------- | ----------- |
| **1000** | Is Pinned | Delete messages that are [pinned](https://support.discord.com/hc/en-us/articles/223209547-How-do-I-pin-messages). Useful for removing outdated pinned content. |
| **1001** | Is Not Pinned | Delete messages that are NOT [pinned](https://support.discord.com/hc/en-us/articles/223209547-How-do-I-pin-messages). Use this to protect important pinned messages while cleaning up regular chat. |
| **1010** | Was Published | Delete messages that were published to subscribed channels via [Announcement Channels](https://support.discord.com/hc/en-us/articles/360032008192-Announcement-Channels-). Only available in Announcement channels. |
| **1011** | Was Not Published | Delete messages that were NOT published to subscribed channels. Only available in Announcement channels. Useful for removing unpublished drafts or announcements. |
| **1020** | Is Crosspost | Delete messages that are [crossposts from another server](https://support.discord.com/hc/en-us/articles/360028384531-Channel-Following-FAQ) (received via Channel Following). Helps keep only your original content. |
| **1021** | Is Not Crosspost | Delete messages that are NOT crossposts from another server. Use this to keep followed content while removing your original messages. |
| **1030** | Is Edited | Delete messages that have been edited after being posted. Useful for removing corrected or updated content. |
| **1031** | Is Not Edited | Delete messages that have NOT been edited. Helps preserve edited messages while removing original posts. |
| **1040** | Is Reply | Delete messages that are [Replies](https://support.discord.com/hc/en-us/articles/360057382374-Replies-FAQ) to another message. Useful for cleaning up reply chains while keeping original messages. |
| **1041** | Is Not Reply | Delete messages that are NOT replies. Helps preserve conversation threads while removing standalone messages. |
| **1050** | Sent by Bot | Delete messages from bot accounts. Great for cleaning up bot command responses or automated messages. |
| **1051** | Not Sent by Bot | Delete messages from human users (not bots). Useful when you want to keep bot messages but remove user chat. |
| **1060** | Is Voice Message | Delete [voice messages](https://support.discord.com/hc/en-us/articles/13091096725527-Voice-Messages). Useful for audio content cleanup in text channels. |
| **1061** | Is Not Voice Message | Delete messages that are NOT [voice messages](https://support.discord.com/hc/en-us/articles/13091096725527-Voice-Messages). Preserves voice messages while removing other content. |
| **1070** | Is Webhook | Delete messages from [Webhooks](https://support.discord.com/hc/en-us/articles/228383668-Intro-to-Webhooks). Useful for removing automated webhook posts. |
| **1071** | Is Not Webhook | Delete messages that are NOT from [Webhooks](https://support.discord.com/hc/en-us/articles/228383668-Intro-to-Webhooks). Preserves webhook content while removing regular messages. |
| **1080** | Is System Message | Delete [system messages](https://support.discord.com/hc/en-us/articles/360035873592-Server-Audit-Log) (join messages, boosts, etc.). Keeps your channel free of automated system notifications. |
| **1081** | Is Not System Message | Delete messages that are NOT system messages. Preserves system notifications while removing user content. |

### Attribute Filters

These filters target messages based on their content attributes and attachments.

| Filter ID | Filter Name | Explanation |
| --------- | ----------- | ----------- |
| **2000** | Has Attachment | Delete messages with one or more file [attachments](https://support.discord.com/hc/en-us/articles/206346498-Where-can-I-find-my-User-Server-Message-ID) (images, videos, documents, etc.). Useful for cleaning up media content. |
| **2001** | Has No Attachment | Delete messages with NO attachments. Useful for keeping media while removing text-only messages. |
| **2010** | Has Embed | Delete messages with [embeds](https://discord.com/safety/using-webhooks-and-embeds). Useful for removing rich content and link previews. |
| **2011** | Has No Embed | Delete messages without [embeds](https://discord.com/safety/using-webhooks-and-embeds). Preserves embedded content while removing plain messages. |
| **2020** | Has Thread | Delete messages where a [thread](https://support.discord.com/hc/en-us/articles/4403205878423-Threads-FAQ) was started from this message. Useful for cleaning up messages that have spawned discussions. |
| **2021** | Has No Thread | Delete messages where NO [thread](https://support.discord.com/hc/en-us/articles/4403205878423-Threads-FAQ) was started. Helps preserve messages that have generated discussion threads. |
| **2030** | Has Reaction | Delete messages that have one or more [reactions](https://support.discord.com/hc/en-us/articles/12102061808663-Reactions-and-Super-Reactions-FAQ). Useful for removing popular or engaged content. |
| **2031** | Has No Reaction | Delete messages with no [reactions](https://support.discord.com/hc/en-us/articles/12102061808663-Reactions-and-Super-Reactions-FAQ). Helps preserve messages that users have reacted to. |
| **2040** | Has Image | Delete messages that contain images. Helps clean up visual content while keeping text discussions. |
| **2041** | Has No Image | Delete messages without images. Preserves visual content while removing text-only messages. |
| **2050** | Has Source Message | Delete [crossposted messages](https://support.discord.com/hc/en-us/articles/360028384531-Channel-Following-FAQ) where the original source message still exists. Only applies to Announcement Channel crossposts. |
| **2051** | Has No Source Message | Delete [crossposted messages](https://support.discord.com/hc/en-us/articles/360028384531-Channel-Following-FAQ) where the original source message was deleted. Only applies to Announcement Channel crossposts. |
| **2060** | Has Poll | Delete messages that contain a [Poll](https://support.discord.com/hc/en-us/articles/22163184112407-Polls-FAQ). Useful for cleaning up expired polls. |
| **2061** | Has No Poll | Delete messages without a [Poll](https://support.discord.com/hc/en-us/articles/22163184112407-Polls-FAQ). Preserves active polls while removing other content. |

### Content Filters

These filters target messages based on their text content and special elements.

| Filter ID | Filter Name | Explanation |
| --------- | ----------- | ----------- |
| **3000** | Contains Emoji | Delete messages that contain one or more [emojis](https://support.discord.com/hc/en-us/articles/360036479811-Custom-Emojis) (standard or custom). Helps clean up emoji-heavy messages. |
| **3001** | Contains No Emoji | Delete messages that do NOT contain any emojis. Perfect for preserving emoji reactions visible while removing plain text. |
| **3010** | Contains Mention | Delete messages that contain one or more [@mentions](https://support.discord.com/hc/en-us/articles/211870018-How-do-I-mention-tag-notify-another-user) (users, roles, or channels). Useful for removing notification-heavy messages. |
| **3011** | Contains No Mention | Delete messages that do NOT contain any mentions. Preserves messages with mentions while cleaning up general chat. |
| **3020** | Contains Link | Delete messages that contain one or more URLs or hyperlinks. Useful for removing spam, promotional content, or external references. |
| **3021** | Contains No Link | Delete messages that do NOT contain any URLs. Good for preserving reference links while cleaning up chat. |
| **3040** | Contains Sticker | Delete messages that contain [stickers](https://support.discord.com/hc/en-us/articles/360056233374-Stickers-FAQ). Helps clean up sticker-based communication. |
| **3041** | Contains No Sticker | Delete messages without [stickers](https://support.discord.com/hc/en-us/articles/360056233374-Stickers-FAQ). Preserves sticker messages while removing text content. |
| **3050** | Has Forwarded Message | Delete messages that contain [forwarded messages](https://support.discord.com/hc/en-us/articles/24640649961367-Message-Forwarding). Useful for removing shared content from other conversations. |
| **3051** | Has No Forwarded Message | Delete messages that do NOT contain [forwarded messages](https://support.discord.com/hc/en-us/articles/24640649961367-Message-Forwarding). Preserves forwarded content while removing original messages. |




## Using Filters Effectively

### Tips for Filter Configuration:

1. **Start Simple**: Begin with just one or two filters and test the behavior before adding more complexity.

2. **Combine Wisely**: Use [Filter Behavior](filter-behavior.md) to control whether messages need to match ALL filters (strict) or just ONE filter (flexible).

3. **Test First**: Create a test channel to verify your filter combination works as expected before applying to production channels.

4. **Common Combinations**:
   - **Bot cleanup**: Filter 1050 (Sent by Bot) + Filter 2001 (Has No Attachment) = Remove bot text commands while keeping bot media
   - **Protect important content**: Filter 1001 (Is Not Pinned) = Delete regular messages while protecting pinned content
   - **Media-only cleanup**: Filter 2000 (Has Attachment) = Delete only messages with files
   - **Bot spam removal**: Filter 3020 (Contains Link) + Filter 1050 (Sent by Bot) = Remove bot messages with links

5. **Role-Based Filtering**: Combine filters with [Roles](roles.md) to target or ignore specific user groups.

See also: [Filter Behavior](filter-behavior.md) to learn how to control filter matching logic.
