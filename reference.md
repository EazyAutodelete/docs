---
title: Reference
description: 
published: true
date: 2025-11-02T20:51:28.322Z
tags: 
editor: markdown
dateCreated: 2025-11-02T20:51:15.794Z
---

# 💬 Reference

Welcome to the EazyAutodelete reference section! This area contains in-depth documentation on core concepts, technical details, and important information for understanding how the bot works under the hood.

## Purpose of This Section

The Reference section is designed to:

- **Explain fundamental concepts** that apply across multiple features
- **Provide technical details** for power users and administrators
- **Clarify Discord-specific terminology** and limitations
- **Document permission systems** and access control
- **Serve as a knowledge base** for advanced users

Unlike configuration guides that focus on "how to do X," reference documentation focuses on "how X works and why."

---

## Reference Topics

### Permission & Access Control

**[👑 User Permissions](reference/user-permissions.md)**

Comprehensive breakdown of EazyAutodelete's three-tier permission system:
- **All Users**: Basic commands available to everyone
- **Server Moderators**: Logging and debugging access
- **Server Administrators**: Full configuration control

Learn who can use which commands, how permission levels are determined, and how to configure custom permission roles in your server.

**Key concepts covered:**
- Permission level hierarchy
- Automatic permission grants (Discord Administrator)
- Moderator vs Administrator distinction
- Support staff access
- Role-based permission assignment

---

### Message Processing

**[🔙 Load old Messages](reference/load-old-messages.md)**

Deep dive into how EazyAutodelete handles historical messages when creating or modifying configs:
- **Technical process**: How message loading works behind the scenes
- **Discord limitations**: The 14-day bulk deletion restriction explained
- **Performance impact**: Loading times and server impact
- **Mode interactions**: How different modes handle old messages
- **Best practices**: When to load and when not to load

**Key concepts covered:**
- Message loading process and timeline
- Discord API constraints
- Background processing
- Status monitoring with `/debug`
- Impact on different deletion modes

---

## Understanding EazyAutodelete Concepts

### Core Terminology

**Config (Configuration)**
A set of rules defining how messages should be deleted in a specific channel. Includes mode, filters, limit, and optional settings.

**Mode**
The deletion algorithm type that determines when and how messages are deleted (individual, interval-based, or count-based).

**Filter**
A criterion that messages must meet (or not meet) to be considered for deletion. Examples: has attachments, is from a bot, contains links.

**Filter Behavior**
The logical relationship between multiple filters - either ALL filters must match (AND logic) or at least ONE filter must match (OR logic).

**Limit**
The time duration or message count that triggers deletion, depending on the mode.

**Permission Level**
The tier of access a user has to EazyAutodelete commands (User, Moderator, or Administrator).

### How Configs Work

1. **Channel-Specific**: Each config applies only to the channel where it was created
2. **Independent Operation**: Multiple configs can run simultaneously in the same channel
3. **60-Second Delay**: Changes don't take effect immediately to allow batch editing
4. **Persistent**: Configs remain active even when you're offline
5. **Automatic Safety**: Bot disables configs (Mode 0) if it detects errors

### Message Lifecycle

Understanding how EazyAutodelete processes messages:

1. **Message Posted**: User sends a message in a channel with active configs
2. **Initial Check**: Bot checks if message is eligible for processing
3. **Filter Evaluation**: Message is tested against all active filters
4. **Behavior Logic**: Filter Behavior determines if message qualifies
5. **Mode Processing**: Message is handled according to the mode
6. **Limit Tracking**: Time or count is tracked for deletion timing
7. **Deletion**: Message is deleted when criteria are met
8. **Logging**: Deletion is logged internally for debugging

---

## Discord Platform Constraints

### API Limitations

EazyAutodelete operates within Discord's API constraints:

**Bulk Deletion Window**
- Messages older than 14 days (~13.96 days) cannot be bulk deleted
- Individual deletion of old messages is extremely slow and rate-limited
- This is a Discord limitation, not a bot limitation

**Rate Limits**
- Discord restricts how fast bots can delete messages
- Large deletion operations take time
- High-traffic channels may experience processing delays
- This ensures platform stability

**Permission Requirements**
- Bot must have proper permissions in each channel
- Missing permissions cause automatic config disable (Mode 0)
- Permission checks happen before each operation

### Message History

**Loading Limitations:**
- Can only load messages from the past 14 days
- Discord API paginates results (100 messages per request)
- Very active channels take longer to load
- Loading happens in the background

**Storage Constraints:**
- Discord limits how far back bots can fetch messages
- Very old messages may not be accessible via API
- Message IDs are used for temporal boundaries

---

## Permission Architecture

### Three-Tier System

EazyAutodelete uses a three-level permission model:

**Level 1: All Users**
- View help documentation
- Check bot status and info
- View language options
- Access general information
- No configuration access

**Level 2: Server Moderators**
- All Level 1 capabilities
- Use `/debug` command
- View logs and diagnostics
- Monitor bot performance
- Check config status (read-only)
- Cannot modify configs

**Level 3: Server Administrators**
- All Level 1 and 2 capabilities
- Create/modify/delete configs
- Configure server-wide settings
- Manage permission roles
- Full control over bot behavior
- Access all commands

### Permission Determination

**Automatic Administrator Access:**
- Discord "Administrator" permission holders
- Server owner
- Always have Level 3 access regardless of role configuration

**Configured Roles:**
- Administrator Roles: Designated roles with Level 3 access
- Moderator Roles: Designated roles with Level 2 access
- Configured via server settings commands

