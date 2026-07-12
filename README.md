# BROCK Bot - Discord Moderation Bot: User Documentation

<img align="right" src="https://github.com/user-attachments/assets/9e927405-a0f0-4ae2-81e5-d3c383214ef4" width="300">

<br/>

### Overview

BROCK Bot provides comprehensive moderation and management features for Cardano-based Discord servers, including automated nickname filtering, file attachment filtering, advanced link filtering, and detailed event logging organized into dedicated log threads. It also offers token-gated role assignment through Cardano wallet verification, so members can automatically earn (and lose) roles based on the assets they hold. Empower your moderation team to monitor your whole server from a single logs channel, and allow BROCK Bot to take on most of the workload via automated actions.

<br/><br/>

## Getting Started

> [!IMPORTANT]  
> Your server must have an active paid subscription to use this bot. The bot will leave immediately if no subscription is active. Purchase at least one month [here](https://brock.tools/brock-bot?subscribe) before inviting the bot. Anyone can top up any server's subscription at any time - once the bot is installed, use `/pay` to check days remaining or get a top-up link.

#### Once a subscription is active, [invite BROCK Bot to your server](https://discord.com/oauth2/authorize?client_id=1253779179455905882)

### Initial Setup

1. **Role hierarchy** - In Server Settings → Roles, drag BROCK Bot's role **above** every role it needs to assign or remove (your verify/base role, token-gated roles, and any roles used by automated kicks). The bot also needs permission to kick members, manage roles, and manage threads in the logs channel. Granting Administrator permission to the role will prevent any permission-related issues.

2. **Bot managers & ignored roles** - On join, the bot automatically adds every Administrator role to both the bot manager list and the ignored-roles list (exempt from automated moderation). Add more with `/add Bot Manager Role` and `/add Ignored Role` as needed.

3. **Logs channel** - Create a channel visible only to moderators, then run `/set Logs Channel`. When logging is enabled, events are organized automatically into threads inside that channel (Links & Invites, Deleted Posts, Edited Posts, Kicks & Bans, Mod Actions, Member Events). Use `/recreate_log_threads` if any thread goes missing.

4. **Enable features** - Use `/settings` or `/toggle` to turn features on. Set the logs channel first, then enable **Logs** before anything that depends on it (Action Alerts, Log Deleted Messages, Log Kicks and Bans).

   Recommended features to start with:
   - [Logs](#logs)
   - [Kick Blocked Nicknames](#kick-blocked-nicknames)
   - [Delete Attachments](#delete-attachments)
   - [Delete Server Invites](#delete-server-invites)
   - [Delete Links](#delete-links)
   - [Minimum Account Age](#minimum-account-age)
   - [Action Alerts](#action-alerts)
   - [Smart Responses](#smart-responses)
   - [Flagged Users Alert Channel](#flagged-users-alert-channel)

5. **Customize lists** - Use `/add` and `/remove` to tune the bot to your server:
   - **`/add Blocked Nickname`** - Add your staff and team display names so impersonators get kicked.
   - **`/add Whitelisted URL`** and **`/add Whitelisted File Type`** - Allow domains and attachments your community legitimately shares.
   - **`/view`** - Check current values for any setting.

6. **Support tickets (optional)** - If you use a ticket channel, run `/set Ticket Channel`. With [Smart Responses](#smart-responses) enabled, the bot directs members there when they ask for help.

7. **Member verification (optional)** - If you enable [Kick Unverified Users](#kick-unverified-users), post a verify button where new members will see it: run **`/verify_button`** in that channel and enter your base role's ID. Members click **Verify** to receive the role; anyone who doesn't within 1 hour is kicked.

8. **Ban known scammers** - Run **`/syncbans`** once after setup to ban every user on the public flagged-users list in your server.

9. **Token-gated roles (optional, Cardano servers)** - Use **`/add Token Role`** to map a token policy to a Discord role. Members link wallets with **`/verify`** and receive roles automatically based on what they hold.

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

- Delete Server Invites

- Delete Links

- Kick Unverified Users

- Action Alerts

- Minimum Account Age Required

- Flagged Users Alert Channel

- Smart Responses

- Activity Roles

- Boost Announcements

### `/toggle [setting]`
Quickly enable/disable individual features.

Available settings:

- Kick Blocked Nicknames

- Delete Attachments

- Delete Server Invites

- Delete Links

- Kick Unverified Users

- Logs

- Log Deleted Messages

- Log User Kicks and Bans

- Action Alerts

- Minimum Account Age

- Flagged Users Alert Channel

- Smart Responses

- Activity Roles

- Boost Announcements

### `/view [setting]`
View current values for various settings:

- Logs

- Logs Channel

- Ticket Channel

- Log Deleted Messages

- Log Kicks and Bans

- Minimum Account Age

- Blocked Nicknames

- Ignored Roles

- Ignored Categories

- Whitelisted URLs

- Whitelisted File Types

- Bot Manager Roles

- Flagged Users Alert Channel

- Smart Responses

- Proxy Bot

- Activity Roles

- Boost Announcement Channel

- Token Roles

### `/set [setting]`
Configure specific values for:

- Logs Channel

- Ticket Channel

- Minimum Account Age (days)

- Proxy Bot

- Boost Announcement Channel

### `/add [setting]`
Add items to various lists:

- Blocked Nickname

- Ignored Role

- Ignored Category

- Whitelisted URL

- Whitelisted File Type

- Bot Manager Role

- Activity Role

- Token Role
    - <sup>*Maps a Cardano token policy ID (and minimum quantity) to a Discord role. See [Wallet Verification & Token-Gated Roles](#wallet-verification--token-gated-roles).*</sup>

### `/remove [setting]`
Remove items from various lists:

- Blocked Nickname

- Ignored Role

- Ignored Category

- Whitelisted URL

- Whitelisted File Type

- Bot Manager Role

- Proxy Bot

- Ticket Channel
    - <sup>*This will ***not*** delete your ticket channel, BROCK Bot will simply stop directing members to it.*</sup>

- Activity Role

- Boost Announcement Channel

- Token Role

### `/flag [user_id]`
Flag a user as a scammer and ban them in all servers that use BROCK Bot.

### `/unflag [user_id]`
Unflag a user as a scammer and unban them in all servers that use BROCK Bot. To be used if a user was mistakenly flagged.

### `/syncbans`
Ban every user on the public flagged-users list in your server in one action. Useful right after inviting the bot, or any time you want to make sure your server is caught up with all known scammers that have been flagged. Reports how many users were newly banned, already banned, or failed, and posts a summary to your logs channel if logging is enabled.

### `/permit [user_id]`
Temporarily permit a new or existing user account to bypass certain automated checks (like minimum account age or blocked nickname) for 24 hours. This is useful for allowing legitimate new users who might otherwise be caught by filters.
- `user_id`: The ID of the user to permit.

### `/check_token [assetid]`
Check if a Cardano asset ID (fingerprint) is flagged as malicious in the [Cardano Scam Token Registry](https://github.com/BrockCruess/Cardano-Scam-Token-Registry). Asset ID must start with `asset...`

### `/remind [when] [message (optional)] [user (optional)]`
Set a reminder.
- `when`: Specify the duration until the reminder (e.g., "30m", "1h", "1h 30m", "1d", "1w"). Maximum 24 days.
- `message`: (Optional) A custom message for the reminder (max 200 characters). Default: "This is your reminder!"
- `user`: (Optional) Mention a user to remind. Defaults to the command user.

When the reminder is due, the bot posts it in the same channel where the reminder was set, mentioning the target user. If the target user posts any message in that channel *after* the reminder was set but *before* it's due, the reminder will be automatically cancelled and removed.

### `/pay`
Get a link to top up this server's bot subscription. The command shows how many days of subscription remain and links to the payment page. Anyone can run it, so members can chip in to keep the server covered. See [Subscriptions](#subscriptions) for more information.

### `/verify_button`
Post a verify button in the current channel. Opens a modal asking for the **Role ID** of the base role to grant. The bot sends an embedded message with a **Verify** button; when a member clicks it, they receive that role. This pairs with [Kick Unverified Users](#kick-unverified-users) - members who click the button within an hour of joining are counted as verified and won't be kicked.

Requires bot manager permission. The bot's role must be above the role being granted.

### `/verify`
Link a Cardano wallet to your Discord account. The bot replies with a private, expiring link to the verification page, where you connect and sign with your wallet (no funds are ever moved). Once verified, you'll automatically receive any [token-gated roles](#wallet-verification--token-gated-roles) you qualify for. Running `/verify` again lets you link additional wallets.

### `/unlink`
Remove a linked Cardano wallet from your account. Presents a menu of your linked wallets to choose from. Any token-gated roles that depended on the removed wallet will be revoked on the next sync.

### `/recreate_log_threads [force]`
Recreate the log threads inside your logs channel. Useful if a log thread was deleted or archived. Requires the `Manage Channels` permission.
- `force`: (Optional) Recreate all threads even if they already exist.

### `/list_log_threads`
List the current log threads for your server and show which ones are active, missing, or archived.

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

### Delete Server Invites
When enabled:

- Automatically deletes messages containing external server invites

- Logs deleted server invites if logging is enabled

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

- A member counts as verified as soon as they receive any role, so this works best alongside a verification flow where new members click a button to receive a base role

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

- All logs are sent to the configured logs channel

- Logs are automatically organized into dedicated threads within the logs channel to keep everything tidy and easy to scan: **Links & Invites**, **Deleted Posts**, **Edited Posts**, **Kicks & Bans**, **Mod Actions**, and **Member Events**

- Use `/recreate_log_threads` to (re)create these threads and `/list_log_threads` to check their status

- Use `/set Logs Channel` to define the logs channel

### Flagged Users Alert Channel
When enabled:

- Creates a dedicated channel for flagged user alerts, restricted to bot manager roles to reduce channel clutter for regular members

- Follows a public feed of flagged scammer accounts

- Every time a new scammer is flagged the feed will receive a new message with the user's information and a ban command that can be easily copied and pasted for quick action

- This allows your moderation team to ban known scammers even before they join your server

<br/>

## Other Features

### Nitro Boost Announcements

- Announces when a server member boosts the server

- Allows specifying a channel for boost announcements so that they are visible to all members

### Activity Roles

- Assigns specific roles to users based on their activity in the server

- Configurable activity thresholds for each role

### Wallet Verification & Token-Gated Roles

- Lets members link their Cardano wallet to their Discord account with the `/verify` command, then grants roles automatically based on the tokens they hold

- Verification happens on a secure external page where the member connects and signs with their wallet; signing only proves ownership and never moves any funds

- Add a token role with `/add Token Role`, mapping a token **policy ID** and a **minimum quantity** to a Discord role (for example, "hold at least 1 token from this policy → get this role")

- Members can link multiple wallets, and holdings are summed across all of their linked wallets when checking each rule

- Roles are re-checked on a recurring schedule: members who still meet the threshold keep their role, and members who no longer qualify (or who unlinked their wallet with `/unlink`) automatically lose it

- Great for verified holder roles, NFT-gated channels, and community perks

- BROCK Bot's role must be above any token role it manages in the role hierarchy

### Proxy Bot

- Optionally routes the bot's user-facing messages through your own bot account so responses appear under your server's preferred branding

- Configure it with `/set Proxy Bot`, view its status with `/view Proxy Bot`, and disconnect it with `/remove Proxy Bot`

<br/>

## Subscriptions

BROCK Bot runs on a paid subscription per server, purchased with stablecoins (USDA, USDM, USDCx or DJED) on Cardano.

- Use `/pay` in your server to get a top-up link and see how many days remain

- Anyone can top up any server's subscription at any time, in 30-day (monthly) increments

- Payments are credited automatically and in real time once the transaction is included in a block, with additional fallbacks to ensure nothing is missed

- When a subscription is running low (7 days or fewer remaining), the bot posts a warning to the logs channel and temporarily changes its nickname to **"Top-Up Needed!"** as a visible reminder; this clears automatically once the server is topped up

- If a subscription lapses completely, the bot will leave the server until it is renewed

<br/>

## Default Settings
BROCK Bot begins with preconfigured defaults:

- Blocked nicknames: `support`, `announcement`

- Whitelisted URLs: `tenor.com`, `imgflip.com`, `twitter.com`, `x.com`, `wikipedia.org`

- Whitelisted file types: `.png`, `.jpg`, `.jpeg`, `.gif`, `.txt`, `.log`

- Minimum account age: `30` days

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
> BROCK Bot is in a beta release state and is developed and maintained solely by me. If you notice anything regularly slipping past the bot, please report it on Discord `@brockcardano`. Feature requests are welcome - the more scammer behaviour I study, the better the bot gets, but it is already highly effective and will significantly reduce scammer activity in your server.

