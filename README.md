# BROCK Bot - Discord Moderation Bot: User Documentation

<img align="right" src="https://github.com/user-attachments/assets/9e927405-a0f0-4ae2-81e5-d3c383214ef4" width="300">

<br/>

### Overview

BROCK Bot provides comprehensive moderation and management features for Cardano-based Discord servers, including automated nickname filtering, file attachment filtering, advanced link filtering, channel deletion prompts for support tickets that have been closed for *`n`* days, and detailed event logging. Empower your moderation team to monitor your whole server from a single logs channel, and allow BROCK Bot to take on most of the workload via automated actions.

<br/><br/>

## Getting Started

> [!IMPORTANT]  
> Your server must be whitelisted to use this bot. The bot will leave your server immediately if it is not whitelisted. There is no payment subscription to get whitelisted. Instead you must delegate at least 250k ADA to BROCK Pool. Please contact me on Discord `@brockcardano` **before** you delegate, so that I can confirm your wallet address(es) prior to the delegation going on-chain. This helps confirm your wallet ownership.

#### Start by [Inviting BROCK Bot to your server](https://discord.com/oauth2/authorize?client_id=1253779179455905882)

### Initial Setup

1. Upon joining, the bot automatically assigns bot manager permissions to all roles with administrator permissions. Bot manager roles can use all bot commands and features. More bot manager roles can be added using the `/add Bot Manager Role` command.

2. Bot manager roles are also automatically added to the Ignored Roles list to be exempt from all automated moderation actions. More ignored roles can be added using the `/add Ignored Role` command.

3. Use the `/set Logs Channel` command to set your logs channel. This channel should only be visible to moderators and admins.

4. If you have a support ticket channel, use the `/set Ticket Channel` command to set your support ticket channel. BROCK Bot will automatically direct users to this channel when they request help as long as the Smart Responses feature is enabled.

