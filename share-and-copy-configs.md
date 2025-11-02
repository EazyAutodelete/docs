---
title: share-and-copy-configs
description: 
published: true
date: 2025-11-02T19:50:26.097Z
tags: 
editor: markdown
dateCreated: 2025-11-02T19:50:13.651Z
---

# 🌐 Share & copy Configs

EazyAutodelete allows you to share your deletion configurations with others or reuse them across different channels and servers. This powerful feature saves time and ensures consistency when you need to apply the same deletion rules in multiple places.

## Overview

The share and copy system has two main features:

1. **Sharing Configs** - Make your config publicly available for others to copy
2. **Copying Configs** - Import shared configs or duplicate your own configs to other channels

---

## Sharing Configs

### What is Config Sharing?

Config sharing allows you to make your deletion configuration publicly accessible. Once shared, anyone with your share code or share URL can copy your exact config settings to their own channels.

### How to Share a Config

1. **Run the share command:**
   ```
   /share <configId>
   ```
   Replace `<configId>` with the ID of the config you want to share

2. **Receive your share information:**
   - **Share Code**: A unique alphanumeric code (e.g., `ABC123`)
   - **Share URL**: A full URL link that others can use
   - Both work identically - choose whichever is more convenient

3. **Distribute your config:**
   - Share the code or URL with others
   - Post it in community forums
   - Include it in tutorials or guides
   - Add it to server templates

### What Gets Shared

When you share a config, the following settings are copied:

- ✅ **Mode** - The deletion algorithm type
- ✅ **Filters** - All active filters and their settings
- ✅ **Filter Behavior** - Match ALL or match ONE logic
- ✅ **Limit** - Time duration or message count
- ✅ **Role Configuration** - Target/ignore role settings (role IDs)
- ✅ **Time Boundaries** - Delete messages after settings

### What Doesn't Get Shared

The following are **NOT** shared:

- ❌ Actual server-specific role objects (only role IDs)
- ❌ Channel information
- ❌ Server information
- ❌ Message history
- ❌ Your personal information
- ❌ Private server data

### Privacy & Security

**Public by design:** Anyone with your share code or URL can view and copy your config settings.

**No private data:** Shared configs don't expose:
- Your server name or ID
- Channel names or IDs
- User information
- Message content
- Other private details

**Role caveat:** Role IDs are included, but they only work if the destination server has roles with matching IDs (rare except for default roles).

### Use Cases for Sharing

**Community Templates:**
- Share optimal configs for specific use cases
- Create config collections for different channel types
- Build a library of tested configurations

**Documentation & Guides:**
- Include share codes in tutorials
- Provide ready-to-use examples
- Help others learn by example

**Server Templates:**
- Package configs with server templates
- Standardize configs across community servers
- Distribute best practices

**Team Coordination:**
- Share configs across team-managed servers
- Ensure consistent deletion rules
- Simplify multi-server management

---

## Copying Configs

### What is Config Copying?

Config copying allows you to:
- Import a publicly shared config from someone else
- Duplicate one of your own configs to another channel
- Quickly apply tested configurations without manual setup

### How to Copy a Config

#### Copying from a Share Code/URL

1. **Get the share information:**
   - Obtain a share code (e.g., `ABC123`) or share URL from someone
   
2. **Run the copy command:**
   ```
   /copy <shareId or shareURL>
   ```
   - Paste the share code or URL after the command
   - Run this command **in the channel** where you want the config

3. **Config is created:**
   - All settings are copied to your channel
   - You can now modify it as needed
   - Wait 60 seconds for activation

#### Copying from Your Own Server

You can copy configs within the same server without sharing first:

1. **Find the config ID:**
   - Use `/setup` to view your configs
   - Note the config ID you want to copy

2. **Run the copy command with config ID:**
   ```
   /copy <configId>
   ```
   - Run this command **in the target channel**
   - The config from the original channel is duplicated here

**Important:** Using a config ID (not share code/URL) **only works** if the config is in the same server. Cross-server copying requires a share code/URL.

### After Copying

Once a config is copied:

1. **Review the settings:**
   - Use `/setup` to view the copied config
   - Verify all settings are correct
   - Check filter and mode configurations

2. **Adjust if needed:**
   - Modify any settings that need customization
   - Update roles to match your server's roles
   - Adjust limits if necessary

3. **Handle role settings:**
   - Role IDs from shared configs likely won't match your server
   - Reconfigure target/ignore roles for your server
   - Remove invalid role references

4. **Test the config:**
   - Wait for the 60-second activation delay
   - Monitor behavior with `/debug`
   - Verify correct messages are being deleted

---

## Best Practices

### When Sharing Configs

