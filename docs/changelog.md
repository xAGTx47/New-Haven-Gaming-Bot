# New Haven Gaming Bot — Changelog

---

## Session — March 20, 2026

### Jail System

Getting caught during a `/rob` now sends you to jail for a random **15–30 minutes**. While in jail every coin-earning command is locked: `/rob`, `/crime`, `/bankrob`, `/work`, `/daily`, `/weekly`, `/monthly`, `/beg`, `/fish`, `/hunt`, `/mine`, `/sell`, `/sellall`, and all gambling commands. The failed rob embed shows a Discord timestamp for your exact release time. Viewing your balance, depositing, withdrawing, shopping, and buying still work normally.

---

### Rob Notifications (DMs)

The victim of a rob attempt now always receives a DM:
- **Successful rob** — told who robbed them and how many coins were taken
- **Failed rob** — told who tried and how much compensation they received
- **Shield blocked** — told whose attempt was blocked and that the shield was consumed

DMs fail gracefully if the victim has them closed — no errors are thrown.

---

### Lockpick — New Shop Item (🪙 200)

A **Lockpick** can be bought from the shop. When using `/rob`, an optional `lockpick:true` flag appears. If the target has a Rob Shield and you have a Lockpick and set the flag, the lockpick is consumed and the shield is bypassed — the rob proceeds normally. Without the flag (or without a lockpick), the shield blocks as normal.

---

### Spy — New Shop Item & Command (🪙 400)

A **Spy** item can be bought from the shop. Using `/spy <user>` consumes the item and reveals the target's current wallet balance in an ephemeral reply only you can see. Works on any member; cannot target yourself or bots.

---

### Robbery Leaderboard — `/roblb`

A new `/roblb` command shows two leaderboards side-by-side:
- **Top Robbers** — ranked by total coins stolen across all successful robs
- **Most Robbed** — ranked by number of times successfully robbed

Stats are tracked persistently in `data/robstats.json` and accumulate across bot restarts.

---

### `/balance` — Rob Shield Indicator

