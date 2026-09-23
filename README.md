# Torn Player Search

An advanced player search for [Torn City](https://www.torn.com), built on the official Torn API v2 Hall of Fame and player profile endpoints.

**Live:** https://geotehnub.github.io/torn-player-search/

## Features

- **Scan the Hall of Fame** by any category (Networth, Level, Awards, Working stats, …), or use **Level band** mode to jump straight to your level range with a binary search.
- **Free filters** from HoF data (no extra API calls): level, time since last action, account age, faction, name, networth.
- **Detailed lookup** (1 call per player, cached): job / company type, position, company stars, current status, donator, property.
- **Battle stat estimates**: a free rank-based bracket (the TornTools method: rank minus level/crimes/networth triggers), plus optional [FFScouter](https://ffscouter.com/) estimates and Fair Fight (205 players per request) for your registered key. Filter by estimated stats and FF.
- **Watchlist** with notes, hide players, import/export.
- **Saved presets** and one-click quick filters (Active < 24h, Inactive 30d+, Factionless, Networth ≥ 1b, …).
- Faction name resolution, quick links (attack, message, trade, bazaar, add friend), CSV export, copy IDs, column toggles.
- Results, lookups and settings persist between visits. "Continue" resumes a scan where it stopped.
- Shortcuts: `Ctrl+Enter` scan · `Esc` stop · `/` focus name filter.

## API key & Torn API ToS

| | |
|---|---|
| **Data storage** | Only in your own browser (localStorage + IndexedDB). There is no server. |
| **Data sharing** | None. The page only talks to `api.torn.com` (and `ffscouter.com` if you opt in). |
| **Purpose of use** | Personal player search over public Hall of Fame / profile data. |
| **Key storage & sharing** | Stored locally in your browser only if you tick "Remember". Sent only to Torn's API (and FFScouter, if you use it). |
| **Key access level** | **Public** is enough. Please use a Public key. |
| **FFScouter (optional)** | Only if you enter an FFScouter key: that key and the relevant player IDs are sent to ffscouter.com under their Data Policy & Terms. |

Rate limiting: the tool never makes more than your chosen budget of calls in any 60-second window (default 80/min, hard cap 100/min, Torn's per-user limit). It backs off on "too many requests" and stops and forgets the key on invalid-key errors.

## Running locally

It's a single static file. Open `index.html` in a browser.
