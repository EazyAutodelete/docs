---
title: Add to Server
description: How to add EazyAutodelete to your server
published: true
date: 2025-11-02T21:44:30.306Z
tags: 
editor: markdown
dateCreated: 2025-11-02T19:49:00.880Z
---

# ➕ Add to server

Adding EazyAutodelete to your Discord server is a straightforward process that takes just a minute. Follow these steps to invite the bot and grant it the necessary permissions to function properly.

## Prerequisites

Before you begin, make sure you have:

- **Administrator permission** or **Manage Server permission** on the Discord server where you want to add the bot

If you don't have the required permissions, ask your server owner or an administrator to add the bot for you.

---

## Step-by-Step Installation

### Step 1: Visit the Invite Page

Navigate to the official EazyAutodelete invite page:

🔗 **[https://eazyautodelete.xyz/invite](https://eazyautodelete.xyz/invite)**

This is the only official invite link for EazyAutodelete. Be cautious of fake or phishing links from other sources.

### Step 2: Select Your Server

On the authorization page:

1. **Click the dropdown menu** that says "Select a server"
2. **Choose the server** where you want to add EazyAutodelete
3. Only servers where you have permission to add bots will appear in the list

**Can't see your server?**
- Verify you have Administrator or Manage Server permission
- Try refreshing the page
- Check if you're logged into the correct Discord account

### Step 3: Review Permissions

The authorization page will show all the permissions EazyAutodelete needs to function:

**Required Permissions:**
- **View Channels** - So the bot can see your channels
- **Send Messages** - For configuration confirmations and responses
- **Manage Messages** - To delete messages (core functionality)
- **Read Message History** - To see past messages for deletion [(loading old messages)](/reference/load-old-messages)
- **Embed Links** - For formatted messages and responses
- Additional permissions for full functionality

> **⚠️ Important: Do NOT change or remove any permissions!**
> 
> All requested permissions are necessary for EazyAutodelete to work correctly. Removing permissions will cause the bot to malfunction or fail entirely. If you remove permissions, you may see configs automatically switching to Mode 0 (disabled) or error messages.

### Step 4: Authorize the Bot

1. **Review the permissions** (but don't change them)
2. **Click the "Authorize" button**
3. **Complete the CAPTCHA** verification (if prompted)
4. Wait for the success confirmation

### Step 5: Confirmation

Once authorization is complete:

- You'll see a success message on the webpage
- EazyAutodelete will appear in your server's member list
- The bot will be online and ready to configure
- You can close the browser window

---

## Verifying the Installation

To confirm EazyAutodelete was added successfully:

### Check the Member List

1. Open your Discord server
2. Look at the member list on the right side
3. Find "EazyAutodelete" in the member list (usually under a "Bots" section)
4. The bot should show as online (green status)

### Test with a Command

Try running a basic command:

```
/help
```

If the bot responds with a help message, the installation was successful!

---

## Granting Channel Permissions

After adding the bot to your server, you may need to grant it access to specific channels:

### Option 1: Server-Wide Access (Recommended)

The easiest approach is to let the bot have server-wide permissions:

1. The bot automatically gets permissions based on its role
2. No additional configuration needed
3. Works in all channels by default

### Option 2: Channel-Specific Access

If you want to restrict the bots permissions to specific channels:

1. **Go to Channel Settings:**
   - Right-click the channel
   - Select "Edit Channel"
   - Go to "Permissions" tab

2. **Add EazyAutodelete:**
   - Click "+" to add a role or member
   - Search for "EazyAutodelete"
   - Add the bot

3. **Grant Required Permissions:**
   - ✅ View Channel
   - ✅ Read Message History
   - ✅ Manage Messages
   - Save changes

4. **Repeat for each channel** where you want to use the bot

> **💡 Tip:** If you're unsure, grant server-wide access.

---

## Next Steps

Now that EazyAutodelete is on your server, you're ready to configure it!

### 1. Create Your First Config

Jump straight into configuring automatic message deletion:

📖 **[Getting Started Guide](getting-started.md)** - Complete setup walkthrough

**Quick start:**
1. Go to a channel where you want auto-deletion
2. Run `/setup`
3. Select "Create Config"
4. Follow the prompts

### 2. Explore Features

Learn about all the available features:

- **[Configuration Options](config/)** - Deep dive into all settings
- **[Modes](config/mode)** - Different deletion algorithms
- **[Filters](config/filters)** - Targeting specific message types
- **[Roles](config/roles)** - Role-based deletion rules

### 3. Configure Server Settings

Set up permission roles for your server:

- **[Server Settings](server-settings/)** - Server-wide configuration
- **[Administrator Roles](server-settings/admin-roles)** - Who can configure the bot
- **[Moderator Roles](server-settings/mod-roles)** - Who can view logs and debug info

### 4. Get Support

Need help or have questions?

- **[Troubleshooting Guide](troubleshooting)** - Common issues and solutions
- **[Support Server](https://eazyautodelete.xyz/discord/)** - Join our community
- **[FAQ](https://eazyautodelete.xyz/faq)** - Frequently asked questions

---

## Troubleshooting Installation

### "I don't see the server I want"

**Possible causes:**
- You don't have Administrator or Manage Server permission
- You're logged into the wrong Discord account
- The server has bot restrictions

**Solutions:**
1. Verify your permissions on the target server
2. Log out and log back in with the correct account
3. Ask the server owner to check bot addition settings
4. Ensure you're not trying to add to a DM or group

### "Bot joined but appears offline"

**Possible causes:**
- Temporary connection issue
- Discord API delays
- Bot restart in progress

**Solutions:**
1. Wait a few minutes and refresh
2. Check [Discord Status](https://discordstatus.com/)
3. Try mentioning the bot to see if it's actually online
4. Contact support if persists for more than 10 minutes

### "Bot can't see messages/delete"

**Possible causes:**
- Missing channel permissions
- Permission overrides blocking the bot
- Role hierarchy issues

**Solutions:**
1. Check channel-specific permissions (see "Granting Channel Permissions" above)
2. Ensure no permission overrides are denying access
3. Move bot role higher in role hierarchy if needed
4. Verify the three required permissions are granted

---

## Security & Privacy

### Official Invite Only

**Always use the official invite link:** [https://eazyautodelete.xyz/invite](https://eazyautodelete.xyz/invite)

**Beware of:**
- Fake bots with similar names
- Phishing links pretending to be EazyAutodelete
- Unofficial "mirror" or "backup" versions
- Requests for login credentials (EazyAutodelete never asks for your passwords)

### Permission Safety

**Why we need these permissions:**
- **View Channels**: To see where configs are set up
- **Manage Messages**: To delete messages (core function)
- **Read Message History**: To load and process old messages
- All other permissions support these core functions

**We will NEVER:**
- Access messages in channels without configs
- Share your messages or data
- Use permissions for anything other than stated functionality
- Ask for additional permissions beyond what's needed

### Data Privacy

EazyAutodelete respects your privacy:
- Only processes messages in channels with active configs
- Doesn't store message content long-term
- Doesn't share data with third parties
- Open source and transparent operations

You can get detailed information about how we use your data in our [Privacy Policy](https://eazyautodelete.xyz/privacy). You are also welcome to ask our support team at any time.

---

## Removing the Bot

If you ever need to remove EazyAutodelete from your server:

1. **Go to Server Settings** → **Members**
2. **Find EazyAutodelete** in the member list
3. **Right-click the bot** and select "Kick" or "Ban"
4. All configs will stop working immediately

**Note:** Kicking the bot does NOT delete its configuration data. If you re-add it later, you'll need to recreate configs from scratch as a security measure.

---

## Additional Resources

### Official Links

- **Bot Invite**: [eazyautodelete.xyz/invite](https://eazyautodelete.xyz/invite)
- **Support Server**: [eazyautodelete.xyz/discord](https://eazyautodelete.xyz/discord/)
- **Premium Subscription**: [eazyautodelete.xyz/premium](https://eazyautodelete.xyz/premium)
- **Website**: [eazyautodelete.xyz](https://eazyautodelete.xyz/)
- **FAQ**: [eazyautodelete.xyz/faq](https://eazyautodelete.xyz/faq)

### Community & Support

- **[Top.GG Page](https://top.gg/bot/746453621821931634)** - Vote and review
- **[Discord Bot List](https://discordbotlist.com/bots/eazyautodelete)** - Alternative listing
- **[Translation Project](https://github.com/EazyAutodelete/translations)** - Contribute translations

---

## Welcome Aboard!

Congratulations on adding EazyAutodelete to your server! We're excited to help you keep your channels clean and organized.

**What's next?**
1. ✅ Bot is installed
2. 📝 Create your first config with `/setup`
3. 🎉 Enjoy automated message deletion!

If you have any questions or need assistance, don't hesitate to join our **[Support Server](https://eazyautodelete.xyz/discord/)**. Our community and support team are here to help!

Happy auto-deleting! 🎉

