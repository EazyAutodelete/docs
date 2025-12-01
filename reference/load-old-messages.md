---
title: Load Old Messages
description: Details about loading old messages
published: true
date: 2025-11-29T17:00:14.956Z
tags: 
editor: markdown
dateCreated: 2025-11-02T19:54:18.381Z
---

# 🔙 Load old Messages

"Loading old messages" is a critical concept in EazyAutodelete that determines how the bot handles messages that existed before a config was created or modified. Understanding this feature is essential for using the bot effectively.

## What Does "Load Old Messages" Mean?

When you create or modify a deletion config, EazyAutodelete needs to decide whether to process messages that were sent **before** that moment. This decision is called "loading old messages."

### Two Approaches:

**Load old messages (Yes):**
- The bot retrieves historical messages from Discord's servers
- These messages are evaluated against your deletion rules
- Matching messages will be deleted according to your config
- Limited to messages sent in the past ~14 days (Discord API restriction)

**Don't load old messages (No):**
- The bot only processes messages sent **after** the config change
- All existing messages are ignored permanently by this config
- Safer option when testing or unsure about settings
- Can be changed later via time boundary settings

---

## Technical Details

### How Loading Works

1. **User modifies config** → Bot records the current timestamp
2. **User chooses "Load old messages"**
3. **Bot starts background process** to fetch historical messages
4. **Messages are retrieved** in batches (Discord API limitation)
5. **Each message is evaluated** against filters and rules
6. **Matching messages are queued** for deletion
7. **Deletion occurs** according to mode and limit settings

### The 14-Day Limitation

**Discord API Restriction:** Discord only allows bulk deletion of messages sent in the past 14 days (technically 13.9583 days or approximately 13 days, 23 hours).

**Why this limit exists:**
- Prevents abuse and spam
- Protects long-term conversation history
- Technical limitations of Discord's infrastructure

**What this means for you:**
- Messages older than 2 weeks cannot be bulk-deleted
- They must be deleted individually (very slow, rate-limited)
- EazyAutodelete doesn't process messages older than 14 days when loading

**Workaround:** If you need to clean messages older than 2 weeks, you'll need to:
- Use Discord's built-in message search and delete manually
- Use a specialized bulk delete tool (at your own risk)
- Accept that older messages will remain

---

## When to Load Old Messages

### Choose "Yes" When:

✅ **Starting fresh in a channel**
- You want to clear existing messages and start with auto-deletion
- Channel is being repurposed

✅ **Cleaning up spam or unwanted content**
- Recent spam needs to be removed
- Content policy changed and you need to enforce it retroactively

✅ **Implementing new rules**
- New server guidelines require cleanup
- Channel purpose changed

✅ **Testing in a test channel**
- You want to see how the bot handles existing content
- Testing with real message examples

✅ **Channel reset**
- Regular cleanup of accumulated messages
- Seasonal or event-based channel reset

### Choose "No" When:

❌ **Preserving history**
- Important conversations shouldn't be deleted
- Archive channel with valuable content

❌ **Testing in production**
- Not sure about settings yet
- Want to see how it works on new messages first

❌ **Gradual implementation**
- Want to phase in auto-deletion slowly
- Applying rules only to future content

❌ **When uncertain**
- Not sure if config is correct
- Better to be safe and test on new messages

❌ **Active important discussions**
- Ongoing conversations you want to keep
- Recent important announcements

---

## Impact on Different Modes

### Mode 1 - Individual Time-Based Deletion

**With load old messages:**
- Historical messages are checked against filters
- Messages older than the limit are deleted immediately
- Messages within the limit wait until their time expires

**Example:** If limit is 30 minutes and you load old messages, messages older than 30 minutes get deleted right away.

### Mode 2 - Interval-Based Bulk Deletion

**With load old messages:**
- All historical matching messages are loaded
- First interval cleanup includes old messages
- Subsequent cleanups only affect new messages

**Example:** If interval is 5 minutes, old messages get deleted in the first cycle.