If you (or the user you're checking) have a **Rob Shield** in your inventory, `/balance` now shows **🛡️ Rob Shield active** next to your name in the embed.

---

### `/shopmove` — Reorder Shop Items

A new `/shopmove <item> <position>` command lets staff move any shop item to a specific position in the list without having to remove and re-add it. Requires **Manage Server** permission.

---

### Bank System — `/deposit` & `/withdraw`

Your coin balance is now split into two pockets:
- **Wallet** — at risk from `/rob`
- **Bank** — completely safe; thieves cannot touch it

Use `/deposit <amount>` to move coins into the bank and `/withdraw <amount|all>` to pull them back out. The `/balance` command shows both values plus a combined total.

---

## Session — March 19, 2026

### Custom Voice Channels (`/vc`)

A full custom voice channel system has been added. Members purchase a **Custom VC** from the shop and receive a permanent voice channel they manage themselves using 20 subcommands under a single `/vc` command.

**Key features:**
- VC persists when empty — members buy once and keep it indefinitely
- Owner gets **Priority Speaker** automatically; transfers with `/vc transfer`
- Privacy modes: **public** (anyone can join) or **private** (everyone can see the channel but only guests can join)
- VC-only mute and ban — no server impact whatsoever
- Guestlist and blacklist with per-user Discord permission overwrites
- Admin setup via `/vc setup category: <category>` to control where VCs are created

See the [Custom Voice Channels](custom-vc.md) page for the full command reference.

---

### Voice Time — Weekly Reset Changed to Sunday Midnight EST

The weekly voice time counter now resets every **Sunday at midnight Eastern Time**, replacing the old rolling 7-day window. The reset is DST-aware (adjusts automatically between EST and EDT).

---

### `/vc invite` — Now Adds Member to Channel Permissions

`/vc invite <user>` no longer generates a Discord invite URL. It now adds the specified member directly to the voice channel's Advanced Permissions (granting `ViewChannel` and `Connect`), identical to `/vc add`. The member is also saved to the guestlist so they retain access if the channel is set to private.

---

### `/buy` — Custom VC Naming on Purchase

When buying a **Custom VC** from the shop, members can now set the channel name directly in the buy command using the optional `channel-name` field. If skipped, the channel is named `username's VC`. The name can be changed any time with `/vc name`.

---

### `/shopadd` — Position Option Added

A new optional `position` field on `/shopadd` lets you place new items at a specific slot in the shop list rather than always appending to the end. Example: `position: 5` inserts the item at slot 5 and shifts everything else down.

---

### `/vc setup` — Restricted to Bot Owner

`/vc setup` was previously gated on **Manage Server** permission. It is now restricted to the **bot owner only**, preventing any server administrator from changing the VC category.

---

### `/vc` — Public "No Custom VC" Error for Non-Owners

Members who run any `/vc` command without owning a Custom VC now receive a public embed (visible to everyone in the channel) explaining they need to buy one. The embed shows the price, that no previous tier is required, and reminds them to use `/buy Custom VC` with an optional channel name.

`/vc help`, `/vc host`, and `/vc setup` are unaffected — they work for anyone as before.

---

### `/vc help` — Now Posts Publicly

`/vc help` no longer sends an ephemeral (private) reply. The embed is now posted publicly so everyone in the channel can see it.

---

### `/help` — Custom VC Added as First Category

The **🔊 Custom VC** category has been added to the `/help` dropdown and placed first in the list. The full order is now: Custom VC → Economy → Pets → Fun → Images → Utility → Moderation.

---

### Shop — Footer and Custom VC Description Updated

- Footer wording corrected to "previous **item**" (was "previous tier")
- Custom VC shop description now shows **No previous tier required.** in bold to make it clear it can be purchased at any time without unlocking prior tiers

---

## Session — March 18, 2026

### Command Consolidation (Slash Command Slot Reduction)

Discord limits bots to **100 slash commands**. This session focused on merging related commands under shared parent commands to free up space for future features. The bot went from **95 → 82 commands**, freeing **18 open slots**.

---

### `/post` — Merged announcement commands

**Replaces:** `/update`, `/announce`, `/botupdates`
**Saves:** 2 command slots

All three posting commands have been merged into a single `/post` command with subcommands. The full multi-step flow (channel picker → ping picker → modal) is unchanged for each type.

| Old Command | New Command |
|---|---|
| `/update` | `/post update` |
| `/announce` | `/post announce` |
| `/botupdates` | `/post botupdates` |

**Additional change:** `/post announce` now includes a 🔔 Get Announcement Pings role toggle button on posted embeds, matching the behaviour of `/post update` and `/post botupdates`.

> Existing role toggle buttons on previously posted embeds continue to work — no posts were broken.

---

### `/pet` — Merged pet system commands

**Replaces:** `/petshop`, `/adopt`, `/petstatus`, `/feed`, `/play`, `/petname`, `/release`
**Saves:** 6 command slots

All seven pet commands are now subcommands under `/pet`. All cooldowns, logic, and embeds are identical — only the names changed.

| Old Command | New Command |
|---|---|
| `/petshop` | `/pet shop` |
| `/adopt <pet>` | `/pet adopt <pet>` |
| `/petstatus` | `/pet status` |
| `/feed` | `/pet feed` |
| `/play` | `/pet play` |
| `/petname <name>` | `/pet name <name>` |
| `/release` | `/pet release` |

---

### `/coins` — Merged coin admin commands

**Replaces:** `/addcoins`, `/removecoins`
**Saves:** 1 command slot

| Old Command | New Command | Permission |
|---|---|---|
| `/addcoins <user> <amount>` | `/coins add <user> <amount>` | Bot Owner only |
| `/removecoins <user> <amount>` | `/coins remove <user> <amount>` | Bot Owner only |

> `/coins remove` was also upgraded this session — it was previously ManageGuild permission and is now restricted to bot owner only, matching `/coins add`.

---

### `/warn` — Merged warning commands

**Replaces:** `/warn`, `/warnings`, `/clearwarnings`
**Saves:** 2 command slots

| Old Command | New Command | Permission |
|---|---|---|
| `/warn <user> <reason>` | `/warn add <user> <reason>` | Moderate Members |
| `/warnings <user>` | `/warn view <user>` | Moderate Members |
| `/clearwarnings <user>` | `/warn clear <user>` | Administrator |

---

### `/bot` — Merged bot info commands

**Replaces:** `/botinfo`, `/ping`, `/uptime`
**Saves:** 2 command slots

| Old Command | New Command |
|---|---|
| `/botinfo` | `/bot info` |
| `/ping` | `/bot ping` |
| `/uptime` | `/bot uptime` |

---

### Bug Fix — Announcement ping button

The `/post announce` command was missing the role toggle button that `/post update` and `/post botupdates` had. Added `🔔 Get Announcement Pings` button which toggles the Announcements ping role for the member who clicks it.

---

## Previous Sessions (Summary)

### Command Merges
- `/invites check` + `/invites leaderboard` → `/invites check` + `/invites leaderboard` (merged subcommands)
- `/messages check` + `/messages leaderboard` → merged subcommands
- `/voicetime check` + `/voicetime leaderboard` → merged subcommands
- `/rep check` + `/rep give` → merged subcommands
- `/channel create` + `/channel delete` → merged with confirmation buttons
- `/guess` — merged from separate `guessstart` / `guesstop` into a single `/guess` command

### New Features Added
- **Cockfight PvP mode** — optional `opponent` parameter sends an Accept/Deny challenge to a specific member with a 60-second timeout; coins transfer on resolution
- **Texas Hold'em Poker** — full multiplayer poker with betting rounds, community cards, and a raise modal
- **Horse racing** — four horses with different odds, animated live race in an embed
- **Bank robbery** — multiplayer heist with crew joining via button, shared payout on success
- **Starboard race condition fix** — processing lock prevents duplicate posts when multiple stars arrive simultaneously
- **Voice time on restart** — elapsed VC time is credited correctly when the bot restarts mid-session (`reconcileVC`)
- **`/addvoicetime`** — bot owner command to manually grant voice time to a member
