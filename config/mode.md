---
description: How the deletion algorithm works
---

# ⚙️ Mode

Currently 4 different modes are supported. You can create multiple configs with different modes.

Each mode works with all available [filters.md](filters.md "mention"). In each mode, all messages that do not meet the configured filters are completely ignored.

{% hint style="warning" %}
To prevent unwanted behavior: you have to set a new [limit](limit.md) after changing the mode.
{% endhint %}

## Mode: 0

Disable the deletion algorithm. The bot will not delete messages.

{% hint style="info" %}
If there is a problem with your channel or your configs, the bot will automatically change all cofigs to mode 0.
{% endhint %}

## Mode: 1

Delete each messages after the configured time.

To change the time, see [limit.md](limit.md "mention").&#x20;

## Mode: 2

Delete all messages after the configured time. For example, delete all messages every 5 minutes.

To change the time, see [limit.md](limit.md "mention").&#x20;

## Mode: 3

Delete all messages after the configurent amount of messages. For example, delete all messages every 10 messages.

{% hint style="info" %}
If your channel has one ore more configs with mode 3 activated, messages are not handled until all old messages are loaded. You can see this as `Waiting to be loaded` on the `/debug` command.
{% endhint %}

{% hint style="info" %}
In the case of delays, the bot may delete more messages than the limit at once.
{% endhint %}

{% hint style="warning" %}
Using Mode 3 with any Mode in one channel can lead to slightly increased delays for message deletion.
{% endhint %}

{% hint style="danger" %}
It is not recommended to use 2 or more configs with mode 3 in one channel.
{% endhint %}

## Mode: 4

Mode 4 is currently unavailable. We are working to get it back again.
