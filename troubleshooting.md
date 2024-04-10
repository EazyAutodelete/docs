# 🤬 Troubleshooting

Common issues to check in case the bot isn't doing what you want it to.

{% hint style="info" %}
The configs are always changing back to Mode 0??

This means that there is an error in the channel. Check all the following steps.
{% endhint %}

If you have any further questions, please visit the support server at [https://eazyautodelete.xyz/discord](https://eazyautodelete.xyz/discord).

## Check the permissions

The bot MUST have the following permissions in the channel you want to use it in:

* View Channel
* Read Message History
* Manage Messages

All 3 of them are mandatory for the bot to work.

## Double-Check your configs

It often happens that people forget some options and the result does not meet their expectations.

You can follow this checklist to check your configs:

* [ ] Is the **Mode** set correctly?
* [ ] Are the **Filters** set correctly?
* [ ] Is the **Filter Behavior** set correctly?
* [ ] Is the **Limit** set correctly?
* [ ] Is it correctly set whether to **load old messages**?

If you have any questions about a mode, a filter or other config options, read the documentation or ask in our support server at [https://eazyautodelete.xyz/discord](https://eazyautodelete.xyz/discord).

## Check the /debug command

The `/debug` command provides you with useful information about your channel. Not only does it show you the IDs of your channel and server, which can be helpful when reaching out to us in the [Support Server](https://eazyautodelete.xyz/discord), but it also shows you details about what the deletion algorithm is doing to your channel.

