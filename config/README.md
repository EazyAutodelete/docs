---
title: README
description: Customize everything according to your needs
published: true
date: 2025-11-02T19:51:23.678Z
tags: 
editor: markdown
dateCreated: 2025-11-02T19:51:10.455Z
---

# 🚮 Delete Configuration

> **ℹ️ Info:** The bot will wait one minute after your last change to a config before starting to apply any changes. This buffer period ensures that you can make multiple adjustments without the bot starting and stopping repeatedly.

EazyAutodelete provides comprehensive configuration options that allow you to customize the deletion algorithm exactly to your needs. You can fine-tune which messages get deleted, when they get deleted, and how the bot behaves in your channels.

## Configuration Options

Below you'll find all available configuration settings for customizing message deletion:

### Core Settings

* **[⚙️ Modes](mode.md)** - Choose how the deletion algorithm works (delete messages after time, delete all at intervals, etc.)
* **[⌛ Limit](limit.md)** - Set the time duration or message count that triggers deletion
* **[🔎 Filters](filters.md)** - Select which types of messages to delete (with emojis, with links, bot messages, etc.)
* **[🔂 Filter Behavior](filter-behavior.md)** - Control whether messages must match ALL filters or just ONE filter

### Time-Based Filtering

* **[⏪ Delete messages before](delete-messages-before.md)** - Only delete messages sent before a specific message (deprecated)
* **[⏩ Delete messages after](delete-messages-after.md)** - Only delete messages sent after a specific message

### Role-Based Configuration

* **[👥 Roles](roles.md)** - Target or ignore messages from users with specific roles

### Message Loading

* **[📡 Load old messages](load-old-messages.md)** - Choose whether to delete messages sent before the config was created

---

## Getting Started with Configuration

1. Use `/setup` command to create or modify a config
2. Choose your desired mode based on your deletion needs
3. Add filters to specify which messages should be deleted
4. Set a limit appropriate for your chosen mode
5. Configure any additional settings like roles or time filters
6. Wait one minute for the bot to start processing

For a step-by-step guide on setting up your first config, see [Getting Started](/getting-started).
