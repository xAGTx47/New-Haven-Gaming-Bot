# 🔨 Moderation Commands

> These commands are only visible to members with the appropriate server permissions.

---

## Member Actions

| Command | Permission | Description |
|---|---|---|
| `/kick <user> [reason]` | Kick Members | Kick a member from the server |
| `/ban <user> [reason]` | Ban Members | Ban a member from the server |
| `/unban <user_id>` | Ban Members | Unban a previously banned user by their Discord ID |
| `/timeout <user> <duration> [reason]` | Moderate Members | Temporarily restrict a member from sending messages |
| `/setnick <user> [nickname]` | Manage Nicknames | Change a member's server nickname. Leave nickname blank to reset it |
| `/roleadd <user> <role>` | Manage Roles | Add a role to a member |

---

## Warnings

The warning system tracks rule violations per member. All three actions are now under the `/warn` command.

| Command | Permission | Description |
|---|---|---|
| `/warn add <user> <reason>` | Moderate Members | Issue a warning to a member — logged with moderator name and timestamp |
| `/warn view <user>` | Moderate Members | View all warnings on record for a member (shows last 10) |
| `/warn clear <user>` | Administrator | Clear all warnings for a member |

---

## Server Management

| Command | Permission | Description |
|---|---|---|
| `/purge <amount>` | Manage Messages | Bulk delete a set number of messages in the current channel |
| `/channel create <name> [category]` | Manage Channels | Create a new text or voice channel, optionally under a category |
| `/channel delete <channel>` | Manage Channels | Delete a channel — requires confirmation via button before executing |
| `/say <message> [mention]` | Manage Guild | Make the bot send a message in the current channel, with an optional role/user mention |
| `/poll <question> <opt1> <opt2> [opt3] [opt4]` | Manage Guild | Create a poll embed with up to 4 options and reaction voting |
| `/addemoji <emoji> [name]` | Manage Emojis | Copy an emoji from another server and add it to this one |

---

## Starboard

| Command | Permission | Description |
|---|---|---|
| `/starboard set <channel> [threshold]` | Manage Guild | Set the starboard channel. Optionally set how many ⭐ reactions are required (default: 3) |
| `/starboard disable` | Manage Guild | Disable the starboard entirely |
| `/starboard status` | Manage Guild | View the current starboard channel and threshold |

---

## Announcements & Posts

All posting commands use a guided flow: select a channel → choose a ping → fill in a modal. The three post types each have a role toggle button on the published embed so members can self-manage their pings.

| Command | Permission | Description |
|---|---|---|
| `/post update` | Manage Guild | Post a server update embed — includes a 🔔 Get Update Pings button |
| `/post announce` | Manage Guild | Post an announcement embed — includes a 🔔 Get Announcement Pings button |
| `/post botupdates` | Manage Guild | Post a bot update embed — includes a 🔔 Get Bot Update Pings button |

**Posting flow:**
1. Run `/post <type>`
2. Select the channel to post in
3. Choose who to ping (pick a role, @everyone, @here, or no ping)
4. Fill in the title, body, optional image URL, and optional footer in the modal
5. The embed is posted — done

---

## Shop Management

| Command | Permission | Description |
|---|---|---|
| `/shopadd <name> <price> [desc] [position]` | Bot Owner | Add a new item to the server shop. Use `position` to insert it at a specific slot — everything else shifts down |
| `/shopedit <item> [name] [price] [desc]` | Manage Guild | Edit an existing shop item — provide only the fields you want to change |
| `/shopremove <name>` | Manage Guild | Remove an item from the shop permanently |

---

## Custom Voice Channel Admin

| Command | Permission | Description |
|---|---|---|
| `/vc setup category: <category>` | Administrator | Set the category where member custom VCs are created. Must be run once before members can buy a Custom VC |

---

## Stat Overrides

| Command | Permission | Description |
|---|---|---|
| `/setmessages <user> <amount>` | Manage Guild | Manually set a member's message count |
| `/setinvites <user> <amount>` | Manage Guild | Manually set a member's invite count |
| `/coins add <user> <amount>` | Bot Owner | Give coins to a member without deducting from anyone else |
| `/coins remove <user> <amount>` | Bot Owner | Remove coins from a member |
