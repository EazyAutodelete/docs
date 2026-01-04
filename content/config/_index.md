---
title: "Config"
weight: 30
# bookFlatSection: false
# bookToc: true
# bookHidden: false
# bookCollapseSection: false
# bookComments: false
# bookSearchExclude: false
# bookHref: ''
# bookIcon: ''
---


# 🚮 Message Delete Configuration

EazyAutodelete provides powerful and flexible configuration options that allow you to customize the deletion algorithm precisely to your needs. Whether you want simple time-based deletion or complex multi-filter rules, you have complete control over how messages are handled in your channels.

## Configuration Options

Below you'll find all available configuration settings for customizing message deletion:

### Core Settings

* **[⚙️ Modes](mode)** - Choose how the deletion algorithm works (delete messages after time, delete all at intervals, etc.)
* **[⌛ Limit](limit)** - Set the time duration or message count that triggers deletion
* **[🔎 Filters](filters)** - Select which types of messages to delete (with emojis, with links, bot messages, etc.)
* **[🔂 Filter Behavior](filter-behavior)** - Control whether messages must match ALL filters or just ONE filter

### Time-Based Filtering

* **[⏪ Delete messages before](delete-messages-before)** - Only delete messages sent before a specific message (deprecated)
* **[⏩ Delete messages after](delete-messages-after)** - Only delete messages sent after a specific message

### Role-Based Configuration

* **[👥 Roles](roles)** - Target or ignore messages from users with specific roles

### Message Loading

* **[📡 Load old messages](load-old-messages)** - Choose whether to delete messages sent before the config was created

> **ℹ️ Info:** The bot will wait one minute after your last change to a config before starting to apply any changes. This buffer period ensures that you can make multiple adjustments without the bot starting and stopping repeatedly.

---

## Getting Started with a Configuration

1. Use `/setup` command to create or modify a config
2. Choose your desired mode based on your deletion needs
3. Add filters to specify which messages should be deleted
4. Set a limit appropriate for your chosen mode
5. Configure any additional settings like roles or time filters
6. Wait one minute for the bot to start processing

For a step-by-step guide on setting up your first config, see [Getting Started](/getting-started).

### Essential Settings

These are the fundamental settings every config must have:

#### **[⚙️ Modes](/config/mode)**
Determines HOW the deletion algorithm works:
- **Mode 0**: Disabled (no deletion)
- **Mode 1**: Delete each message after X time individually
- **Mode 2**: Delete all messages every X time (interval)
- **Mode 3**: Delete all messages after X message count
- **Mode 4**: Limit the amount of messages in a channel. Keep the newest X messages and delete oldest when a new one is created.
- **Mode 5**: Delete all messages daily at HH:mm.

#### **[⌛ Limit](/config/limit)**
Sets the time or count that triggers deletion:
- For Modes 1 & 2: Time duration (10 seconds to 7 days)
- For Mode 3: Message count (3 to 75 messages)

**Format examples:**
- `30s` = 30 seconds
- `5min` = 5 minutes
- `2hrs 30min` = 2 hours and 30 minutes
- `50` = 50 messages (Mode 3 only)

---

## Message Filtering

Control exactly which messages are targeted for deletion:

### **[🔎 Filters](/config/filters)**
Select from 20+ different message characteristics:
- Content type (emojis, links, attachments)
- Author type (bot vs human)
- Message status (pinned, has thread, is reply)
- Announcement features (published, crosspost)
- And more!

**Examples:**
- Only delete bot messages
- Only delete messages with attachments
- Only delete unpinned messages (protect pins)
- Only delete messages without links

### **[🔂 Filter Behavior](/config/filter-behavior)**
Control how multiple filters work together:
- **Match ONE** (OR logic): Delete if message matches ANY filter
- **Match ALL** (AND logic): Delete only if message matches ALL filters

**Example:**
- Filters: "Contains Links" + "Author is Bot"
- Match ONE: Deletes messages with links OR from bots
- Match ALL: Deletes only messages with links AND from bots

---

## Advanced Options

Fine-tune your configuration with these optional settings:

### Role-Based Filtering

**[👥 Roles](/config/roles)** - Control whose messages are affected:
- **Target roles**: Only delete from users with these roles
- **Ignore roles**: Never delete from users with these roles
- Up to 10 roles (20 with Premium)

**Use cases:**
- Protect moderator messages
- Target temporary member roles
- Exclude VIP/supporter roles
- Create staff-only channels

### Time Boundaries

Control which messages in the timeline are processed:

**[⏩ Delete messages after](/config/delete-messages-after)** - Only delete messages sent after a specific message ID
- Preserves older conversation history
- Creates a temporal starting point
- Useful for phased rollout

**[⏪ Delete messages before](/config/delete-messages-before)** - ⚠️ Deprecated feature
- No longer available
- Historical reference only

### Message Loading

**[📡 Load old messages](/config/load-old-messages.md)** - Decide whether to process existing messages:
- **Yes**: Process messages from the past 2 weeks
- **No**: Only process new messages going forward
- Critical decision when creating/modifying configs

---

## Configuration Process

### Creating a Config

