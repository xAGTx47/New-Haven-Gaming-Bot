# Getting Started

> **New Haven Gaming Bot** is a fully custom Discord bot built exclusively for the New Haven Gaming server. It covers economy, pets, fun, moderation, and automatic server tracking — all in one place.

---

## Ping Roles

The server has three opt-in ping roles. You can toggle each one yourself by clicking the button on any relevant post — no need to ask a mod.

| Role | What it's for | How to get it |
|---|---|---|
| **Updates** | Server updates, rule changes, important news | Click 🔔 Get Update Pings on any update post |
| **Announcements** | General announcements and events | Click 🔔 Get Announcement Pings on any announcement |
| **Bot Updates** | New bot features, changes, and fixes | Click 🔔 Get Bot Update Pings on any bot update post |

Clicking the button again removes the role. It works as a toggle — you're always in control.

---

## Economy System

The economy system revolves around a server coin currency. Here's how it works at a high level.

### Earning Coins

There are several reliable ways to earn coins every day:

- **`/daily`** — Your main income source. Claim every 24 hours. Maintaining a streak rewards bonus coins — the longer you keep it going, the more you earn.
- **`/weekly`** — A larger payout once a week.
- **`/monthly`** — The biggest passive reward, claimable once a month.
- **`/work`** — Work a shift for a steady payout with a short cooldown.
- **`/beg`** — Small random amount, no cooldown.
- **`/crime`** — Higher risk, higher reward. You can lose coins if caught.

### Gathering & Selling

Three gathering activities produce items you can sell:

- **`/fish`** — Catches fish of varying rarity (Common, Rare, Legendary, etc.)
- **`/hunt`** — Hunts animals in the woods
- **`/mine`** — Mines ores and gems

Once you have items, sell them with `/sell <item>` or dump everything at once with `/sellall`. Items sit in your `/inventory` until you sell them.

### Gambling & Games

Several commands let you wager coins for a chance at bigger rewards:

| Command | Risk level |
|---|---|
| `/cointoss` | 50/50 |
| `/gamble` | Random multiplier |
| `/highlow` | Low risk, jackpot on exact match |
| `/slots` | Slot machine odds |
| `/blackjack` | Skill-based card game |
| `/cockfight` | 50/50 or challenge a member |
| `/horse` | Pick a horse, higher odds = bigger payout |
| `/bankrob` | Multiplayer heist — crew shares the reward |
| `/poker` | Multiplayer Texas Hold'em |

### Spending Coins

- **`/shop`** — Browse what's available to buy on the server
- **`/buy <item>`** — Purchase an item; it goes into your `/inventory`
- **`/give <user> <amount>`** — Send coins directly to another member
- **`/giveitem <user> <item>`** — Give an inventory item to someone

### Checking Your Balance

- **`/balance`** — Your current coin count
- **`/leaderboard`** — See where you rank on the server

---

## Pet System

You can adopt one companion pet at a time. Pets have stats that change based on how well you care for them.

### Adopting a Pet
Browse available pets with `/pet shop` and adopt one with `/pet adopt`. Each pet costs a set number of coins.

### Caring for Your Pet
- **`/pet feed`** — Keep your pet's hunger up. Available every **4 hours**.
- **`/pet play`** — Boost your pet's happiness. Available every **6 hours**.

Neglecting your pet will lower its mood over time. Check its current state anytime with `/pet status`.

### Other Actions
- **`/pet name <name>`** — Give your pet a custom name
- **`/pet release`** — Release your pet for a partial coin refund

---

## Tracking Systems

The bot automatically tracks several stats for every member — no setup needed.

### Voice Time
Time spent in voice channels is tracked in the background. Accumulating enough VC time earns you voice levels. Check your stats with `/voicetime check` and see the top members with `/voicetime leaderboard`.

### Message Count
Every message you send in the server is counted. View your total with `/messages check` and compare with the server with `/messages leaderboard`.

### Invites
When a new member joins using your invite link, you get credit. See your invite count with `/invites check` and the top inviters with `/invites leaderboard`.

### Reputation
Once per day you can give a reputation point to any member with `/rep give <user>`. Check anyone's rep score with `/rep check`. Rep is a way to recognise helpful or positive members.

### Profile
`/profile [user]` pulls all tracking stats together into one embed — coins, rep, VC time, voice level, messages sent, and invite count — for a full picture of any member's activity on the server.

---

## Starboard

When a message receives enough ⭐ reactions, it gets automatically reposted in the starboard channel. The star threshold and target channel are configured by staff using `/starboard set`.
