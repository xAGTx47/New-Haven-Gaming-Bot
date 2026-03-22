# 🔧 Utility Commands

![Utility Banner](images/utility-banner.png)

Server information, member stat tracking, and the XP leaderboard.

---

## Bot Info

| Command | Description |
|---|---|
| `/bot info` | Display bot information — version, server count, uptime, and more |
| `/bot ping` | Check the bot's current latency to Discord |
| `/bot uptime` | See how long the bot has been continuously online |
| `/help` | Open the interactive help menu — browse all command categories |

---

## Server & Member Info

| Command | Description |
|---|---|
| `/serverinfo` | Display information about the server — member count, creation date, boosts, and more |
| `/userinfo [user]` | Display detailed info about a member — join date, roles, and account age |
| `/profile [user]` | View a member's full server profile — **Level & XP** at the top, then coins, reputation, voice time, messages, and invite count |

---

## Levels & XP

| Command | Description |
|---|---|
| `/rank [user]` | View a member's level, XP, rank on the server, and progress bar to the next level. Shows Server Booster bonus if applicable |
| `/lbrank` | See the top 10 members sorted by XP — includes their level. Top 3 get medals |

> See the [Levels & XP](levels.md) page for full details on how XP and levels work.

---

## Invite Tracking

| Command | Description |
|---|---|
| `/invites check [user]` | Check how many members a user has invited. Defaults to yourself |
| `/lbinvite` | See the top inviters on the server |

---

## Message Tracking

| Command | Description |
|---|---|
| `/messages check [user]` | Check how many messages a user has sent. Defaults to yourself |
| `/lbmsg` | See who has sent the most messages on the server |

---

## Voice Time Tracking

| Command | Description |
|---|---|
| `/voicetime check [user]` | Check a member's total time in voice channels. Defaults to yourself |
| `/lbvc` | See who has spent the most time in voice channels |

> Weekly voice time resets every **Sunday at midnight Eastern Time** (automatically adjusts for daylight saving).

---

## Reputation

| Command | Description |
|---|---|
| `/rep check [user]` | Check a user's reputation score. Defaults to yourself |
| `/rep give <user>` | Give your daily reputation point to a member — resets every 24 hours |
