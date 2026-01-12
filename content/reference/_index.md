---
linkTitle: "Reference"
title: "💬 Reference"
weight: 40
---

This reference section provides detailed explanations for common concepts, terminology, and features used within EazyAutodelete. Use these documents to deepen your understanding of how the bot works and how to use advanced features effectively.

## Reference Documentation

* **[👑 User Permissions](/reference/user-permissions)** - Understanding permission levels and who can use which commands in your server

* **[🤖 Bot Permissions](/reference/bot-permissions)** - Overview of the permissions EazyAutodelete needs to function properly in your server

* **[🔤 Languages](/reference/languages)** - Information about supported languages and localization options

* **[🔙 Load old Messages](/reference/load-old-messages)** - Detailed explanation of how the bot handles historical messages and what "loading old messages" means

## Quick Reference Guide

### Key Concepts

**Configs**: Deletion rule sets that apply to specific channels. Each config defines how and when messages are deleted.

**Modes**: Different deletion algorithms (time-based individual, interval-based bulk, count-based, etc.)

**Filters**: Criteria that determine which messages should be deleted (emojis, links, attachments, etc.)

**Limit**: The time duration or message count that triggers deletion, depending on the mode

**Permission Levels**: Three tiers of access - All Users, Server Moderators, and Server Administrators

### Discord API Limitations

**2-Week Deletion Window**: Discord only allows bulk deletion of messages sent in the past 14 days (13.9583 days to be exact). Messages older than this must be deleted individually and very slowly, so the bot doesn't process them.

**Rate Limits**: Discord limits how fast bots can delete messages to prevent abuse. This means deletion may not be instantaneous, especially in high-traffic channels.

**Permission Requirements**: The bot needs View Channel, Read Message History, and Manage Messages permissions to function properly.

---

## Additional Resources

For more detailed configuration guides, see:
- [Configuration Overview](/config/) - Complete guide to all config options
- [Getting Started](/getting-started) - Step-by-step setup instructions
- [Troubleshooting](/troubleshooting) - Common issues and solutions

Need help? Join our [Support Server](https://eazyautodelete.xyz/discord/) for assistance!