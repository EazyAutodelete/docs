---
title: troubleshooting
description: 
published: true
date: 2025-11-02T19:50:45.178Z
tags: 
editor: markdown
dateCreated: 2025-11-02T19:50:31.688Z
---

# 🤬 Troubleshooting

Experiencing issues with EazyAutodelete? This guide covers the most common problems and their solutions. Most issues can be resolved by checking permissions, verifying your config settings, or using the `/debug` command.

## Quick Issue Identifier

> **ℹ️ Common Issue: Configs Keep Resetting to Mode 0?**
> 
> If your configs automatically change back to Mode 0 (disabled), this means the bot has detected an error in your channel configuration. This is a safety feature to prevent incorrect operation. Follow all the steps below to identify and fix the issue.

---

## Step 1: Check Bot Permissions

**The bot MUST have these 3 permissions in your channel:**

### Required Permissions:

1. **View Channel** - Bot needs to see the channel exists
2. **Read Message History** - Bot needs to read past messages for deletion
3. **Manage Messages** - Bot needs this permission to actually delete messages

**All three permissions are mandatory.** Missing even one will cause the bot to malfunction.

### How to Check Permissions:

1. Right-click on your channel
2. Select "Edit Channel"
3. Go to "Permissions" tab
4. Find "EazyAutodelete" in the roles/members list
5. Verify all three permissions are enabled (green checkmark)

### Granting Permissions:

If permissions are missing:
- Grant them to the @EazyAutodelete role server-wide, OR
- Add a permission override specifically for EazyAutodelete in your channel

**Still having issues?** Verify that no other role or permission override is denying these permissions to the bot.

---

## Step 2: Verify Your Configuration

Configuration errors are the most common cause of unexpected behavior. Use this checklist to verify each aspect of your config:

### Configuration Checklist

Run `/setup` and review each setting:

- [ ] **Mode** - Is the correct mode selected for your use case?
  - Mode 0 = Disabled (no deletion)
  - Mode 1 = Delete each message after time
  - Mode 2 = Delete all messages at intervals
  - Mode 3 = Delete messages after message count
  
- [ ] **Filters** - Are the filters configured correctly?
  - Review each active filter
  - Ensure filters match the messages you want to delete
  - Check if you're using the right Filter Behavior (match ALL vs match ONE)
  
- [ ] **Filter Behavior** - Match ALL or match ONE?
  - "Match ONE" = Delete if message matches any filter (OR logic)
  - "Match ALL" = Delete only if message matches all filters (AND logic)
  
- [ ] **Limit** - Is the limit value appropriate?
  - Mode 1 & 2: Time duration (10 seconds to 7 days)
  - Mode 3: Message count (3 to 75)
  - Verify format for time: `30s`, `5min`, `2hrs`, `1day`
  
- [ ] **Load Old Messages** - Is this set correctly?
  - "Yes" = Process historical messages (up to 2 weeks)
  - "No" = Only process new messages
  
- [ ] **Roles** - Are role filters working as intended?
  - Target roles = Only delete from these roles
  - Ignore roles = Don't delete from these roles
  - Verify the correct roles are selected

- [ ] **Time Boundaries** - Check "delete messages after" setting
  - Is there an unintended message ID restricting deletion?
  - Set to `0` to disable time boundaries

### Common Configuration Mistakes:

1. **Wrong mode for the use case**: Using Mode 2 when you need Mode 1
2. **Conflicting filters**: Having opposite filters (e.g., "Contains Emoji" + "Match ALL" + "No Emoji")
3. **Role misconfiguration**: Accidentally ignoring everyone or targeting no one
4. **Incorrect limit format**: Using wrong time format or out-of-range values
5. **Forgetting the 60-second delay**: Changes take 1 minute to apply

**Need help understanding a setting?** Check our detailed documentation:
- [Modes Documentation](config/mode.md)
- [Filters Documentation](config/filters.md)
- [Limit Documentation](config/limit.md)
- [Roles Documentation](config/roles.md)

