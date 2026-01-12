---
date: '2026-01-04T23:03:18+01:00'
title: '⚙️ Modes'
weight: 10
---


EazyAutodelete currently supports 5 (+1) different deletion modes, each designed for specific use cases. You can create multiple configs with different modes in different channels, or even multiple configs with different modes in the same channel (up to 3 configs per channel, or more with [Premium](/premium)).

Each mode works with all available [Filters](/config/filters). In each mode, all messages that do not meet the configured filters are completely ignored by the deletion algorithm.

> **⚠️ Warning:** To prevent unwanted behavior and ensure your config works as expected, you **must** set a new [Limit](/config/limit) after changing the mode. Different modes interpret the limit value differently (as time or message count).

## Mode: 0 - Disabled

**Disable the deletion algorithm completely.** When set to Mode 0, the bot will not delete any messages in the channel for this config. This is useful when you want to temporarily pause deletion without deleting your entire configuration.

> **ℹ️ Info:** If the bot encounters a problem with your channel or your configs (such as missing permissions), it will automatically change all configs to Mode 0 as a safety mechanism. This prevents the bot from operating incorrectly or causing unintended deletions. Check the `/debug` command to see why your configs were disabled.

## Mode: 1 - Time-Based Individual Deletion

**Delete each message individually after a configured amount of time has passed since it was sent.** This is the most commonly used mode and provides a "self-destructing messages" effect.

For example, if you set the limit to 30 seconds, each message will be deleted exactly 30 seconds after it was posted. This creates a rolling deletion effect where messages gradually disappear as they age.

**Example Use cases:**
- Create temporary chat channels where messages auto-delete after a set time
- Keep channels clean without permanently removing all conversation history at once
- Allow users to read recent messages while automatically cleaning up older ones

To change the time duration, see [Limit](/config/limit).

## Mode: 2 - Interval-Based Bulk Deletion

**Delete all qualifying messages at regular time intervals.** The bot will wait for the configured time period, then delete all messages that match your filters at once, then wait again and repeat.

For example, if you set the limit to 5 minutes, the bot will delete all matching messages every 5 minutes. This creates periodic "cleanup sweeps" of your channel.

In addition to the interval itself, you can also optionally provide the Date as YYYY-MM-DD and Time as HH:mm 24 hour format (both UTC±0) to set the time of when the interval is calculated.
Otherwise the bot will use the current time as the interval start and the first deletion run will be at "now" + "interval".

**Example Use cases:**
- Regular channel cleanups at predictable intervals
- Keeping channels clean by clearing them every few hours
- Bulk cleanup of spam or temporary content at set times

To change the time interval, see [Limit](/config/limit).

## Mode: 3 - Message Count-Based Bulk Deletion

**Delete all qualifying messages after a specific number of messages.** The bot counts matching messages and triggers a deletion when the count reaches your configured limit.

For example, if you set the limit to 10 messages, the bot will delete all matching messages once 10 qualifying messages have been sent.

**Example Use cases:**
- Limit spam in high-traffic channels by capping message count

## Mode: 4 - Message Count-Based Single Deletion

**Delete the oldest message after a specific number of messages**. The bot counts matching messages and deletes the oldest message as soon as the limit is reached.

For example, if you set the limit to 15 messages, the bot will delete the first matched message once a 16th message was sent. This keeps your channel at a maximum message count.

**Example Use cases:**
- Maintain a specific message history length
- Keep chat channels showing only the most recent X messages

## Mode: 5 - Delete Daily at

**Delete all matched messages daily at a specific time.** The bot collects all matched messages and deletes them all daily when the configured time is reached.

When configuring this mode, please be aware that the time is entered in the UTC±0 timezone and HH:mm 24-hour format.

**Example Use cases:**
- Have a fresh channel every morning at 09:00
- Delete all messages at 24:00 to only keep messages from that day

---

## Choosing the Right Mode

- **Mode 1** is best when you want to delete messages individually based on their send timestamp
- **Mode 2** is ideal when you want predictable cleanup times and bulk operations
- **Mode 3** is perfect for restricting the amount of messages for a channel
- **Mode 4** is perfect for maintaining a specific message history length
- **Mode 5** is perfect for a daily clean up
- **Mode 0** lets you pause deletion without losing your configuration

Remember that you can combine different modes across multiple configs in the same channel to create complex deletion rules!
