---
title: getting-started
description: A quick guide on how to get started with EazyAutodelete.
published: true
date: 2025-11-02T19:49:33.047Z
tags: 
editor: markdown
dateCreated: 2025-11-02T19:49:19.302Z
---

# 🚀 Getting Started

## Inviting the Bot

Adding EazyAutodelete to your server is pretty simple.

You can find a step-by-step guide on how to add EazyAutodelete to your server here:

{% content-ref url="add-to-server.md" %}
[add-to-server.md](add-to-server.md)
{% endcontent-ref %}

## Setting up the deletion algorithm

EazyAutodelete deletes messages based on user-created **configs**. A config only applies to **the channel in which you ran the command**. You can create up to 3 configs per channel, with the [Premium version](https://eazyautodelete.xyz/premium) even more.

1. Run /setup and select "Create Config" to create a new config.
2. You can choose **different modes** for your config. If you wish to delete each message after x seconds, use mode 1. If you wish to delete all messages every x seconds, use mode 2. There are more modes to try out. Read more about them [here](https://docs.eazyautodelete.xyz/config/modes).
3. Once you have selected a mode, you can select **as many filters as you like**. In addition, you can set certain roles to be targeted or ignored as well as automatically applying your configs to new threads and so much more.
4. Finally, you select a limit value for your config. Depending on the mode, this is either a **duration or an amount of messages**.
5. After changing your config, EazyAutodelete will ask you whether you want to **load old messages**. If you wish messages that were sent before you set up the bot in this channel to be deleted, select yes, otherwise select no.

And that's it. Your good to go. After one minute, EazyAutodelete will start working just as you configured it to.

For more settings, see [Configuration](config/).
