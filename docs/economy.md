# 💰 Economy Commands

![Economy Banner](images/economy-banner.png)

Commands for earning, spending, and managing coins.

---

## Passive Income

| Command | Cooldown | Description |
|---|---|---|
| `/daily` | 24 hours | Claim your daily coins — streak bonuses increase the payout the longer you keep your streak |
| `/weekly` | 7 days | Claim a larger weekly coin reward |
| `/monthly` | 30 days | Claim the biggest passive coin reward |
| `/beg` | None | Beg for a small random amount of coins |
| `/work` | Cooldown applies | Work a shift for a steady coin payout |
| `/crime` | Cooldown applies | Attempt a crime — higher reward but risk losing coins if caught |

---

## Gathering

Gathering commands produce items that sit in your inventory until you sell them.

| Command | Description |
|---|---|
| `/fish` | Go fishing — catch common, rare, or legendary fish |
| `/hunt` | Hunt animals in the woods |
| `/mine` | Mine for ores and gems |
| `/sell <item>` | Sell a single gathered item for coins |
| `/sellall` | Sell every gathered item in your inventory at once |

---

## Wallet & Bank

Your coins are split across two places:

- **Wallet** — coins here are at risk of being stolen via `/rob`
- **Bank** — coins here are completely safe from robbery

| Command | Description |
|---|---|
| `/balance` | Check your own wallet, bank, and total balance — also shows if you have a Rob Shield active |
| `/deposit <amount>` | Move coins from your wallet into your bank |
| `/withdraw <amount\|all>` | Move coins from your bank back to your wallet |
| `/inventory [user]` | View your inventory, or another member's |
| `/give <user> <amount>` | Send coins directly to another member |
| `/giveitem <user> <item>` | Give an inventory item to another member |
| `/leaderboard` | See who has the most coins on the server |

---

## Shop

| Command | Description |
|---|---|
| `/shop` | Browse the server shop |
| `/buy <item> [channel-name]` | Purchase an item from the shop — it goes into your inventory. When buying a Custom VC, the optional `channel-name` field sets the VC's name |

> **Custom VC** is a special shop item. Buying it instantly creates a permanent voice channel assigned to you. See [Custom Voice Channels](custom-vc.md) for full details.

### Shop Items

| Item | Price | Effect |
|---|---|---|
| Rob Shield | 🪙 500 | Automatically blocks the next `/rob` attempt against you. Consumed when triggered. Shows on `/balance`. |
| Lockpick | 🪙 600 | Use with `/rob lockpick:true` to bypass a target's Rob Shield. Consumed on use. |
| Spy | 🪙 250 | Use `/spy <user>` to secretly check someone's wallet balance. Result is only visible to you. Consumed on use. |

---

## Robbery

| Command | Description |
|---|---|
| `/rob <user> [lockpick]` | Attempt to steal 100–500 coins from another member's **wallet** — 50/50 chance of success. Set `lockpick:true` to use a Lockpick and bypass their Rob Shield if they have one. |
| `/spy <user>` | Secretly check someone's wallet balance (requires a **Spy** item — consumed on use). Only you can see the result. |
| `/roblb` | View the robbery leaderboard — top robbers ranked by total coins stolen, and most robbed victims. |

### How robbery works

1. **Target's wallet must have at least 100 coins** — bank coins are completely safe
2. **50% win / 50% fail:**
   - **Win** → steal 100–500 coins from their wallet; victim is DM'd
   - **Fail** → you pay the victim 100–300 coins in compensation, and you go to **jail** for 15–30 minutes
3. **Rob Shield** — if the target has a Rob Shield in their inventory, it automatically blocks the rob and is consumed. You can bypass it by spending a **Lockpick** (`/rob lockpick:true`)
4. **Jail** — while in jail you cannot use: `/rob`, `/crime`, `/bankrob`, `/work`, `/daily`, `/weekly`, `/monthly`, `/beg`, `/fish`, `/hunt`, `/mine`, `/sell`, `/sellall`, or any gambling command. `/balance`, `/deposit`, `/withdraw`, `/shop`, and `/buy` still work.
5. **DM notifications** — the victim always receives a DM: when robbed, when their shield blocks an attempt, or when a robber fails and pays them

---

## Games & Gambling

| Command | Description |
|---|---|
| `/cointoss <side> <bet>` | Bet on heads or tails — 50/50 chance |
| `/highlow` | Guess whether the next number is higher or lower — match exactly for the jackpot. Only you can click your own game's buttons |
| `/gamble <amount>` | Pure luck gamble — random multiplier applied to your bet |
| `/slots <bet>` | Spin the slot machine |
| `/blackjack <bet>` | Play a hand of blackjack against the dealer |
| `/cockfight <bet> [opponent]` | Enter your chicken in a fight. Leave opponent blank for a solo fight, or tag a member to challenge them directly — they must accept via button within 60 seconds |
| `/horse <horse> <bet>` | Pick one of four horses and watch a live animated race. Higher odds = bigger payout |
| `/bankrob <bet>` | Start a crew bank robbery — other members join via button, the crew shares the payout if successful |
| `/poker <buyin>` | Start a multiplayer Texas Hold'em game — other members can buy in and join |
