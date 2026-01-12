---
title: "User Permissions"
linkTitle: "👑 User Permissions"
weight: 1
---

EazyAutodelete uses 3 primary Permission Levels to control which commands users have access to.

## 1. All Users

This Permission Level is assigned to all commands that every user has access to. `/autodelete`, `/help` or `/premium` are examples of these commands.

## 2. Server Moderators

This Permission Level is assigned to all commands regarding logging and general information about the setup of EazyAutodelete on a server.

Users are considered "Moderators" if they have at least one role from the server's configured ["Moderator Roles"](../server-settings/mod-roles.md).

## 3. Server Administrators

This Permission Level is assigned to all commands that change the Delete Configurations in a Server. This includes the `/setup` command.

Users are recognized as Administrators if they have at least one role from server's configred ["Administrator Roles"](../server-settings/admin-roles.md) assigned or have the Discord "Administrator" permission.

## Additional Permissions

Certain commands on your server may be accessible to the Bot's Support Staff and Developers, even if explicit permission has not been granted. This is done to ensure the prompt and efficient handling of your inquiry.
