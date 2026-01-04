---
title: "Server Settings"
weight: 50
# bookFlatSection: false
# bookToc: true
# bookHidden: false
# bookCollapseSection: false
# bookComments: false
# bookSearchExclude: false
# bookHref: ''
# bookIcon: ''
---

# 🛠️ Server Settings

Server Settings allow server administrators to configure EazyAutodelete's behavior at the server level, including who has permission to use various bot commands. These settings apply server-wide and affect how users interact with the bot across all channels.

## Server-Wide Configuration Options

### Permission Role Configuration

* **[Administrator Roles](admin-roles.md)** - Configure which roles can create and modify deletion configs and use administrative commands
* **[Moderator Roles](mod-roles.md)** - Configure which roles can access moderation and logging commands without full admin privileges

---

## Understanding Permission Roles

EazyAutodelete uses a role-based permission system to control access to different bot features. Rather than relying solely on Discord's permission system, the bot allows you to designate specific roles that should have access to configuration and moderation features.

### Why Custom Permission Roles?

**Flexibility**: Not everyone with Discord's "Administrator" permission should be able to configure auto-deletion in every channel.

**Granular Control**: Separate admin capabilities (config management) from moderator capabilities (viewing logs and debug info).

**Safety**: Prevent accidental misconfiguration by limiting who can create and modify deletion rules.

### Permission Hierarchy

1. **Server Administrators** (highest)
   - Configure deletion configs with `/setup`
   - Manage all EazyAutodelete settings
   - Access all bot commands
   - Users with Discord's "Administrator" permission automatically have this level

2. **Server Moderators** (middle)
   - View logs and debug information
   - Access server statistics
   - Cannot modify deletion configs
   - Must have assigned moderator roles

3. **All Users** (lowest)
   - Basic commands like `/help` and `/premium`
   - View general information
   - Cannot modify any settings

---

## Best Practices

### Setting Up Permission Roles

1. **Create dedicated roles**: Consider creating specific roles like "AutoDelete Admin" or "AutoDelete Manager"
2. **Keep it limited**: Only assign admin roles to trusted users who understand the bot
3. **Use moderator roles wisely**: Give moderator access to users who need to troubleshoot without config access
4. **Regular audits**: Periodically review who has which roles
5. **Test changes**: Verify role permissions work as expected after configuration

### Common Configurations

**Small servers**: 
- Admin roles: Server Owner, Administrators
- Mod roles: Moderators, Helpers

**Large servers**:
- Admin roles: Server Owner, Head Admin, Bot Manager
- Mod roles: Moderators, Trial Mods, Support Team

**Bot-heavy servers**:
- Admin roles: Bot Admin (dedicated role)
- Mod roles: Bot Support, Server Moderators

---

## Configuring Roles

To configure permission roles for EazyAutodelete:

1. Ensure you have Discord's "Administrator" permission or are the server owner
2. Use the bot's server settings commands (check `/help` for specific commands)
3. Select the roles you want to assign as admin or moderator roles
4. Test the configuration with users who have those roles

---

## Related Documentation

- [User Permissions](../reference/user-permissions.md) - Detailed breakdown of permission levels
- [Getting Started](../getting-started.md) - Initial bot setup
- [Troubleshooting](../troubleshooting.md) - Permission-related issues

Need assistance? Visit our [Support Server](https://eazyautodelete.xyz/discord/) for help!