# Botfather2

> [!IMPORTANT]
> **This is a beta build (0.9.x).** All of Botfather2's planned features are in, and it is being tested on real fleets before the first full release, **1.0.0**. What that means for you:
> - **It runs real accounts, but expect bugs.** Some features are still being checked against the live game, and a few may behave differently from what you expect.
> - **Updates come often**, usually with fixes. Install them when the app offers them.
> - **Settings and data carry forward.** Your roster, settings and scan history are kept from one beta to the next, and on into 1.0.0.
> - **Report what you find**, with the account's server and roughly when it happened, to whoever gave you access. The app's logs (**Logs** page) help a lot.
> - Start with a few accounts before moving a whole fleet onto a new version.

**Botfather2** runs and manages a whole fleet of Evony accounts from one desktop app. It works without a browser, Flash or a game client: a built-in engine talks to the game servers directly, so a single PC can keep hundreds of accounts online at a time.

This repository holds **installers and updates only**. The source code is private.

---

## Download

Get the latest release from the [**Releases** page](../../releases/latest):

| Platform | File | Notes |
| --- | --- | --- |
| Windows 10/11 (64-bit) | `Botfather2-Setup.exe` | Per-user installer, no admin prompt needed |
| Linux (64-bit) | `Botfather2-<version>.tar.xz` | Portable: extract and run, nothing to install |

Nothing else is needed. The engine and everything it needs are bundled.

### Windows

1. Download and run `Botfather2-Setup.exe`.
2. SmartScreen may warn the first time, because the installer isn't code-signed. Click **More info → Run anyway**.
3. Botfather2 installs for your user only, with Start-menu and desktop shortcuts.

### Linux

```bash
tar -xJf Botfather2-*.tar.xz
cd Botfather2-*/
./botfather2
```

If it stops at start-up with *"The SUID sandbox helper binary was found, but is not configured correctly"*, either give the sandbox helper the permissions it wants:

```bash
sudo chown root:root chrome-sandbox && sudo chmod 4755 chrome-sandbox
```

or run without the sandbox: `./botfather2 --no-sandbox`.

On a minimal Linux install you may also need the usual desktop libraries (`libgtk-3-0`, `libnss3`, `libasound2`, `libgbm1` on Debian/Ubuntu).

---

## Updates

Botfather2 checks this repository for new versions by itself. No GitHub account or token is needed. When an update is available it shows in **Settings → Advanced → Updates**, and installing it is one click.

If you use **detached engines** (below), your accounts can stay logged in while the app updates.

---

## Botfather2 License key

The core of the app is free to use. **Premium modules** need a **Botfather2 License key**.

**Getting a key:** go to **Settings → General → Botfather2 License key**, enter your email and a name for the key, and click **Email me a key**. The key arrives by email; paste it into the same card.

- **One key per computer.** A key locks to the first computer that uses it.
- **One email can hold several keys**, one for each of your computers. Name each key with your game name or the computer's name.
- The key is checked when you save it and then every 15 minutes in the background. No Google account or sign-in is needed.

| Module | What it unlocks |
| --- | --- |
| `market` | The **Markets** page and the scheduled **Market Monitor** scan |
| `map` | The **Map** page and the scheduled **Map Scan** |
| `prestigemonitor` | The scheduled **Player Rank** and **Hero Rank** scans |
| `communications` | The **Communications** page and posting to **Discord / Telegram** webhooks |
| `engine` | Editable **request pacing** and rank-scan page size (otherwise fixed at safe defaults) |
| `mcp` | The **AI agents (MCP)** connection for Claude and other AI tools |

---

## What it does

### Fleet control
- **Roster** of all your accounts, with sortable columns: online status, lord, alliance, prestige, resources, CPU and memory.
- **Import** accounts from Botfather, Director, OPTiC Monitor, or a Flash client's local data. Re-importing updates accounts without losing what live play has filled in.
- **Proxies:** assign proxies per account, or let Botfather2 rotate through a pool.
- **Launch protection:** at most 5 logins a minute per game server and per proxy or IP. This applies to every way an account starts, so a big fleet never floods a server.
- **Keep Alive** starts chosen accounts when the app opens, and restarts them if they drop.
- **Auto Stop** logs other accounts out after a set time. It waits if a script is running or a city is under attack.
- **Auto-reconnect:** after a disconnect, such as someone else logging into the account, the account pauses and logs back in later by itself.
- **Detached engines** (optional, **Settings → Advanced → Engines**): accounts stay online when the app is closed, crashes or updates, and the next start picks them up again without logging in again.

### Account page
Double-click an account to open its page:
- **City tabs** with information panels: resources and production, troops, troop and fortification queues, buildings, valleys, heroes (Feasting Hall and Inn), technology, market trades, marches (recall them), and incoming armies (hostile, reinforcements, transports).
- **Logs:** the account log, each city's own log, decoded game **reports**, alliance, items, statistics and friends.
- **Live chat**, plus **mail** and **packages**.
- **Goals and Scripts** editors.

### Goals
Standing, unattended automation per city: building, research, troops, fortifications, trading, upkeep, valleys, NPCs, heroes, quests and more. Goal sets come in layers: base goals for every account, alliance goals, and each city's own goals. New or captured cities get **New City goals** automatically.

### Scripts
NEAT's script language: variables, expressions, control flow, functions, the game objects (`city`, `cities`…), map searches, and commands for chat, items, quests, marches (attack, scout, transport, reinforce, recall) and more. Scripts keep running when you close the account page.

### Server-wide data
Scheduled scans, set up per server on the **Tasks** page:
- **Markets:** price history and charts, Trading Play, and buying up market dumps.
- **Rankings:** every player, alliance and hero on a server. Prestige changes over 24 hours and 7 days, and when each player was last active.
- **Map:** the whole server map, colored by your diplomacy (yours, allies, neutral, enemies). You can search for players and alliances.
- **Cities** and **Heroes** pages: every city and hero across your fleet in one table.

Every big table is paged, can be sorted by any column, and has **Download CSV** to save exactly what your filters show.

Scan history is kept like this: every scan for 7 days, one scan a day up to 90 days, then one a week.

### Alerts and communications
- **City watch:** warns about low food, attacks and similar problems. Alerts go to your alliance chat or a Discord/Telegram webhook.
- **Chat relay:** forwards world and alliance chat to Discord or Telegram.
- **Maintenance notices:** posts server maintenance announcements to your webhooks.

### AI agents (MCP)
Connect Claude Code, Claude Desktop or any MCP client to read your fleet's state and act on it. The connection is local-only (loopback) and denies by default. You choose which kinds of action (market, items, heroes, city, chat, quests) an agent may take, and on which accounts. Every action is logged.

---

## Your data

- Everything Botfather2 stores stays **on your computer**:
  - **Windows:** `%APPDATA%\Botfather2`
  - **Linux:** `~/.config/Botfather2`
- That folder holds your roster, settings, logs and per-server scan databases.
- Logs keep only what your log settings switch on. Old logs are deleted after the number of days you choose (**Settings → Logs**).
- Botfather2 connects only to:
  - the game servers;
  - this repository, to check for updates;
  - the license server, which receives your key and an anonymous ID for your computer;
  - any Discord/Telegram webhooks you set up yourself.

---

## Versions

Botfather2 is in **beta**: versions are `0.9.x` until the first full release, `1.0.0`. Each release's notes on the [Releases page](../../releases) list what changed.

Settings → Advanced → **Engines** sets how many accounts one engine process hosts (25 by default). It also shows this computer's memory and CPU, and roughly how many more accounts would fit.
