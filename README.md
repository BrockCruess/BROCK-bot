# Discord Moderation Bot - User Documentation

<br/>

## Overview
This bot provides comprehensive moderation and management features for Discord servers, including automated nickname filtering, attachment control, link management, channel expiry, and detailed logging capabilities.

<br/>

## Getting Started

### Initial Setup

> [!IMPORTANT]  
> Your server must be whitelisted to use this bot. It will leave your server immediately if it is not whitelisted. There is no payment subscription to get whitelisted. Instead you must delegate at least 1 million ADA to BROCK Pool. Please contact me on Discord `@brockcardano` **before** you delegate, so that I can confirm your wallet address(es) prior to the delegation going on-chain. This helps confirm your wallet ownership.

1. The bot automatically assigns bot manager permissions to roles with administrator privileges when it joins your server

2. Bot manager roles can use all bot commands and features

3. Bot manager roles are automatically added to the ignored roles list (exempt from automated moderation)

<br/>

## Commands
All commands use Discord's slash command system (`/command`).

### Core Settings Commands

#### `/settings`
View and toggle all boolean settings through an interactive interface. Each setting has its own button to toggle on/off:

- Logs

- Log Deleted Messages

- Log Kicks and Bans

- Kick Blocked Nicknames

- Delete Attachments

- Kick Unverified Users

- Delete Links

- Action Alerts

- Minimum Account Age Required

- Flagged Users Alert Channel

#### `/toggle [setting]`
Quickly toggle individual settings on/off. Available settings:

- Kick Blocked Nicknames

- Delete Attachments

- Kick Unverified Users

- Delete Links

- Expired Channels

- Logs

- Log Deleted Messages

- Log User Kicks and Bans

- Action Alerts

- Minimum Account Age

- Flagged Users Alert Channel

#### `/view [setting]`
View current values for various settings:

- Logs Channel

- Logs Status

- Log Deleted Messages Status

- Log Kicks and Bans Status

- Minimum Account Age

- Blocked Nicknames List

- Ignored Roles List

- Ignored Categories List

- Whitelisted URLs List

- Whitelisted File Types List

- Bot Manager Roles List

- Expired Channels Categories List

- Channel Expiry Days

#### `/set [setting]`
Configure specific values for:

- Logs Channel (select channel for bot logs)

- Minimum Account Age (days)

- Channel Expiry Days

#### `/add [setting]`
Add items to various lists:

- Blocked Nickname

- Ignored Role

- Ignored Category

- Whitelisted URL

- Whitelisted File Type

- Bot Manager Role

- Expired Channels Category

#### `/remove [setting]`
Remove items from the same lists as `/add`

### Special Commands

#### `/check_token [assetid]`
Check if a Cardano asset ID is flagged as malicious in the scam registry.

<br/>

## Features

### Nickname Management
When enabled:

- Automatically kicks users with blocked nicknames

- Kicks users with emoji-only nicknames

- Logs these actions if logging is enabled

- Provides ban buttons in logs for quick action

### Attachment Control
When enabled:

- Deletes messages containing non-whitelisted file types

- Configurable whitelist of allowed file extensions

- Optional alerts to users when attachments are deleted

- Logs deleted attachments if logging is enabled

### Link Management
When enabled:

- Automatically deletes messages containing non-whitelisted URLs

- Configurable whitelist of allowed domains

- Optional alerts to users when links are deleted

- Logs deleted links if logging is enabled

### User Verification
When enabled:

- Kicks users who haven't received any roles within 1 hour of joining

- Logs kicked users if logging is enabled

### Minimum Account Age
When enabled:

- Kicks new members whose accounts are younger than the specified age

- Configurable minimum age in days

- Logs kicked users if logging is enabled

### Channel Expiry
When enabled:

- Monitors specified categories for inactive channels

- Marks channels as expired after configured number of days

- Creates log entries with delete buttons for expired channels

- Allows manual review and deletion of expired channels

### Logging System
When enabled:

- Logs deleted messages

- Logs user kicks and bans

- Logs automated moderation actions

- Logs channel deletions

- All logs sent to designated logging channel

### Flagged Users Alert Channel
When enabled:

- Creates a dedicated channel for flagged user alerts

- Follows official announcement channel for scammer alerts

- Restricted to bot manager roles

<br/>

## Default Settings
The bot comes with sensible defaults:
- Blocked nicknames: "support", "announcement"
- Whitelisted URLs: tenor.com, imgflip.com, twitter.com, x.com, wikipedia.org
- Whitelisted file types: .png, .jpg, .jpeg, .gif, .txt, .log
- Channel expiry: 7 days

<br/>

## Best Practices
- Set up a dedicated logging channel

- Review and customize blocked nicknames

- Configure whitelisted URLs and file types

- Assign bot manager roles carefully

- Test settings in a controlled channel first

<br/>

## Troubleshooting
- Ensure the bot has appropriate permissions

- Check if roles/channels are properly configured

- Verify logging channel is set if using logging features

- Confirm bot manager roles are properly assigned
