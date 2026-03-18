# New Haven Gaming Bot — Changelog

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
