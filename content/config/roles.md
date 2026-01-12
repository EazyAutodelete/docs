---
title: "👥 Roles"
weight: 40
---

**Role filtering** allows you to control whose messages are affected by your deletion config based on their Discord roles. This is powerful for creating different deletion rules for different user groups in your server.

You can choose to either **target specific roles** (only delete messages from users with these roles) or **ignore specific roles** (delete messages from everyone except users with these roles).

## How Role Filtering Works

When you configure roles, you're essentially creating a whitelist or blacklist for your deletion algorithm:

- **Target Roles**: Only messages from users with at least one of the selected roles will be considered for deletion
- **Ignore Roles**: Messages from users with at least one of the selected roles will never be deleted

> **⚠️ Important:** When you set new target roles, any previously configured ignore roles will be automatically cleared, and vice versa. You cannot have both target and ignore roles active at the same time - you must choose one approach.

## Role Limits

- **Standard users**: Select up to **10 roles** to target or ignore
- **[Premium](/premium) users**: Select up to **20 roles** to target or ignore

This gives you flexibility to create complex role-based deletion rules for large servers with many different user groups.

## Target Roles

**Only delete messages from members that have one or more of the selected roles.**

When you enable target roles, the bot will exclusively focus on messages from users who have been assigned at least one of the roles you've selected. All other messages from users without these roles will be completely ignored by the deletion algorithm.

**Use cases:**
- Clean up messages from a specific "Temporary Member" role
- Delete messages from "Muted" or "Restricted" users
- Target bot roles or service accounts for cleanup
- Focus deletion on trainee or trial member roles

**Important notes:**
- Messages from users WITHOUT the target roles are ignored and **not counted** when using Mode 3 (message count) or Mode 4
- A user only needs ONE of the target roles to have their messages affected
- This is useful for creating VIP or moderator protection while cleaning up regular user messages

## Ignore Roles

**Ignore messages from members that have one or more of the selected roles.**

When you enable ignore roles, the bot will completely skip messages from users who have been assigned at least one of the roles you've selected. Only messages from users WITHOUT these roles will be considered for deletion.

**Use cases:**
- Protect messages from moderators and administrators
- Preserve messages from verified or trusted members
- Keep bot command messages while deleting user messages
- Exclude VIP, supporter, or donor roles from cleanup
- Maintain messages from content creators or event organizers

**Important notes:**
- Messages from users WITH the ignore roles are not processed and **not counted** when using Mode 3 (message count) or Mode 4
- A user only needs ONE of the ignore roles to have their messages protected
- This is the most common role configuration as it lets you protect important user groups

---

## Tips for Role Configuration

1. **Plan your role structure**: Think about which user groups should be affected by auto-deletion before creating roles
2. **Use descriptive role names**: This makes it easier to select the right roles in the configuration
3. **Test with ignore roles first**: It's safer to start by protecting important roles rather than targeting specific ones
4. **Combine with filters**: Role filtering works alongside all other filters for precise control
5. **Regular reviews**: Periodically review your role configuration as your server grows and changes