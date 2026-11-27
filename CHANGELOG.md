# Changelog

Every Botfather2 beta release (0.9.x), newest first. Downloads are on the [Releases page](https://github.com/evony-tech/Botfather2-releases/releases).

## 0.9.7 (2026-11-26)

### New
- **Scripts run the way NeatBot runs them:** `%name%` is filled in once when the script loads, from the `set` lines above it; `print` is `echo`; `$error` is only set when a command fails, starts empty inside a function and comes back after it; a function's variables are its own; calls nest up to 40 deep; `sleep @HHMMSS` works; `json_encode`'s extra arguments leave keys out; lists have NeatBot's `getItemAt`, `contains`, `addItem`, `addItemAt`, `removeItemAt`, `removeAll`, `setItemAt` and `getItemIndex`.
- **Log lines in NeatBot's words:** `Upgrade Sawmill:7 at position 1004 to level 8`, `Research Agriculture to level 5`, `TROOPS: Queued archer:30`; a refusal is its own line (`castle.upgradeBuilding error (-1): ...`); and when the work is done, `Completed upgrading of Sawmill:7 at position 1004 to level 8` / `Completed research of Agriculture to level 5` (or `Cancelled ...`).
- **Incoming attacks** are written in the attacked city's log, red, as NeatBot does: `ATTACK by: <lord>@<alliance> from <city>(x,y) with catapult:6666 in 01m:47 @ 7:51:06 PM, 8 waves`, then each wave of 1000+ troops, repeated every 1-2 minutes while they are on their way.
- **Reports → Report Log:** a running log of the account's army reports (`DEFENSE Plunder Reports, from 8(658,340) to 6(657,340)`, green) and battle results, also shown in the account's Log; **Mailbox** is the report browser as before.

_Restarts the engine: accounts log in again within about a minute._

## 0.9.6 (2026-11-26)

### New
- **The Log and City Log look and work like NeatBot's:** every city's lines also show in the account's Log after a red `(City) - `, the account's own after a blue `(Account) - `; each line in its log category's colour, errors red, `HH:MM:SS` stamps in NeatBot's teal.
- **Holiday waits for every march to come home**, however long that takes (it used to give up after 30 minutes), then clears the cities again and goes on holiday. Problems -- the game refusing with nothing out, a wait past 2 hours, giving up after a day -- are said in **alliance chat**, or posted to the server's **Notices** target (Communications page) when the account has no alliance.
- **Settings → About** has the version, a **Check for updates now** button, what Botfather2 does, the license modules, where your data is kept, and this changelog.
- **Request pacing** moved into the **Engines** card (Settings → Advanced).
- The gold theme is now called **Classic Gold** (nothing else changes).

### Fixes
- **The main window no longer goes blank** on a busy market: it was sent every city's full state over 100 times a second (about 20 MB/s) and crashed, again and again after each reload. Each city now reaches the windows at most once a second; goals and scripts still see every update.

_Restarts only the app window; accounts on a detached engine stay online._

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