### Mode 3 - Count-Based Deletion

**With load old messages:**
- Loading is **required** for accurate counting
- Bot must know total message count
- `/debug` shows "Waiting to be loaded" until complete
- Deletion doesn't start until loading finishes

**Example:** If limit is 50 messages, bot must load existing messages to know when count reaches 50.

> **ℹ️ Important:** Mode 3 MUST load old messages to function properly. You'll see "Waiting to be loaded" status until this completes.

---

## Loading Process & Status

### Monitoring Load Progress

Use the `/debug` command to check loading status:

**Possible statuses:**
- **"Loading old messages"** - Process is ongoing
- **"Waiting to be loaded"** - Queued but not started yet (Mode 3)
- **"Ready"** or **"Active"** - Loading complete, processing messages
- **"Error"** - Problem occurred (check permissions)

### How Long Does Loading Take?

Loading duration depends on:
- **Channel message count** - More messages = longer load time
- **Server activity** - High-traffic servers may be slower
- **Discord API rate limits** - Bot must respect Discord's limits
- **Bot server load** - High overall usage can cause delays

**Typical times:**
- Low activity channel (100-500 messages): 10-30 seconds
- Medium activity channel (500-2000 messages): 30-90 seconds
- High activity channel (2000+ messages): 2-5 minutes
- Very active channel (5000+ messages): 5-15 minutes

**Be patient!** The process runs in the background and doesn't interfere with normal channel use.

---

## Changing Your Decision

### Decided to Load After Choosing "No"?

You can retroactively load old messages:

1. Open `/setup` for the config
2. Modify the "delete messages after" setting
3. Set it to a message ID or clear it
4. The bot will start loading from that point

### Decided Not to Load After Choosing "Yes"?

Once the loading process starts, you can't stop it. However:

1. Set config to Mode 0 (disabled) to pause deletion
2. Wait for loading to complete
3. Reconfigure or delete the config as needed

---

## Best Practices

### Before Choosing:

1. **Review your config** - Make sure filters, mode, and limit are correct
2. **Test in test channel** - Create identical config in a test channel first
3. **Backup important content** - Screenshot or archive critical messages
4. **Check permissions** - Verify bot has required permissions
5. **Communicate with users** - Let them know cleanup is happening

### After Loading:

1. **Monitor with `/debug`** - Check progress and status
2. **Watch for errors** - Mode 0 activation indicates problems
3. **Verify results** - Ensure correct messages are being deleted
4. **Adjust if needed** - Modify config if behavior isn't as expected

### General Guidelines:

- **When in doubt, choose "No"** - Safer option
- **Test first** - Always test new configs on new messages
- **Communicate changes** - Tell your users what to expect
- **Document decisions** - Keep notes on why you chose each option
- **Regular reviews** - Periodically check if settings still make sense

---

## Common Questions

**Q: Can I load messages older than 2 weeks?**
A: No, Discord's API limitation prevents bulk deletion of older messages.

**Q: Will loading old messages slow down my server?**
A: No, loading happens in the background and doesn't affect server performance.

**Q: Can I cancel loading once it starts?**
A: You can disable the config (Mode 0) to stop deletion, but loading will complete.

**Q: Do I need to load old messages for Mode 3?**
A: Yes, Mode 3 requires loading to accurately count messages.

**Q: What happens if I have multiple configs in one channel?**
A: Each config's load decision is independent, but they share the loading process for efficiency.

**Q: Will pinned messages be deleted if I load old messages?**
A: Only if your filters don't include "Is not pinned" (Filter 8). Always use Filter 8 to protect pins.

---

## Related Documentation

- [Delete Messages After](../config/delete-messages-after.md) - Set temporal boundaries
- [Modes](../config/mode.md) - How loading interacts with different modes
- [Filters](../config/filters.md) - Control which loaded messages are deleted
- [Getting Started](../getting-started.md) - Initial setup guide

Need help with loading old messages? Join our [Support Server](https://eazyautodelete.xyz/discord/)!