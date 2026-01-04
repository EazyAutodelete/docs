---
title: Limit
description: The limit with which the deletion algorithm should work.
published: true
date: 2026-01-04T18:48:39.890Z
tags: 
editor: markdown
dateCreated: 2025-11-02T19:52:49.661Z
---

# ⌛ Limit

The **Limit** value is a crucial configuration setting that determines when messages are deleted. Depending on the [Mode](mode.md) you've selected, the limit is interpreted either as a **time duration** or as a **number of messages**.

All ranges here are inclusive ranges. Meaning "> 10 seconds" allows you to also use 10 seconds as a limit.

The listed limits are the Free Limits available for anyone in as many configs as they wish.

If you still need limits outside of these ranges, check the [✨ Premium Plan](https://eazyautodelete.xyz/premium) or reach out to the support server.
You can see the broader limits for premium users [here](https://eazyautodelete.xyz/faq#what-are-the-limits).

> **ℹ️ Info:** For Mode 1, Mode 2 and Mode 5 (time-based modes): If a message gets edited and only meets your configured filters after the change, the deletion timer still uses the original send time of the message. This might lead to a message being deleted immediately or very quickly after being edited, which is intended behavior to prevent unpredictable the deletion rules.

## Mode 1 - Time-Based Individual Deletion

Limit is specified as a **time duration**.

**Limitations:**
- The duration must be **more than 10 seconds**
- The duration must be **less than 7 days**

**Examples:**
- `2h` Delete each message after 2 hours
- `3d 6h 5m` Delete each message after 3 days, 6 hours and 5 minutes
- `720m` Delete each message after 720 minutes = 12 hours

---

## Mode 2 - Interval-Based Bulk Deletion  

Limit is specified as a **time duration**.

**Limitations:**
- The duration must be **more than 10 seconds**
- The duration must be **less than 2 days**

**Examples:**
- `4h` Delete all messages every 4 hours
- `2d 1h` Delete all messages every 2 days and 1 hour = every 49 hours

---

## Mode 3 - Message Count-Based Bulk Deletion

Limit is specified as a **simple number** (message count).

**Limitations:**
- The amount must be **between 10 and 100**

**Examples:**
- `15` Delete all messages once 15 messages were sent in the channel
- `100` Delete all messages after 100 messages in the channel

---

## Mode 4 - Message Count-Based Single Deletion

Limit is specified as a **simple number** (message count).

**Limitations:**
- The number must be **between 3 and 200** (inlusively)

**Examples:**
- `20` Keep the last 20 message in the channel

---

## Mode 5 - Delete Daily at

Limit is specified as a HH:mm 24 hour format **time**.
The timezone used for the calculation is [UTC±0](https://en.wikipedia.org/wiki/UTC%2B00:00).

**Examples:**
- `19:00` Delete all messages daily at UTC±0 19:00 / 7pm
- `24:00` Delete all messages daily at UTC±0 midnight

---

## Supported Time Units

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
- Units can be in any order
- The bot will calculate the total duration automatically