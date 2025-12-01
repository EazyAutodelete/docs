---
title: Limit
description: The limit with which the deletion algorithm should work.
published: true
date: 2025-11-29T17:08:41.468Z
tags: 
editor: markdown
dateCreated: 2025-11-02T19:52:49.661Z
---

# ⌛ Limit

The **Limit** value is a crucial configuration setting that determines when messages are deleted. Depending on the [Mode](mode.md) you've selected, the limit is interpreted either as a **time duration** or as a **number of messages**.

This setting works in conjunction with your chosen mode to control the deletion timing and frequency.

> **ℹ️ Info:** For Mode 1 and Mode 2 (time-based modes): If a message gets edited and only meets your configured filters after the change, the deletion timer still uses the original send time of the message. This might lead to a message being deleted immediately or very quickly after being edited, which is intended behavior to prevent circumventing the deletion rules.

## Specifying the limit for different modes

### Mode 1 - Time-Based Individual Deletion

Limit is specified as a **time duration**.

**Requirements:**
- The duration must be **more than 10 seconds**
- The duration must be **less than 7 days**

**Example:** Setting a limit of "2 hours" means each message will be deleted 2 hours after it was sent.

---

### Mode 2 - Interval-Based Bulk Deletion  

Limit is specified as a **time duration**.

**Requirements:**
- The duration must be **more than 10 seconds**
- The duration must be **less than 7 days**

**Example:** Setting a limit of "30 minutes" means all matching messages will be deleted every 30 minutes.

---

### Mode 3 - Message Count-Based Deletion

Limit is specified as a **simple number** (message count).

**Requirements:**
- The number must be **between 3 and 75**

**Example:** Setting a limit of "50" means all matching messages will be deleted once 50 qualifying messages have been posted.

---

### Mode 4 - Currently Unavailable

Limit would be specified as a **simple number**.

**Requirements (when available):**
- The number must be **between 3 and 50**

## How to specify durations

When setting a time duration for Mode 1 or Mode 2, you need to use specific time unit abbreviations. The bot understands various formats for flexibility.

### Supported Time Units

| Time Unit | Accepted Abbreviations | Example Usage |
| --------- | ---------------------- | ------------- |
| **Seconds** | `s`, `sec`, `secs` | `30s`, `45sec`, `60secs` |
| **Minutes** | `m`, `min`, `mins` | `5m`, `10min`, `30mins` |
| **Hours** | `h`, `hr`, `hrs` | `2h`, `3hr`, `12hrs` |
| **Days** | `d`, `day`, `days` | `1d`, `2day`, `3days` |

### Formatting Rules

**✅ Correct Examples:**
- `1mins 30sec` - 1 minute and 30 seconds
- `5mins` - 5 minutes
- `2hrs 3m` - 2 hours and 3 minutes  
- `1days 6hr 3min` - 1 day, 6 hours, and 3 minutes
- `30s` - 30 seconds
- `12h` - 12 hours

**❌ Incorrect Examples:**
- `1m30s` - Missing space between units
- `2,3h` - Using comma instead of space
- `1d6h3m` - Missing spaces between units
- `1d 6hsr 3n` - Typos in unit abbreviations

### Tips for Duration Input

- Always include a **space** between different time units
- You can mix different units: `1day 2hr 30min`
- Units can be in any order, but logical order (largest to smallest) is recommended
- The bot will calculate the total duration automatically
- Remember the limits: minimum 10 seconds, maximum 7 days

