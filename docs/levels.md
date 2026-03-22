# ⭐ Levels & XP

The bot tracks XP for every message you send and rewards you with levels as you earn more. Server Boosters earn bonus XP on every message.

---

## How XP Works

| Setting | Value |
|---|---|
| XP per message | 15–25 (random each message) |
| Cooldown | 60 seconds — only one XP grant per minute per user |
| Booster bonus | +15% XP on every message for Server Boosters |
| Level formula | `level = floor(sqrt(total_xp / 100))` |

XP scales so that each level requires progressively more effort:

| Level | Total XP required |
|---|---|
| 1 | 100 XP |
| 2 | 400 XP |
| 3 | 900 XP |
| 5 | 2,500 XP |
| 10 | 10,000 XP |
| 15 | 22,500 XP |

---

## Level-Up Announcements

When you level up, the bot posts an announcement in the same channel you messaged in. The embed shows your new level, how much XP you just earned, and your progress toward the next level. If you're a Server Booster, the embed also notes your bonus XP.

---

## Commands

### `/rank [user]`

View your level card — or check someone else's. Shows:
- Your **rank** on the server (#1, #2, etc.)
- Your current **level**
- Your total **XP**
- A `▓▓▓▓▓░░░░░` progress bar showing how far through the current level you are
- <:boosters:1481418598059737118> **Server Booster** badge and +15% note if applicable

### `/lbrank`

See the top 10 members on the server sorted by XP, with their level shown alongside. Top 3 get 🥇🥈🥉 medals.

---

## Server Booster Bonus

Members with the Server Booster role earn **+15% XP** on every message. The bonus is shown with the <:boosters:1481418598059737118> emoji in:

- `/rank` — shown under the progress bar
- Level-up announcements — noted in the embed description
- `/profile` — shown next to the progress bar in the Level & XP section

---

## XP on Your Profile

`/profile` shows a **Level & XP** section at the top of the embed with your current level, total XP, and progress bar — plus the booster badge if you're boosting.
