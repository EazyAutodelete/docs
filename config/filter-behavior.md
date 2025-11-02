---
title: filter-behavior
description: 
published: true
date: 2025-11-02T19:52:21.879Z
tags: 
editor: markdown
dateCreated: 2025-11-02T19:52:09.354Z
---

# 🔂 Filter Behavior

**Filter Behavior** determines how multiple filters work together when you have more than one filter activated. This setting controls the logical relationship between your selected filters.

## Two Matching Modes

You can choose between two different filter matching behaviors:

### 1. Match ONE Activated Filter (OR Logic) - Default

Delete messages that match **AT LEAST ONE** of your activated [filters](filters.md).

**How it works:** If a message meets the criteria of ANY single filter you've selected, it will be deleted. This is a more flexible and inclusive approach.

**Example:** If you activate:
- Filter 3 (Contains Links)
- Filter 11 (Author is Bot)

Then the bot will delete messages that **either** contain links **OR** are from bots (or both). A message only needs to match one condition to be deleted.

**Best for:**
- Catching a wide variety of unwanted content
- Removing different types of messages with a single config
- More aggressive cleanup scenarios

---

### 2. Match ALL Activated Filters (AND Logic)

Delete messages that match **ALL** of your activated [filters](filters.md) simultaneously.

**How it works:** A message must meet the criteria of EVERY filter you've selected to be deleted. This is a more strict and precise approach.

**Example:** If you activate:
- Filter 3 (Contains Links)
- Filter 11 (Author is Bot)

Then the bot will delete messages that **both** contain links **AND** are from bots. A message must satisfy both conditions to be deleted.

**Best for:**
- Very specific targeting of certain message types
- Avoiding accidental deletion of wanted content
- Precise cleanup scenarios where you want exact matches

---

## Default Setting

> **ℹ️ Info:** The default filter behavior is set to **"Match ONE activated filter"** (OR logic). This is the most commonly used setting as it provides broader coverage.

## Choosing the Right Behavior

- Use **"Match ONE"** when you want to cast a wider net and remove various types of messages
- Use **"Match ALL"** when you need surgical precision and want to target very specific messages
- You can change this setting at any time without affecting your other configuration options

---

![Filter Behavior Selection Interface](.gitbook/assets/image%20(1).png)

*The filter behavior selection in the bot's configuration interface*