**Fallback Behavior:**
- If no roles configured, only Discord Administrators and owner have elevated access
- Regular users always have Level 1 access
- Role hierarchy is respected

---

## Technical Specifications

### Config Limits

**Standard Users:**
- 3 configs per channel maximum
- 10 roles for target/ignore filtering
- All modes and filters available
- Standard support

**Premium Users:**
- More than 3 configs per channel
- 20 roles for target/ignore filtering
- All modes and filters available
- Priority support

### Mode Specifications

| Mode | Type | Limit Format | Min | Max | Processing |
|------|------|--------------|-----|-----|------------|
| 0 | Disabled | N/A | N/A | N/A | No deletion |
| 1 | Individual Time | Duration | 10s | 7d | Per-message |
| 2 | Interval Bulk | Duration | 10s | 7d | Batch deletion |
| 3 | Count-Based | Message Count | 3 | 75 | Batch deletion |
| 4 | Unavailable | N/A | N/A | N/A | Not implemented |

### Filter Categories

**Content Filters:** (Emojis, Links, Attachments)
- Analyze message content and metadata
- Fast evaluation
- No external API calls

**Author Filters:** (Bot, Roles)
- Check author properties
- Cached for performance
- Role-based require server data

**Status Filters:** (Pinned, Thread, Reply)
- Check message flags and relationships
- Discord API data
- May require additional checks

**Announcement Filters:** (Published, Crosspost)
- Announcement channel specific
- Check message properties
- Only work in announcement channels

---

## Bot Behavior Patterns

### Activation Delay

**60-Second Wait Period:**
- Prevents rapid start/stop cycles during configuration
- Allows users to make multiple changes
- Reduces API calls and processing overhead
- Countdown resets with each config modification

### Error Handling

**Automatic Mode 0:**
- Bot switches configs to Mode 0 on error detection
- Prevents incorrect deletion
- Requires manual review and fix
- Common triggers: permission loss, invalid configuration

**Safety Mechanisms:**
- Permission verification before operations
- Config validation on modification
- Error logging for debugging
- Graceful degradation on failures

### Performance Optimization

**Message Loading:**
- Batched API requests (100 messages per batch)
- Background processing doesn't block channels
- Shared loading across multiple configs
- Cancellation on config deletion

**Deletion Operations:**
- Respects Discord rate limits
- Batches deletions when possible
- Priority queue for time-sensitive deletions
- Optimized for minimal API calls

---

## Data & Privacy

### What Data is Stored

**Configuration Data:**
- Channel IDs and config settings
- Mode, filters, limits, and role IDs
- Timestamps for scheduling
- No message content

**Operational Data:**
- Processing queues and status
- Error logs for debugging
- Performance metrics
- No personal user data

### What Data is NOT Stored

- ❌ Message content or text
- ❌ User messages or DMs
- ❌ Personal user information
- ❌ Channel message history
- ❌ Any data from non-configured channels

### Data Retention

- Config data: Retained until config is deleted
- Operational data: Temporary, cleared regularly
- Error logs: Retained for debugging, then purged
- No long-term message storage

---

## Advanced Topics

### Multi-Config Interactions

**When using multiple configs in one channel:**
- Each config processes messages independently
- Filters are evaluated per-config
- First matching config may delete before others process
- Mode 3 conflicts with other Mode 3 configs

**Best Practices:**
- Use complementary, not competing configs
- Avoid multiple Mode 3 configs
- Test interactions in test channels
- Document multi-config strategies

### Cross-Server Considerations

**Config Sharing:**
- Share codes work across servers
- Role IDs likely won't match (need reconfiguration)
- Time boundaries use message IDs (server-specific)
- Filters and modes copy exactly

**Server-Specific Settings:**
- Permission roles are per-server
- Language settings are per-server
- Each server's configs are independent
- No cross-server interference

---

## Frequently Referenced Information

### Command Quick Reference

| Command | Permission Level | Purpose |
|---------|------------------|---------|
| `/help` | All Users | View help information |
| `/autodelete` | All Users | Quick config info |
| `/language` | Administrators | Change bot language |
| `/debug` | Moderators | View channel status |
| `/setup` | Administrators | Configure deletion |
| `/share` | Administrators | Share config |
| `/copy` | Administrators | Copy config |

### Common Issues

Most issues fall into these categories:
1. **Permission problems** - Missing required permissions
2. **Configuration errors** - Incorrect settings
3. **Misunderstood behavior** - Feature working as designed but unexpected
4. **Discord limitations** - API constraints affecting operations

See [Troubleshooting Guide](troubleshooting.md) for detailed solutions.

---

## Additional Resources

### Configuration Guides
- [Getting Started](getting-started.md) - Initial setup
- [Configuration Overview](config.md) - All config options
- [Modes](config/mode.md) - Deletion algorithms
- [Filters](config/filters.md) - Message targeting

### Server Management
- [Server Settings](server-settings/) - Server-wide configuration
- [Administrator Roles](server-settings/admin-roles.md) - Admin access control
- [Moderator Roles](server-settings/mod-roles.md) - Moderator access control

### Community
- [Support Server](https://eazyautodelete.xyz/discord/) - Get help
- [Premium Features](premium.md) - Enhanced capabilities
- [Voting](voting-for-eazyautodelete.md) - Support the bot

---

## Contributing to Documentation

Found an error or want to improve the reference documentation?

- Report issues in our Support Server
- Suggest improvements and clarifications
- Help us identify confusing sections
- Share your expertise with the community

Your feedback helps make these docs better for everyone!

---

**Questions not covered in reference docs?** Check our [Support Server](https://eazyautodelete.xyz/discord/) or other documentation sections!