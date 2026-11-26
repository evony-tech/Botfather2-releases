# Changelog

Every Botfather2 beta release (0.9.x), newest first. Downloads are on the [Releases page](https://github.com/evony-tech/Botfather2-releases/releases).

## 0.9.5 (2026-11-26)

### New
- **Holiday button** (account page, was Prepare for Holiday): one click pauses the account, recalls every march and cancels queues and trades in every city, then puts the account on holiday for 2 days, renewing until the coins run out. While the game still refuses (marches on their way home), it clears again and retries every minute for up to 30 minutes.
- **Feasting Hall** looks like NeatBot's: rows colored by the hero's status, and a **Recall** button for heroes out marching or defending.

### Fixes
- The console's `holiday` command works (it always said "the account's player id is not known"). `holiday` alone is 2 days, renewing; add a number for more days, or `/once` not to renew.

_Restarts the engine: accounts log in again within about a minute._

## 0.9.4 (2026-11-25)

### New
- **Logging works like NeatBot:** one list of NeatBot's log categories, switched per city in its Debug panel (the ladybug), with per-account and fleet-wide defaults. A kind of line that's off isn't logged anywhere. Errors, warnings and connection lines always show.
- **Goal set names:** the goals every account runs first are **Prepends**; each alliance's own set is **Alliance prepends**.
- **Goal editor:** a little smaller; clicking outside it cancels (asking first if you changed something).

### Fixes
- **Windows: no separate .NET install needed.** The engine carries its own runtime; without .NET 8, earlier versions showed "Throttled. Launching in 0:00" and never started an account.

_Restarts the engine: accounts log in again within about a minute._

## 0.9.3 (2026-11-25)

### New
- **NeatBot's own icons** on the account page: green pause / red play, refresh, settings and the city toolbar.
- **Big goal editor** with line numbers (Ctrl+S saves, Esc cancels), and **Current goals**: everything a city runs, in order, plus any goals a script loaded.
- Stopping an account by hand, and switching Keep Alive or Autopilot, show in its log.

_Restarts only the app window; accounts on a detached engine stay online._

## 0.9.2 (2026-11-25)

### Fixes
- **Even less disk writing:** the roster is saved at most once a minute (and always when you quit or back it up).

_Restarts only the app window; accounts on a detached engine stay online._

## 0.9.1 (2026-11-25)

### Fixes
- **Much less disk writing:** the roster is no longer rewritten in full on every change.

_Restarts only the app window; accounts on a detached engine stay online._

## 0.9.0 (2026-11-25)

### New
- **The first beta.** All of Botfather2's planned features are in, tested on real fleets before 1.0.0.
- **Accounts per engine** (Settings → Advanced → Engines): 1 to 250 (25 by default), with this computer's memory and CPU and roughly how many more accounts would fit.

### Fixes
- Much less disk writing and CPU while the market is busy: each city's cache file is saved at most every 10 seconds.

_Restarts the engine: accounts log in again within about a minute._
