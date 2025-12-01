---
title: Mode
description: How the deletion algorithm works
published: true
date: 2025-11-29T17:07:51.172Z
tags: 
editor: markdown
dateCreated: 2025-11-02T19:53:25.143Z
---

# ⚙️ Modes

EazyAutodelete currently supports 4 different deletion modes, each designed for specific use cases. You can create multiple configs with different modes in different channels, or even multiple configs with different modes in the same channel (up to 3 configs per channel, or more with [Premium](/premium)).

Each mode works with all available [Filters](filters.md). In each mode, all messages that do not meet the configured filters are completely ignored by the deletion algorithm.

> **⚠️ Warning:** To prevent unwanted behavior and ensure your config works as expected, you **must** set a new [Limit](limit.md) after changing the mode. Different modes interpret the limit value differently (as time or message count).

## Mode: 0 - Disabled

**Disable the deletion algorithm completely.** When set to Mode 0, the bot will not delete any messages in the channel. This is useful when you want to temporarily pause deletion without deleting your entire configuration.

> **ℹ️ Info:** If the bot encounters a problem with your channel or your configs (such as missing permissions), it will automatically change all configs to Mode 0 as a safety mechanism. This prevents the bot from operating incorrectly or causing unintended deletions. Check the `/debug` command to see why your configs were disabled.

## Mode: 1 - Time-Based Individual Deletion

**Delete each message individually after a configured amount of time has passed since it was sent.** This is the most commonly used mode and provides a "self-destructing messages" effect.

For example, if you set the limit to 30 seconds, each message will be deleted exactly 30 seconds after it was posted. This creates a rolling deletion effect where messages gradually disappear as they age.

**Use cases:**
- Create temporary chat channels where messages auto-delete after a set time
- Keep channels clean without permanently removing all conversation history at once
- Allow users to read recent messages while automatically cleaning up older ones

To change the time duration, see [Limit](limit.md).

## Mode: 2 - Interval-Based Bulk Deletion

**Delete all qualifying messages at regular time intervals.** The bot will wait for the configured time period, then delete all messages that match your filters at once, then wait again and repeat.

For example, if you set the limit to 5 minutes, the bot will delete all matching messages every 5 minutes. This creates periodic "cleanup sweeps" of your channel.

**Use cases:**
- Regular channel cleanups at predictable intervals
- Keeping announcement channels clean by clearing them every few hours
- Bulk cleanup of spam or temporary content at set times
- Less frequent deletion operations compared to Mode 1

To change the time interval, see [Limit](limit.md).

## Mode: 3 - Message Count-Based Bulk Deletion

**Delete all qualifying messages after a specific number of messages have been sent.** The bot counts matching messages and triggers a deletion when the count reaches your configured limit.

For example, if you set the limit to 10 messages, the bot will delete all matching messages once 10 qualifying messages have been posted. This keeps your channel at a maximum message count.

**Use cases:**
- Maintain a specific message history length
- Keep chat channels showing only the most recent X messages
- Limit spam in high-traffic channels by capping message count

> **ℹ️ Info:** If your channel has one or more configs with Mode 3 activated, messages are not processed until all old messages are loaded from Discord. You can see the status as `Waiting to be loaded` when using the `/debug` command. This is necessary for accurate message counting.

> **ℹ️ Info:** Due to Discord API rate limits and potential delays, the bot may delete slightly more messages than the exact limit at once. This is normal behavior to ensure consistent operation.

> **⚠️ Warning:** Using Mode 3 with any other Mode in the same channel can lead to slightly increased delays for message deletion. The different counting mechanisms can interfere with each other.

> **🚨 Danger:** It is **not recommended** to use 2 or more configs with Mode 3 in one channel. Multiple count-based configs will conflict with each other and may cause unpredictable deletion behavior.

## Mode: 4 - Currently Unavailable

Mode 4 is currently unavailable and disabled. We are working to reimplement it with improved functionality. Stay tuned for updates on our [Support Server](https://eazyautodelete.xyz/discord/).

---

## Choosing the Right Mode

- **Mode 1** is best for most use cases where you want a continuous, rolling deletion of older messages
- **Mode 2** is ideal when you want predictable cleanup times and bulk operations
- **Mode 3** is perfect for maintaining a specific message history length
- **Mode 0** lets you pause deletion without losing your configuration

Remember that you can combine different modes across multiple configs in the same channel (within the config limit) to create complex deletion rules!
