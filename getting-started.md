---
title: Getting Started
description: A quick guide on how to get started with EazyAutodelete.
published: true
date: 2025-11-29T18:04:36.469Z
tags: 
editor: markdown
dateCreated: 2025-11-02T19:49:19.302Z
---

# 🚀 Getting Started

Welcome to EazyAutodelete! This guide will walk you through the process of setting up automatic message deletion in your Discord server. Whether you want to keep channels clean, manage temporary content, or enforce content policies, EazyAutodelete makes it easy.

## Step 1: Inviting the Bot

Adding EazyAutodelete to your Discord server is quick and straightforward.

**Follow our detailed guide:**

📖 **[Add to Server Guide](add-to-server.md)** - Step-by-step instructions for inviting and authorizing the bot

**Quick summary:**
1. Visit [eazyautodelete.xyz/invite](https://eazyautodelete.xyz/invite)
2. Select your server from the dropdown
3. Keep all requested permissions (required for proper functionality)
4. Click "Authorize"

The bot will join your server and be ready to configure!

---

## Step 2: Understanding Configs

EazyAutodelete uses **configs** to define deletion rules. Understanding how configs work is key to using the bot effectively:

### What is a Config?

A config is a set of deletion rules that applies to **a specific channel**. Each config includes:
- A deletion mode (how messages are deleted)
- A limit (when to delete)
- Filters (which messages to delete)
- Optional settings (roles, time boundaries, etc.)

### Key Facts About Configs:

- **Channel-specific**: Each config only affects the channel where it was created
- **Multiple configs**: You can create up to **3 configs per channel** (more with [Premium](https://eazyautodelete.xyz/premium))
- **Independent operation**: Different channels can have completely different deletion rules
- **Flexible combinations**: Multiple configs in one channel can work together to create complex deletion rules

---

## Step 3: Creating Your First Config

Now let's create a config to start automatically deleting messages!

### Using the `/setup` Command

1. **Run** `/setup` in the channel where you want auto-deletion
2. **Select** "Create Config" from the menu

### Configure Deletion Mode

**Choose from 5 different modes:**

- **Mode 1 - Time-based individual deletion**: Delete each message X seconds/minutes/hours after it's sent
  - *Example*: Delete every message 30 seconds after posting
  - *Best for*: Creating self-destructing temporary chat channels

- **Mode 2 - Interval-based bulk deletion**: Delete all messages at regular intervals
  - *Example*: Delete all messages every 5 minutes
  - *Best for*: Regular cleanup sweeps of active channels

- **Mode 3 - Message count-based bulk deletion**: Delete all messages after X messages are sent
  - *Example*: Delete all messages once 50 messages have been posted
  - *Best for*: Maintaining a specific message history length

- **Mode 4 - Message count-based single deletion**: Keep newest X messages and delete oldest one
	- *Example*: Keep the newest 10 messages and delete the oldest one when a new one is created
	- *Best for*: Limit a channel to only the essentials and keep it compact
  
- **Mode 5 - Daily Time-based bulk deletion**: Delete all messages daily at HH:mm.
 	- *Example*: Delete all messages at 10:00 UTC.
  - *Best for*: Clean up yesterday's mess and have a fresh start for a new day

**Learn more:** [Modes Documentation](config/mode.md)

### Select Filters

**Filters let you target specific message types for deletion:**

Choose as many filters as you need to match your use case:

- Is/isn't pinned
- Is/isn't from bots
- Is/isn't a reply
- Contains/doesn't contain emojis
- Contains/doesn't contain links
- Has/doesn't have attachments
- And many more!

**Examples:**
- Delete only bot messages: Select "Author is Bot"
- Delete only messages with links: Select "Contains Link(s)"
- Delete everything except pinned: Select "Is not pinned"

**Learn more:** [Filters Documentation](config/filters.md)

### Set Additional Options

**Enhance your config with optional settings:**

- **Filter Behavior**: Require messages to match ALL filters or just ONE
- **Roles**: Target or ignore messages from specific roles
- **Time boundaries**: Only delete messages after a certain point
- **Thread settings**: Control how threads are handled

### Set the Limit

**The limit determines when deletion happens:**

Examples: `30s`, `5min`, `2hrs`, `1day 6hr`

**Learn more:** [Limit Documentation](config/limit.md)

### Load Old Messages

**Final decision: What about existing messages?**

- **Yes**: Process and delete messages sent before now (up to 2 weeks old)
- **No**: Only delete new messages sent after now

**When to choose Yes:**
- You want to clean up existing message history
- Starting fresh in a channel
- Applying new rules retroactively

**When to choose No:**
- You want to preserve existing conversation
- Testing a new config safely
- Unsure about the settings

**Learn more:** [Load Old Messages Documentation](config/load-old-messages.md)

---

## Step 4: Activation

After completing the setup:

1. **Wait 60 seconds**: The bot waits one minute after your last config change before starting
2. **Automatic operation**: EazyAutodelete will begin processing messages according to your rules
3. **Make adjustments**: Run `/setup` again anytime to modify your config

> **ℹ️ Info:** The 60-second delay prevents the bot from constantly starting and stopping while you make multiple configuration changes.

---

## Next Steps

### Explore Advanced Configuration

For more control over message deletion, explore these advanced features:

- **[Configuration Guide](config/)** - Deep dive into all configuration options
- **[Share & Copy Configs](share-and-copy-configs.md)** - Reuse configs across channels and servers
- **[Server Settings](server-settings/)** - Configure bot permissions and roles
- **[User Permissions](reference/user-permissions.md)** - Understand who can use which commands

### Need Help?

- **[Troubleshooting Guide](troubleshooting.md)** - Common issues and solutions
- **[Support Server](https://eazyautodelete.xyz/discord/)** - Get help from our community
- **[Premium Features](premium.md)** - Unlock advanced capabilities

### Useful Commands

- `/setup` - Create or modify configs
- `/debug` - Check config status and bot information
- `/help` - View all available commands
- `/autodelete` - Quick config management

---

## Tips for Success

1. **Start simple**: Begin with basic configs and add complexity as needed
2. **Test in a test channel**: Always test new configurations before using in production
3. **Use `/debug`**: Check this command to understand what the bot is doing
4. **Read the docs**: Each setting has detailed documentation - use it!
5. **Join support**: Our support server has many experienced users who can help

Happy auto-deleting! 🎉
