---
title: filters
description: The filters allow you to set exactly which messages are deleted.
published: true
date: 2025-11-02T19:52:41.949Z
tags: 
editor: markdown
dateCreated: 2025-11-02T19:52:27.380Z
---

# 🔎 Filters

Filters give you precise control over which messages EazyAutodelete will target for deletion. You can select from a variety of filters to match exactly the type of content you want to remove from your channels.

Filters work with all [Modes](mode.md) and can be combined to create sophisticated deletion rules. Use [Filter Behavior](filter-behavior.md) to control whether messages must match ALL filters or just ONE filter.

## Available Filters

The following table lists all available message filters. Each filter has a unique ID and is designed to target specific message characteristics:

| Filter ID | Filter Name | Explanation |
| --------- | ----------- | ----------- |
| **1** | Contains Emoji(s) | Delete the message **only if** it contains one or more emojis (custom or Unicode emojis). |
| **2** | Does not contain Emoji(s) | Delete the message **only if** it does NOT contain any emojis. Perfect for keeping emoji reactions visible while removing plain text. |
| **3** | Contains Link(s) | Delete the message **only if** it contains one or more URLs or hyperlinks. Useful for removing spam or promotional content. |
| **4** | Does not contain Link(s) | Delete the message **only if** it does NOT contain any URLs. Good for preserving reference links while cleaning up chat. |
| **5** | Has Attachment(s) | Delete the message **only if** it has one or more file attachments (images, videos, documents, etc.). |
| **6** | Does not have Attachment(s) | Delete the message **only if** it has NO attachments. Useful for keeping media while removing text-only messages. |
| **7** | Is pinned | Delete the message **only if** it is currently pinned in the channel. Note: This requires special permissions. |
| **8** | Is not pinned | Delete the message **only if** it is NOT pinned. This is the most common setting as you typically want to preserve pinned messages. |
| **11** | Author is Bot | Delete the message **only if** the author is a bot account. Great for cleaning up bot command responses or automated messages. |
| **12** | Author is not Bot | Delete the message **only if** the author is a human user (not a bot). Useful when you want to keep bot messages but remove user chat. |
| **13** | Has a Thread | Delete the message **only if** a thread was started from this message. Useful for cleaning up messages that have spawned discussions. |
| **14** | Does not have a Thread | Delete the message **only if** NO thread was started from it. Helps preserve messages that have generated discussion threads. |
| **15** | Was published | Delete the message **only if** it was published to subscribed channels via [Channel Following](https://support.discord.com/hc/en-us/articles/360032008192-Announcement-Channels-). Only available in Announcement channels. |
| **16** | Was not published | Delete the message **only if** it was NOT published to subscribed channels. Only available in Announcement channels. |
| **17** | Is Crosspost | Delete the message **only if** it is a [published message from another server](https://support.discord.com/hc/en-us/articles/360028384531-Channel-Following-FAQ) (received via Channel Following). |
| **18** | Is not Crosspost | Delete the message **only if** it is NOT a crosspost from another server. Use this to keep your original content while removing followed content. |
| **19** | Is a Reply | Delete the message **only if** it is a [Reply](https://support.discord.com/hc/en-us/articles/360057382374-Replies-FAQ) to another message. Useful for cleaning up reply chains. |
| **20** | Is not a Reply | Delete the message **only if** it is NOT a reply. Helps preserve conversation threads while removing standalone messages. |

## Using Filters Effectively

### Tips for Filter Configuration:

1. **Start Simple**: Begin with just one or two filters and test the behavior before adding more complexity.

2. **Combine Wisely**: Use [Filter Behavior](filter-behavior.md) to control whether messages need to match ALL filters (strict) or just ONE filter (flexible).

3. **Test First**: Create a test channel to verify your filter combination works as expected before applying to production channels.

4. **Common Combinations**:
   - **Bot cleanup**: Filter 11 (Author is Bot) + Filter 6 (Does not have Attachments) = Remove bot text commands
   - **Keep important content**: Filter 8 (Is not pinned) = Protect pinned messages from deletion
   - **Media preservation**: Filter 5 (Has Attachments) = Delete only messages with files
   - **Spam prevention**: Filter 3 (Contains Links) + Filter 11 (Author is Bot) = Remove bot spam with links

4. **Role-Based Filtering**: Combine filters with [Roles](roles.md) to target or ignore specific user groups.

See also: [Filter Behavior](filter-behavior.md) to learn how to control filter matching logic.