**Document your config:**
- Explain what the config does
- Describe ideal use cases
- Note any special requirements
- Mention expected behavior

**Test thoroughly:**
- Ensure the config works as intended before sharing
- Test in a test channel first
- Verify all settings are correct

**Provide context:**
- Explain mode choice
- Describe filter logic
- Document intended channel types
- Mention any caveats

**Keep it updated:**
- If you improve the config, share a new version
- Notify users of updates
- Maintain documentation

### When Copying Configs

**Always review:**
- Don't blindly apply shared configs
- Understand what each setting does
- Verify it matches your needs
- Check all filters and mode

**Test first:**
- Create a test channel
- Copy the config there first
- Observe behavior before production use
- Ensure it works as expected

**Customize as needed:**
- Adjust limits for your activity level
- Update roles for your server
- Modify filters if needed
- Adapt to your specific use case

**Respect the original:**
- Give credit if sharing modified versions
- Follow any usage terms provided
- Report issues to the original sharer
- Provide feedback

---

## Common Workflows

### Workflow 1: Multi-Channel Setup

**Scenario:** You want the same deletion rules in 5 similar channels

1. Create and test config in first channel
2. Share the config with `/share <configId>`
3. Note the share code
4. In each remaining channel, run `/copy <shareCode>`
5. Verify all copies work correctly

**Time saved:** Minutes vs. manually configuring each channel

### Workflow 2: Server Template Distribution

**Scenario:** You manage multiple servers with similar structure

1. Perfect your configs in your template server
2. Share each config type (general chat, announcements, etc.)
3. Document share codes in your template guide
4. Use codes to quickly set up new servers
5. Adjust roles for each new server

### Workflow 3: Community Config Library

**Scenario:** Building a repository of useful configs

1. Create various configs for different use cases
2. Share each one with descriptive documentation
3. Compile share codes into a guide
4. Share with community
5. Gather feedback and iterate

---

## Troubleshooting

### "Share code not found"

**Possible causes:**
- Typo in the share code
- Share code expired (if applicable)
- Code never existed

**Solutions:**
- Double-check the code for typos
- Request the code again from the sharer
- Verify you're using the correct format

### "Copy failed"

**Possible causes:**
- Invalid share code or URL
- Permission issues in target channel
- Config limit reached in target channel

**Solutions:**
- Verify bot permissions in target channel
- Check you haven't exceeded config limit (3 standard, more with Premium)
- Try a different channel
- Contact support if issue persists

### "Role settings don't work"

**Cause:** Role IDs from the original server don't exist in your server

**Solution:**
- This is normal and expected
- After copying, manually reconfigure role settings
- Select roles from your server
- Use `/setup` to update role configuration

### "Config doesn't behave as expected"

**Possible causes:**
- Settings need adjustment for your server
- Different activity levels
- Misunderstood original purpose

**Solutions:**
- Review all settings carefully with `/setup`
- Check filters and filter behavior
- Verify mode and limit are appropriate
- Test in a test channel first
- Adjust settings as needed

---

## Advanced Tips

### Creating Config Packs

Create multiple related configs for different scenarios:
- **Pack 1**: Active chat channels (various activity levels)
- **Pack 2**: Announcement channels (different retention periods)
- **Pack 3**: Media channels (attachment-focused)
- **Pack 4**: Bot command channels (bot message cleanup)

Share all codes together as a comprehensive solution.

### Version Control

When updating shared configs:
- Share new version with updated code
- Document changes between versions
- Notify users of updates
- Keep changelog of improvements

### Community Contributions

Build a community config library:
- Encourage users to share their best configs
- Curate high-quality configs
- Create categories by use case
- Maintain a searchable database

---

## Frequently Asked Questions

**Q: Can I un-share a config?**
A: Once shared, the share code remains active. Create a new config if you need to stop sharing.

**Q: How many times can a shared config be copied?**
A: Unlimited! Anyone with the code can copy it as many times as they want.

**Q: Can I see who copied my shared config?**
A: No, copying is anonymous to protect privacy.

**Q: Do I need Premium to share configs?**
A: No, sharing and copying are available to all users.

**Q: Can I modify a copied config?**
A: Yes! Once copied, it's yours to modify freely.

**Q: Will the original config update if I modify my copy?**
A: No, they're independent after copying.

---

## Related Documentation

- [Configuration Overview](config/) - Understanding all config options
- [Getting Started](getting-started.md) - Creating your first config
- [Modes](config/mode.md) - Understanding deletion modes
- [Filters](config/filters.md) - Available filter options

Need help sharing or copying configs? Join our [Support Server](https://eazyautodelete.xyz/discord/)!
