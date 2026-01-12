---
date: '2026-01-12T20:05:07+01:00'
title: '🔙 Load old Messages'
---

When configuring EazyAutodelete, you will encounter the option to "load old messages." This setting determines whether the bot should process and potentially delete messages that were sent before the current configuration was created or last modified.

## What Does "Load Old Messages" Mean?

When you create or modify a deletion configuration, EazyAutodelete gives you the choice to either:

1. **Yes, load old messages**: The bot will go back and evaluate messages that were sent before the configuration was created or last changed. It will apply your filters and deletion rules to these historical messages, potentially deleting them if they match the criteria.

2. **No, don't load old messages**: The bot will only consider messages sent after the current timestamp. All existing messages in the channel will be ignored by this configuration, and only new messages will be processed going forward.
This will set the [Delete Messages after](/config/delete-messages-after) timestamp to the current time, effectively skipping all prior messages.
