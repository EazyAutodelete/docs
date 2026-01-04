---
title: "Mod Roles"
weight: 1
# bookFlatSection: false
# bookToc: true
# bookHidden: false
# bookCollapseSection: false
# bookComments: false
# bookSearchExclude: false
# bookHref: ''
# bookIcon: ''
---

# 🛡️ Moderator Roles

Moderator Roles grant users access to logging, debugging, and informational commands without giving them the ability to modify deletion configurations. This permission level is perfect for support staff and moderators who need to troubleshoot issues without the risk of accidentally changing deletion rules.

## What are Moderator Roles?

Moderator Roles are Discord roles that you designate as having moderator-level access to EazyAutodelete. Users with these roles can view detailed information about bot operations and help troubleshoot problems, but cannot create or modify configs.

### Key Capabilities

Users with moderator roles can:

- ✅ Use `/debug` to view channel status and configuration details
- ✅ Access logging commands to see bot activity
- ✅ View general information about configs (but not modify them)
- ✅ Help troubleshoot issues by gathering diagnostic information
- ✅ Access all user-level commands like `/help` and `/premium`

### What Moderators Cannot Do

Moderators **cannot**:

- ❌ Create new configs
- ❌ Modify existing configs with `/setup`
- ❌ Delete configs
- ❌ Change deletion settings (modes, filters, limits)
- ❌ Configure server-wide settings
- ❌ Modify role-based deletion rules

This separation ensures moderators can help users and troubleshoot problems without accidentally breaking working configurations.

---

## Why Use Moderator Roles?

### Benefits of Moderator-Level Access

**Safe Troubleshooting**: Moderators can investigate issues without risk of breaking configs

**Distributed Support**: Allow your mod team to handle support requests without admin access

**Better Support Experience**: Mods can gather diagnostic info quickly to help users

**Reduced Admin Burden**: Admins don't need to handle every troubleshooting request

**Training Ground**: New team members can learn the bot with limited access before getting admin rights

### Common Use Cases

- Support team members helping users troubleshoot
- Trial moderators who need limited access
- Community helpers who answer questions
- Staff members who monitor bot performance
- Debug assistants who gather information for admins

---

## Configuring Moderator Roles

### How to Set Up

1. Ensure you have administrator access to EazyAutodelete or Discord's "Administrator" permission
2. Use the bot's server configuration commands to add moderator roles
3. Select one or more roles from your server to designate as moderator roles
4. Users with any of these roles will immediately gain moderator access

### Role Selection Strategies

**Existing mod roles**: Use your existing @Moderator or @Support roles

**Dedicated role**: Create a specific "EazyAutodelete Moderator" role for bot-specific access

**Tiered system**: Use different mod roles for different access levels:
- Trial Moderators: Basic access
- Full Moderators: Moderator + some admin access
- Head Moderators: Full admin access

**Department-based**: Assign based on responsibility:
- Support Team: Moderator access
- Management Team: Administrator access

---

## Best Practices

### Choosing Moderators

Give moderator roles to users who:

- ✓ Regularly help users with questions
- ✓ Understand basic bot concepts
- ✓ Are trusted not to share sensitive information
- ✓ Are active and responsive
- ✓ Have good communication skills

### Role Management

**Start with moderator access**: New team members should start with moderator access before graduating to admin

**Clear documentation**: Ensure mods know what they can and cannot do

**Support training**: Train moderators on using `/debug` and interpreting results

**Communication channels**: Create channels where mods can escalate to admins

**Regular reviews**: Periodically audit who has moderator access

---

## Using Moderator Commands Effectively

### The `/debug` Command

**What mods can see:**
- Channel and server IDs
- Active configs and their current states
- Bot processing status
- Error messages and warnings
- Message loading progress
- Permission status

**How to help users:**
1. User reports issue → Ask them to run `/debug`
2. Review the output for obvious issues
3. Check for permission errors or Mode 0 status
4. Guide user through basic troubleshooting
5. Escalate to admins if config changes are needed

### Gathering Information

When helping users, moderators should:

1. **Get the basics**: Channel ID, Server ID (from `/debug`)
2. **Check permissions**: Verify bot has required permissions
3. **Review config**: Note current mode, filters, limit (visible in `/debug`)
4. **Check status**: Is bot waiting, processing, or errored?
5. **Document the issue**: Take screenshots for admin review if needed

---

## Permission Scenarios

### Scenario 1: Community Server

**Setup:**
- Moderator Roles: @Community Helpers, @Support Team
- Administrator Roles: @Server Admins

**Why:** Helpers can troubleshoot without accidentally changing configs

### Scenario 2: Large Public Server  

**Setup:**
- Moderator Roles: @Trial Mod, @Moderator
- Administrator Roles: @Senior Mod, @Admin

**Why:** Progressive access system as mods gain experience

### Scenario 3: Gaming Guild

**Setup:**
- Moderator Roles: @Officers
- Administrator Roles: @Guild Leadership

**Why:** Officers handle day-to-day support, leadership configures automation

---

## Troubleshooting Moderator Access

### "I can't use `/debug`"

**Possible causes:**
- You don't have a moderator role assigned
- Moderator roles haven't been configured yet
- You're trying in a DM (must be in server)

**Solutions:**
1. Verify you have a configured moderator role
2. Ask an admin if moderator roles are set up
3. Ensure you're running the command in a server channel

### "Moderator roles not working"

**Possible causes:**
- Roles weren't saved properly
- Discord role sync issues
- Bot permission problems

**Solutions:**
1. Ask admin to verify moderator role configuration
2. Try removing and re-adding the role to users
3. Restart Discord client (cache issue)
4. Contact support if persists

---

## Moderator Command Reference

### Available Commands (typically)

- `/debug` - View channel and bot status
- `/help` - View all available commands
- `/info` - Bot information
- `/premium` - Premium feature information
- `/language` - View available languages

**Note:** Exact available commands may vary. Use `/help` to see what you can access.

### Commands NOT Available

- `/setup` - Requires administrator role
- Config modification commands - Admin only
- Server-wide setting commands - Admin only

---

## Upgrading from Moderator to Administrator

If a moderator proves capable and trustworthy, consider upgrading them to administrator access:

1. **Evaluate performance**: Have they been helpful and responsible?
2. **Test knowledge**: Do they understand how configs work?
3. **Add training**: Ensure they've read the full documentation
4. **Give test channel**: Let them practice in a test environment first
5. **Assign admin role**: Grant administrator role when ready
6. **Monitor initially**: Watch their first few config changes

---

## Related Documentation

- [User Permissions](../reference/user-permissions.md) - Complete permission level breakdown
- [Administrator Roles](admin-roles.md) - Setting up administrator access
- [Server Settings](README.md) - Overview of server-wide settings
- [Troubleshooting](../troubleshooting.md) - How to use `/debug` effectively

Need help with moderator roles? Visit our [Support Server](https://eazyautodelete.xyz/discord/)!