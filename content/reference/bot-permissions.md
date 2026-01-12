---
title: "🤖 Bot Permissions"
weight: 1
---

EazyAutodelete requires specific permissions to function correctly within your Discord server. Below is a list of the essential permissions the bot needs, along with explanations of their purposes.

- **View Channel**: Allows the bot to see channels where it needs to operate.
- **Read Message History**: Enables the bot to read past messages in channels to determine which messages need to be deleted based on your configurations.
- **Manage Messages**: Grants the bot the ability to delete messages as per the configured rules.

## Function-Specific Permissions

### Voice Channels

If you want to use EazyAutodelete to autodelete messages in Voice Channels, the bot will also need:

- **Connect**: Allows the bot to connect to voice channels.

This is due to Discord's permission structure, which requires bots to have the Connect permission to interact with voice channels, even for message deletion purposes.
EazyAutodelete will never join or listen to a Voice Channel; it only needs this permission to manage messages in the voice channel's text channel.

---

### `/autodelete-notice` Command

To use the `/autodelete-notice` command, the bot additionally requires the following permission:

- **Send Messages**: Allows the bot to send the notice message in the channel where the command is executed.

---

### `/duplicate` Command

For the `/duplicate` command to function, the bot needs these permissions as well:

- **Manage Channels**: Enables the bot to create duplicate channels as specified by the command.