---

## Step 3: Use the `/debug` Command

The `/debug` command is your best troubleshooting tool. It provides crucial information about your channel's status and configuration.

### What `/debug` Shows:

- **Channel ID** and **Server ID** - Useful when contacting support
- **Active configs** - All configs in the channel and their current state
- **Bot status** - What the bot is currently doing
- **Loading status** - Whether old messages are being loaded
- **Error messages** - Any detected problems with permissions or configuration
- **Processing queue** - How many messages are waiting to be processed

### How to Use `/debug`:

1. Run `/debug` in the channel you're troubleshooting
2. Review all displayed information carefully
3. Look for status messages like:
   - "Waiting to be loaded" - Old messages are still being fetched
   - "Permission error" - Bot is missing required permissions
   - "Mode 0" - Config is disabled (check why)
   - "Processing X messages" - Bot is actively working

### Common `/debug` Indicators:

- **"Waiting to be loaded"**: Normal for Mode 3 or when loading old messages. Be patient.
- **"Mode 0 - Disabled"**: Something went wrong. Check permissions and config.
- **"No configs found"**: You haven't created a config yet. Use `/setup`.
- **"Permission denied"**: Missing one of the three required permissions.

---

## Advanced Troubleshooting

### Bot Not Deleting Anything

**Possible causes:**
1. Mode is set to 0 (disabled)
2. Filters are too restrictive (no messages match)
3. All users have ignore roles assigned
4. Time boundary excludes all messages
5. Waiting for 60-second activation delay
6. Still loading old messages (check `/debug`)

**Solution:** Review configuration checklist above and verify filters aren't too restrictive.

### Bot Deleting Wrong Messages

**Possible causes:**
1. Filter Behavior set incorrectly (ALL vs ONE)
2. Wrong filters selected
3. Role configuration targeting wrong users
4. Multiple overlapping configs in the same channel

**Solution:** Use `/setup` to review filters and Filter Behavior setting. Consider testing in a test channel first.

### Bot Deleting Too Slowly

**Possible causes:**
1. Discord API rate limits (normal behavior)
2. High server load
3. Multiple Mode 3 configs in one channel
4. Very active channel with many messages
5. Still loading historical messages

**Solution:** This is often normal behavior due to Discord's rate limits. Mode 1 is typically faster than Mode 2 or 3.

### Bot Deleted Pinned Messages

**Possible causes:**
1. Filter "Is pinned" is selected instead of "Is not pinned"
2. Message was unpinned before deletion timer expired

**Solution:** Always use Filter 8 "Is not pinned" to protect pinned messages.

---

## Still Need Help?

If you've tried all the above steps and still can't resolve your issue:

### Contact Support

Visit our **[Support Server](https://eazyautodelete.xyz/discord/)** for personalized assistance.

**Before asking for help, please:**
1. Run `/debug` in the affected channel
2. Take a screenshot of your config (use `/setup`)
3. Note your Channel ID and Server ID (from `/debug`)
4. Describe what you expected vs what actually happened
5. Mention any error messages you've seen

Our support team and community members are ready to help you get EazyAutodelete working perfectly!

### Common Questions in Support

- "Why is my config in Mode 0?" → Check permissions
- "Messages aren't being deleted" → Verify filters and limit settings
- "How do I protect pinned messages?" → Use Filter 8 "Is not pinned"
- "Can I delete messages older than 2 weeks?" → No, Discord API limitation
- "Why is there a 60-second delay?" → Prevents constant bot restarts during configuration

---

## Helpful Resources

- [Getting Started Guide](getting-started.md) - Complete setup walkthrough
- [Configuration Documentation](config/) - Detailed config explanations
- [User Permissions](reference/user-permissions.md) - Who can use which commands
- [Support Server](https://eazyautodelete.xyz/discord/) - Get real-time help

