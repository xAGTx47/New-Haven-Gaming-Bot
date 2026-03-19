# 🔊 Custom Voice Channels

Members can purchase a permanent custom voice channel from the server shop and manage it entirely using the `/vc` command. The channel stays even when everyone leaves — members only need to buy it once.

---

## Buying a Custom VC

Purchase the **Custom VC** item from the shop with `/buy`. You can name the channel right in the command using the optional `channel-name` field — if you skip it, it defaults to `username's VC`. The channel is created instantly in the designated category. Only one custom VC per member is allowed at a time.

**Examples:**
- `/buy item:Custom VC channel-name:Late Night Lounge` — creates a VC named "Late Night Lounge"
- `/buy item:Custom VC` — creates a VC named after your username

You can rename it any time with `/vc name`.

---

## How Privacy Works

| Mode | @everyone | Guests (added via `/vc add`) |
|---|---|---|
| **Public** (default) | Can see and join freely | — |
| **Private** | Can see the channel but **cannot join** | Can see and join |

Switch modes at any time with `/vc privacy`.

---

## Owner Perks

- **Priority Speaker** — your voice takes priority in the channel automatically
- **Full control** — rename, resize, set bitrate, manage the guest & blacklist, mute/ban members in-channel only

---

## Command Reference

All commands require you to be inside **your own custom VC** to work, except `/vc help` and `/vc host` which work anywhere. `/vc help` posts the embed publicly so everyone in the channel can see it.

> **Don't own a Custom VC yet?** If you try to use any `/vc` command without owning one, the bot will reply publicly with an embed explaining how to get one. Everyone in the channel will see it.

### ⚙️ Settings

| Command | Description |
|---|---|
| `/vc name <name>` | Rename your voice channel |
| `/vc size <limit>` | Set the user limit — 0 for unlimited |
| `/vc privacy <public/private>` | Open or lock your channel |
| `/vc bitrate <kbps>` | Set audio quality (8–96 kbps) |

### 👥 Guest Management

| Command | Description |
|---|---|
| `/vc add <user>` | Add a member to your guestlist — they can join even when private |
| `/vc remove <user>` | Remove a member from your guestlist |
| `/vc blacklist <user>` | Block a member from connecting |
| `/vc whitelist <user>` | Remove a member from the blacklist |
| `/vc guests` | View your current guestlist and blacklist |

### 🔇 VC-Only Moderation

These actions affect **only your voice channel** — they have zero impact on the server itself.

| Command | Description |
|---|---|
| `/vc mute <user>` | Prevent a member from speaking in your VC |
| `/vc unmute <user>` | Restore a member's speaking ability |
| `/vc ban <user>` | Remove and block a member from your VC — kicks them instantly if they are inside |
| `/vc unban <user>` | Remove a member's VC ban |

### 📋 Info & Other

| Command | Description |
|---|---|
| `/vc help` | Show all custom VC commands |
| `/vc info` | Show your channel's current settings |
| `/vc view` | Show a channel overview and link |
| `/vc host [channel]` | See who owns a custom VC — defaults to your current VC |
| `/vc invite <user>` | Add a member to your channel permissions so they can join |
| `/vc reset` | Reset your channel to default name, size, bitrate, and clear all overwrites |
| `/vc transfer <user>` | Hand ownership to another member — Priority Speaker moves with it |

---

## Admin Setup

Run `/vc setup category: <category>` to set the server category where purchased VCs are created. Requires **Bot Owner** only.
