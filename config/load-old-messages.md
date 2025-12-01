---
title: Load old Messages
description: Details about the options to load old messages after editing a Config
published: true
date: 2025-11-29T17:39:14.561Z
tags: 
editor: markdown
dateCreated: 2025-11-02T19:53:08.240Z
---

# 📡 Load old messages

After creating or modifying a config, EazyAutodelete will ask you whether to load (and potentially delete) messages that were sent before the config was created or last modified. This is an important decision that affects how the bot processes your channel's message history.

## Understanding the Options

### Yes, load old messages

**The bot will process historical messages** sent before the config was created.

**What happens:**
- The bot starts loading messages that were sent before your config was created or last modified
- These historical messages will be evaluated against your filters and deletion rules
- Due to Discord's API limitations, the bot can only load and delete messages from the **past 13.9583 days** (approximately 2 weeks)
- Messages older than 2 weeks cannot be bulk-deleted by Discord's API and will not be processed

**Best for:**
- Cleaning up existing message backlogs
- Applying new rules to recent conversation history  
- Starting fresh with a clean channel
- Retroactively enforcing new content policies

**Important notes:**
- Loading old messages may take time depending on channel activity
- The bot will show progress in the `/debug` command
- Messages older than 2 weeks cannot be deleted due to Discord limitations

---

### No, don't load old messages

**The bot will only process new messages** sent after the current timestamp.

**What happens:**
- The bot saves the current timestamp in your configuration
- Only messages sent after this moment will be considered for deletion
- All existing messages in the channel are permanently ignored by this config
- This setting can be edited anytime using the [Delete messages after](delete-messages-after.md) feature

**Best for:**
- Preserving existing conversation history
- Starting deletion from a clean slate going forward
- Testing new configs without affecting old messages
- Channels with important historical context

**Important notes:**
- This is the safer option if you're unsure
- Existing messages remain untouched regardless of your filters
- You can always change this later if needed

---

## Impact on Multiple Configs

When you choose to **not load old messages** for one config in a channel, this decision may affect other configs in the same channel. The bot optimizes message loading across all configs to avoid redundant API calls.

> **ℹ️ Info:** If one config is set to not load old messages, the bot may stop loading historical messages for the entire channel, even if other configs are set to load them. This is done to prevent conflicts and ensure consistent behavior.

## Recommendations

1. **New channels**: Choose "Yes" to start with a clean slate
2. **Active channels**: Choose "No" to preserve existing discussions
3. **Testing**: Always choose "No" when testing new configs
4. **Cleanup mode**: Choose "Yes" if you're trying to clean up spam or unwanted content
5. **When uncertain**: Choose "No" - you can always manually clean up old messages separately

## Related Settings

- [Delete messages after](delete-messages-after.md) - Set a specific message as the starting point for deletion
- [Modes](mode.md) - Different modes may behave differently with old messages
- Mode 3 specifically requires old messages to be loaded for accurate counting