5. Use the `/settings` command to start enabling moderation features. Recommended features to start with are:
    - [Logs](#logs)
    - [Action Alerts](#action-alerts)
    - [Delete Attachments](#delete-attachments)
    - [Delete Links](#delete-links)
    - [Smart Responses](#smart-responses)
    - [Flagged Users Alert Channel](#flagged-users-alert-channel)

6. Use the `/view`, `/add` and `/remove` commands to customize feature settings.

<br/>

## Commands

All commands use Discord's slash command system (`/command`).

### `/settings`
View all features and their descriptions.

Each setting has its own button to enable/disable:

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

- Smart Responses

### `/toggle [setting]`
Quickly enable/disable individual features.

Available settings:

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

- Smart Responses

### `/view [setting]`
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

- Smart Responses

### `/set [setting]`
Configure specific values for:

- Logs Channel

- Minimum Account Age (days)

- Channel Expiry Days
    - <sup>*Applies to channels within Expired Channels Categories. See [Expired Channels](#expired-channels) for more information.*</sup>

- Ticket Channel

### `/add [setting]`
Add items to various lists:

- Blocked Nickname

- Ignored Role

- Ignored Category

- Whitelisted URL

- Whitelisted File Type

- Bot Manager Role

- Expired Channels Category

### `/remove [setting]`
Remove items from various lists:

- Blocked Nickname

- Ignored Role

- Ignored Category

- Whitelisted URL

- Whitelisted File Type

- Bot Manager Role

- Expired Channels Category

- Ticket Channel
    - <sup>*This will ***not*** delete your ticket channel, BROCK Bot will simply stop directing members to it.*</sup>

### `/check_token [assetid]`
Check if a Cardano asset ID (fingerprint) is flagged as malicious in the [Cardano Scam Token Registry](https://github.com/BrockCruess/Cardano-Scam-Token-Registry). Asset ID must start with `asset...`

<br/>

## Moderation Features

### Smart Responses
When enabled:

- Automatically responds to messages when common keywords are detected

- Detect common phrases used by scammers and post a warning message in response

- Detect when someone is requesting help, and direct them to your server's support ticket channel

- Use `/set Ticket Channel` to define your server's support ticket channel

- Reminds members of scammer activity when there's a possibility of a scam message being posted, and reminds members to use the proper channels for support

### Kick Blocked Nicknames
When enabled:

- Automatically kicks users with nicknames containing blocked nicknames

- Kicks users with emoji-only nicknames

- Logs these actions if logging is enabled

- Provides ban buttons in logs for quick action

- Scammers often copy the nicknames of staff members, or act as an announcement bot (often using an emoji-only nickname) to share malicious information with other members

### Delete Attachments
When enabled:

- Deletes messages containing non-whitelisted file attachment types

- Configurable whitelist of allowed file extensions

- Optional alerts to users when messages are deleted

- Logs deleted attachment names if logging is enabled

- Whitelisting media-based file extensions (.jpg, .png, .gif, etc.) and relevant file type requirements for technical support (.log files for example) allows your community to safely share media and also share relevant files with support staff while blocking malicious files from being shared

### Delete Links
When enabled:

- Automatically deletes messages containing non-whitelisted URLs

- Configurable whitelist of allowed domains

- Optional alerts to users when links are deleted

- Logs deleted links if logging is enabled

- Domain whitelisting is much more effective than blacklisting, as scam links change domains constantly

### Kick Unverified Users
When enabled:

- Kicks users who haven't received any roles within 1 hour of joining

- Logs kicked users if logging is enabled

- Most scammers join many servers at once, and don't immediately verify to receive a role in each server; whereas legitimate users usually verify immediately upon joining

### Minimum Account Age
When enabled:

- Kicks new members whose accounts are younger than the specified age

- Configurable minimum account age in days

- Logs kicked users if logging is enabled

- Most brand new accounts are scammers, and when they're instantly kicked upon joining they rarely come back later

### Logs
When enabled:

- Logs deleted messages

- Logs user kicks and bans

- Logs automated moderation actions

- Logs expired channel deletions

- All logs are sent to the configured logs channel

- Use `/set Logs Channel` to define the logs channel

### Flagged Users Alert Channel
When enabled:

- Creates a dedicated channel for flagged user alerts, restricted to bot manager roles to reduce channel clutter for regular members

- Follows a public feed of flagged scammer accounts

- Every time a new scammer is flagged the feed will receive a new message with the user's information and a ban command that can be easily copied and pasted for quick action

- This allows your moderation team to ban known scammers even before they join your server

<br/>

## Other Features

### Expired Channels
When enabled:

- Monitors specified categories for inactive channels

- Add categories to monitor for expired channels using `/add Expired Channels Category`

- Marks channels as expired after configured number of days

- Set the number of days before a channel is marked as expired using `/set Channel Expiry Days`

- Creates log entries with delete buttons for expired channels

- Allows for manual review and deletion of expired channels in one spot

- Discord buttons only remain functional for a few minutes, so expired buttons will be deleted and reposted to the logs channel automatically every 5 minutes

- Great for cleaning up support ticket channels that have been closed for a configured number of days

<br/>

## Default Settings
BROCK Bot begins with preconfigured defaults:

- Blocked nicknames: `support`, `announcement`

- Whitelisted URLs: `tenor.com`, `imgflip.com`, `twitter.com`, `x.com`, `wikipedia.org`

- Whitelisted file types: `.png`, `.jpg`, `.jpeg`, `.gif`, `.txt`, `.log`

- Minimum account age: `30` days

- Channel expiry: `7` days

- All moderation features are disabled by default

<br/>

## Best Practices
- Create a dedicated logging channel, only visible to moderators and admins

- Add blocked nicknames, including your team's nicknames

- Add whitelisted URLs and file types according to your community's needs

- Assign bot manager roles carefully, including admin and moderation roles

- Enable the features that interest you one at a time

<br/>

## Troubleshooting
- Ensure the bot has appropriate permissions and is above all regular roles in the role hierarchy

- Confirm that the logs channel is set if using logging features

- Confirm that bot manager roles are properly assigned for moderation staff to use bot features and configure the bot

- "This interaction failed" errors are usually client-side. Restarting your Discord client usually resolves the issue.

<br/><br/><br/>

> [!IMPORTANT]  
> BROCK Bot is in a beta release state, and is developed and maintained solely by me. This is why I don't charge a payment subscription, and instead use ADA delegation as a form of support for the project. If you notice anything regularly slipping past the bot, please report it to me on Discord `@brockcardano` so that I can fix it. If you have any feature requests, please let me know and I will do my best to implement them. The more scammer behaviour I study, the better the bot will get, but it is already at a state of high effectiveness and will significantly reduce the amount of scammer activity in your server.
