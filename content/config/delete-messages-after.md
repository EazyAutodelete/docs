---
title: "⏩ Delete Messages After"
weight: 50
---

The **"Delete messages after"** setting allows you to create a temporal boundary for your deletion config. Only messages sent **AFTER** a specific message will be considered for deletion by your config.

This is useful when you want to preserve older conversation history while applying auto-deletion rules to newer messages.

## How to Configure

1. Click the **"Delete messages after"** button in your config settings
2. Enter the **Message ID** of the boundary message
3. The bot will only delete messages that were sent after this message

All messages sent before (and including) the specified message will be completely ignored by this config.

## Finding Message IDs

To get a message ID, you need to enable Developer Mode in Discord:

**Learn how to find message IDs:**
- [Discord Support: Where can I find my User/Server/Message ID?](https://support.discord.com/hc/en-us/articles/206346498-Where-can-I-find-my-User-Server-Message-ID-)

**Quick steps:**
1. Enable Developer Mode in Discord Settings → Advanced → Developer Mode
2. Right-click on any message
3. Select "Copy Message ID"
4. Paste the ID into the bot's configuration

## Disabling This Setting

To disable the "delete messages after" filter and process all messages regardless of age:
- Enter `0` as the message ID
- This will remove the temporal boundary

## Use Cases

- **Preserve announcements**: Set the boundary after important announcements to keep them visible
- **Fresh starts**: Begin auto-deletion from a specific point in time without affecting history
- **Event-based cleanup**: Only delete messages after an event started
- **Gradual rollout**: Test deletion on new messages before applying to entire history