1. **Navigate to your channel** where you want auto-deletion
2. **Run `/setup`** command
3. **Select "Create Config"** from the menu
4. **Choose your mode** (1, 2, or 3)
5. **Select filters** (optional but recommended)
6. **Set filter behavior** (ALL or ONE)
7. **Configure roles** (optional)
8. **Set the limit** (time or count)
9. **Choose whether to load old messages**
10. **Wait 60 seconds** for activation

### Modifying a Config

1. **Run `/setup`** in the channel with the config
2. **Select the config** you want to modify
3. **Choose "Edit Config"**
4. **Modify any settings** as needed
5. **Confirm changes**
6. **Wait 60 seconds** for changes to take effect

### Deleting a Config

1. **Run `/setup`** in the channel
2. **Select the config** to delete
3. **Choose "Delete Config"**
4. **Confirm deletion**
5. **Config stops immediately**

---

## Multi-Config Strategies

### Why Use Multiple Configs?

You can have up to 3 configs per channel (more with Premium), allowing sophisticated deletion strategies:

**Example 1: Dual-Purpose Chat**
- Config 1: Mode 1, 1 hour, all messages → Regular chat cleanup
- Config 2: Mode 1, 5 minutes, filter "Author is Bot" → Fast bot command cleanup

**Example 2: Selective Preservation**
- Config 1: Mode 1, 30 minutes, all messages except pinned → General cleanup
- Config 2: Mode 2, 1 day, filter "Contains Links" + "Author is Bot" → Bot link cleanup

**Example 3: Role-Based Tiers**
- Config 1: Mode 1, 10 minutes, target "Trial Member" role → Quick cleanup for trials
- Config 2: Mode 1, 1 hour, ignore "Moderator" role → Preserve mod messages longer

### Best Practices for Multiple Configs

✅ **Do:**
- Use different modes for different purposes
- Combine filters strategically
- Test each config individually first
- Document your multi-config strategy
- Use `/debug` to monitor all configs

❌ **Don't:**
- Use multiple Mode 3 configs in one channel (causes conflicts)
- Create overlapping configs that fight each other
- Forget which config does what
- Make them too complex to understand

---

## Configuration Tips

### Getting Started

1. **Start simple**: Begin with one Mode 1 config and basic filters
2. **Test in test channel**: Always test new configs before production use
3. **Use common filters**: Start with "Is not pinned" to protect important messages
4. **Choose conservative limits**: Start with longer times, shorten if needed
5. **Don't load old messages initially**: Test on new messages first

### Common Configurations

**Temporary Chat Channel:**
```
Mode: 1 (Individual time-based)
Limit: 1hrs
Filters: Is not pinned
Load old: No
```

**Bot Command Cleanup:**
```
Mode: 1 (Individual time-based)
Limit: 30s
Filters: Author is Bot
Load old: Yes
```

**Announcement Channel:**
```
Mode: 2 (Interval-based bulk)
Limit: 7days
Filters: None (all messages)
Load old: No
```

**Media Channel:**
```
Mode: 3 (Count-based)
Limit: 50 messages
Filters: Has Attachment(s)
Load old: Yes
```

### Troubleshooting Configs

**Config not deleting anything?**
- Check Mode (is it set to 0?)
- Verify permissions (View, Read History, Manage Messages)
- Review filters (too restrictive?)
- Check `/debug` for errors
- Wait for 60-second activation delay

**Config deleting wrong messages?**
- Review Filter Behavior (ALL vs ONE)
- Check which filters are active
- Verify role configuration
- Test in test channel to confirm behavior

**Config keeps resetting to Mode 0?**
- Bot is detecting an error
- Check permissions in the channel
- Verify role configuration is valid
- Review `/debug` for error messages
- See [Troubleshooting Guide](troubleshooting.md)

---

## Related Documentation

### Configuration Details
- [Modes](/config/mode) - Detailed mode explanations
- [Limit](/config/limit) - Time and count specifications
- [Filters](/config/filters) - All available filters
- [Filter Behavior](/config/filter-behavior) - Filter logic
- [Roles](/config/roles) - Role-based filtering

### Setup Guides
- [Getting Started](/getting-started) - Complete setup walkthrough
- [Add to Server](/add-to-server) - Bot installation
- [Share & Copy Configs](/share-and-copy-configs) - Reuse configurations

### Support
- [Troubleshooting](/troubleshooting) - Common issues
- [Support Server](https://eazyautodelete.xyz/discord/) - Get help

---

## Quick Reference

| Setting | Purpose | Options/Range |
|---------|---------|---------------|
| **Mode** | Deletion algorithm | 0, 1, 2, 3 |
| **Limit** | When to delete | 10s - 7d OR 3-75 msgs |
| **Filters** | What to delete | 20+ options |
| **Filter Behavior** | Filter logic | ALL or ONE |
| **Roles** | Whose messages | 10-20 roles |
| **Time Boundary** | Message timeline | Message ID or 0 |
| **Load Old Messages** | Process history | Yes or No |

---

## Need Help?

Configuring EazyAutodelete to perfectly match your needs can take some experimentation. Don't hesitate to:

- Read the detailed documentation for each setting
- Test configurations in test channels
- Join our [Support Server](https://eazyautodelete.xyz/discord/) for assistance
- Check the [Troubleshooting Guide](/troubleshooting)
- Share your configs and learn from others

Happy configuring! 🎉