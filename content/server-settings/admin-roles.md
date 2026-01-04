---
title: "Administrator Roles"
linkTitle: "👑 Administrator Roles"
weight: 1
---

Administrator Roles control which users have full access to EazyAutodelete's configuration features. Users with an assigned administrator role can create, modify, and delete configs, as well as access all bot commands and features.

## What are Administrator Roles?

Administrator Roles are Discord roles that you designate as having administrative privileges for EazyAutodelete. When a user has at least one of these roles, they gain the ability to manage the bot's deletion configurations and settings.

### Key Capabilities

Users with administrator roles can:

- ✅ Create new deletion configs with `/setup`
- ✅ Modify existing deletion configs
- ✅ Delete configs
- ✅ Change all configuration settings (modes, filters, limits, etc.)
- ✅ Configure role-based deletion rules
- ✅ Set time boundaries for deletion
- ✅ Access all moderator-level commands
- ✅ Access all user-level commands
- ✅ Configure server-wide bot settings

### Automatic Administrator Access

Users with the following permissions **automatically** have administrator access, even if no roles are configured:

- **Discord's "Administrator" permission** - Built-in Discord permission that grants full server control
- **Server Owner** - The server owner always has full access

This ensures that server owners and administrators can always configure the bot, even if no specific roles have been set up.

---

## Configuring Administrator Roles

### How to Set Up

1. Ensure you have Discord's "Administrator" permission or are the server owner
2. Use the bot's server configuration commands to add administrator roles
3. Select one or more roles from your server to designate as administrator roles
4. Users with any of these roles will immediately gain administrator access

### Best Practices

**Create a dedicated role**: Consider creating a specific "EazyAutodelete Admin" or "Bot Manager" role rather than using your main admin roles. This gives you fine-grained control over who can configure auto-deletion.

**Limit access**: Only assign administrator roles to users who:
- Understand how the bot works
- Are trusted with channel management
- Won't accidentally misconfigure deletion rules
- Are available to help troubleshoot issues

**Use multiple roles if needed**: In large servers, you might have different admin teams:
- Bot Management Team
- Channel Management Team  
- Server Leadership Team

**Document your choices**: Keep track of which roles have admin access and why

**Regular audits**: Periodically review:
- Who has administrator roles
- Whether they still need access
- If any changes are needed

---

## Permission Scenarios

### Scenario 1: Small Community Server

**Setup:**
- Administrator Roles: @Admins, @Server Owner
- These users can fully configure EazyAutodelete

**Why:** Simple structure, trusted admin team

### Scenario 2: Large Gaming Server

**Setup:**
- Administrator Roles: @Head Admin, @Bot Manager, @Channel Admin
- Different teams manage different aspects

**Why:** Distributed responsibility, specialized roles

### Scenario 3: Corporate/Professional Server

**Setup:**
- Administrator Roles: @IT Team, @Server Manager
- Only technical staff can configure automation

**Why:** Controlled environment, professional management

---

## Security Considerations

### What Administrators Can Do

Administrator role holders have significant power over channel content:
- They can configure deletion rules that remove messages immediately
- They can change existing configs that other admins created
- They can disable deletion by setting configs to Mode 0
- They can configure rules that affect the entire server's channels

### Recommendations

1. **Trust is essential**: Only give admin roles to users you completely trust
2. **Communication is key**: Ensure all admins communicate about config changes
3. **Use test channels**: Admins should test configs in test channels first
4. **Monitor changes**: Keep track of who makes configuration changes
5. **Backup important channels**: Consider regular backups of important channel content
6. **Educate your admins**: Ensure all users with admin roles understand the documentation

---

## Troubleshooting Administrator Access

### "I can't access `/setup`"

**Possible causes:**
- You don't have an administrator role
- You don't have Discord's "Administrator" permission
- The bot's role permissions may be misconfigured

**Solutions:**
1. Check if you have any of the configured administrator roles
2. Check if you have Discord's "Administrator" permission
3. Ask the server owner to verify administrator role configuration
4. Ensure the bot has proper permissions in the channel

### "Admin roles aren't working"

**Possible causes:**
- Roles haven't been configured yet
- Discord role hierarchy issues
- Bot permissions issues

**Solutions:**
1. Verify administrator roles are actually configured (ask server owner)
2. Check that users have the correct roles assigned in Discord
3. Ensure the bot's role is high enough in the role hierarchy
4. Contact support if issues persist

---

## Related Documentation

- [User Permissions](../reference/user-permissions.md) - Complete permission level breakdown
- [Moderator Roles](mod-roles.md) - Setting up moderator access
- [Server Settings](README.md) - Overview of server-wide settings
- [Getting Started](../getting-started.md) - Initial configuration guide

Need help configuring administrator roles? Join our [Support Server](https://eazyautodelete.xyz/discord/)!