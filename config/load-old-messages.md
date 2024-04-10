# 📡 Load old messages

After changing a config you are asked whether to load (and delete) old messages.&#x20;

## Yes, load old messages

When selecting old messages, the bot will start to load messages that were sent before the config was created. Due to Discord's API limitations the bot will only load (and delete) messages that were sent in the past 13,9583 days.

## No, don't laod old messages

When selection to not load old messages, the bot will not load (or delete) any old messages.

The bot will save in your configuration to only handle any messages that are sent after the current timestamp. You can edit this anytime by using the [delete-messages-after.md](delete-messages-after.md "mention").

When selection to not load old messages for one config, this might stop also the loading of old messages in that specific channel.
