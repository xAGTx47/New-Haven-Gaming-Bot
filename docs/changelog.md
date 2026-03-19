# New Haven Gaming Bot — Changelog

---

## Session — March 19, 2026 (continued)

### Music — Audio Bleed Between Songs Fixed

Brief clips of the next queued song could be heard while the current song was still playing. The root cause was the audio player's `maxMissedFrames` threshold being set to the library default of **5 frames (100ms)**. Any brief yt-dlp or FFmpeg pipeline hiccup longer than 100ms — a network round-trip, a codec flush, a short buffer stall — would trigger the end-of-song logic mid-track, starting the next queued song prematurely.

**Fixes applied:**
- `maxMissedFrames` raised from 5 (100ms) to **250 (5 seconds)** — brief pipeline hiccups no longer cause premature song advancement
- `/skip` now **force-stops** the player (`stop(true)`) and immediately kills the yt-dlp process, eliminating any residual audio in the transition gap between songs

---

### Music — `/help` Tab Added

A **🎵 Music** category has been added to the `/help` dropdown, placed between Images and Utility. All 12 music commands are listed with descriptions:

`/play`, `/pause`, `/resume`, `/skip`, `/stop`, `/queue`, `/nowplaying`, `/loop`, `/volume`, `/seek`, `/remove`, `/shuffle`

---

### Music System — Now Working (Voice Connection Fixed)

The music system is now fully functional. The root cause of the voice connection failure was `@discordjs/voice` using **voice protocol v4** (version 0.18.x), which produced a WebSocket handshake timing issue on Replit's network — the bot sent `Identify` before Discord's voice server could send `Hello`, causing the connection to be rejected immediately.

**Fix:** Upgraded `@discordjs/voice` from 0.18.0 to **0.19.2**, which uses voice protocol **v8**. The handshake now completes cleanly on the first attempt.

**Additional fix:** The dev bot (running in the Replit workspace) and the deployed bot were both active at the same time. Since both share the same token and user ID, they were competing for the same Discord voice sessions, invalidating each other's connections (Discord close code 4006). The dev workflow has been permanently disabled (`echo bot-disabled`, `autoStart: false`) so only the deployed bot runs.

**Confirmed working:**
- Voice connects on the first try every time
- YouTube search queries and direct URLs both play
- Queue, loop, skip, volume, and all other music commands function correctly
- Bot stays in the voice channel after the queue empties

See the [Music](music.md) page for the full command reference.

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
