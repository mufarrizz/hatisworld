# 🏆 Hati's World — World Cup Predictions

A single-file browser app for betting imaginary coins on the 2026 FIFA World Cup. No server, no install — just open the HTML file and play.

---

## Getting Started

1. Download `hatis_worldcup_predictions.html`
2. Open it in any modern browser (Chrome, Firefox, Edge, Safari)
3. Register an account, pick your flag, and start betting

That's it. No internet connection required after the file is loaded.

---

## Features

- **Real 2026 World Cup schedule** — all 72 group stage matches across Groups A–L, plus Round of 32, Round of 16, Quarter-Finals, Semi-Finals, and the Final
- **Live match status** — matches automatically lock for betting once kickoff time passes
- **Imaginary coin betting** — every new account starts with 🪙 1,000 coins
- **Odds & payouts** — each match has home/draw/away odds; your payout is `stake × odds`
- **Leaderboard** — see everyone ranked by coin balance
- **Simulate tab** — manually set match results to trigger payouts for all winning bets
- **Persistent login** — the app remembers who you are across page reloads; no need to log in every time
- **Multi-user** — multiple people can create accounts in the same browser (data is shared via localStorage)

---

## How Betting Works

1. Go to the **⚽ Predict** tab
2. Click a team (or Draw) on any open match
3. Enter your stake in the amount box, or use the chip shortcuts (100 / 250 / 500 / ½ / All-in)
4. Hit **Bet 🎯** to confirm

Once a match kicks off, betting closes automatically and the card moves to the **Betting Closed** section. When you win, your payout is added to your balance automatically when an admin sets the result.

---

## Match Sections

| Section | What it means |
|---|---|
| **Upcoming Matches** | Kickoff hasn't happened yet — betting is open |
| **Betting Closed** | Match has started but no result set yet |
| **Settled Matches** | Result has been entered; winners paid out |

---

## Admin / Simulate Tab

The **⚙️ Simulate** tab lets anyone set match results. When a result is set:

- All users who picked the winning side receive their payout automatically
- Losers forfeit their stake
- Results can be reset (but payouts already issued are **not** reversed)

There's no admin password — this is a friends-only app built on trust.

---

## Data & Storage

All data lives in your browser's `localStorage` under the key `hati_wc_v2`. This means:

- Data is **per browser** — switching browsers or devices means a fresh start
- Clearing browser data / site data will wipe everything
- If you want to share a league with friends, everyone needs to use the **same browser on the same device**, or the host device needs to be accessible to all players

No data is ever sent to any server.

---

## Match Data

The app ships with the full **2026 FIFA World Cup** group stage (72 matches) covering all 12 groups:

| Group | Teams |
|---|---|
| A | Mexico, South Korea, Czechia, South Africa |
| B | Canada, Switzerland, Qatar, Bosnia & Herz. |
| C | Brazil, Morocco, Haiti, Scotland |
| D | USA, Australia, Paraguay, Türkiye |
| E | Germany, Ivory Coast, Ecuador, Curaçao |
| F | Netherlands, Japan, Sweden, Tunisia |
| G | Belgium, Iran, New Zealand, Egypt |
| H | Spain, Uruguay, Saudi Arabia, Cape Verde |
| I | France, Senegal, Norway, Iraq |
| J | Argentina, Austria, Algeria, Jordan |
| K | Portugal, Colombia, DR Congo, Uzbekistan |
| L | England, Croatia, Ghana, Panama |

Plus placeholder slots for all knockout rounds (Round of 32 → Final) that can be bet on as TBD matchups.

---

## Tips

- **Early bets = best odds** — odds aren't dynamic, so bet before the crowd figures out the favourite
- **All-in on underdogs** — upsets happen; a 🪙 100 bet on Scotland beating Brazil pays 🪙 600
- **Check the Simulate tab** — if a result hasn't been set after a match finishes, bug whoever runs the app
- **Leaderboard resets** only if someone manually clears localStorage — your coins are safe otherwise

---

## Technical Notes

- Pure HTML/CSS/JS — zero dependencies, zero build steps
- Uses `localStorage` for persistence (5MB limit; more than enough for hundreds of users and bets)
- Session is remembered via a separate `hati_wc_session` key so you stay logged in across reloads
- Timestamps are in UTC milliseconds; match expiry is checked client-side against `Date.now()`
- The file is fully self-contained — CSS, JS, and all data are embedded inline
