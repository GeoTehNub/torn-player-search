# Torn Mug Finder

Find players worth mugging in [Torn City](https://www.torn.com): people who just made sales and probably haven't banked the cash yet, and whom you can actually beat.

**Live:** https://geotehnub.github.io/torn-player-search/

## How it works

A mug takes a cut (about 5–10%) of the cash a player is **carrying**, so no public data shows a wallet directly. The tool looks for the next best thing: fresh income that hasn't been banked.

1. **Find players** from one of five sources:
   - players active right now (Torn's user search, 25 per call)
   - this week's top-earning and busiest bazaars (1 call, up to 80 sellers)
   - everyone in your level range (Level Hall of Fame)
   - the richest players (Net worth Hall of Fame)
   - a faction's members (about 100 per call)
2. **Check them.** One call per player covers status, job, bazaar and dated trading stats (bazaar, item market, points, auctions, trades). Players who sold in the last week get one extra call for their weekly sales amount.
3. **Mug score (0–100).** It combines how recent their last sale was, this week's bazaar and item market revenue, whether their bazaar is open, whether they're idle, 7★ Clothing Store mug protection (−75%), and your chance of winning (FFScouter Fair Fight, or a rank-based stat estimate).
4. **See how rich they are.** Sort by net worth, lifetime bazaar income and lifetime item market income (from their personal stats), or filter by them. The stats button on each row opens their full public stats: money and trading, spending (rehab fees, refills, bounties), other income, toughness and activity.
5. **Watch the best.** Star players and press *Start watching*. They're re-checked about every 30 s while the page is open. You're alerted (sound and optional desktop notification) when their bazaar stock drops or they become attackable. Alerts only link to the attack page; you always click it yourself.

## Torn API ToS

| | |
|---|---|
| **Data storage** | Your data stays in your own browser (localStorage + IndexedDB). The only thing stored on a server is donated keys (see below). |
| **Data sharing** | None. The page talks to `api.torn.com` (and `ffscouter.com` if you use Fair Fight). |
| **Purpose of use** | Personal gain: finding mugging targets from public data. |
| **Key storage & sharing** | Stored locally in your browser only if you tick "Remember". Sent only to Torn's API (and FFScouter, if you use it). |
| **Shared keys** | When you save a key with *Share my key* ticked (the default), a **Public Only** key is donated to the site's key pool server (a Cloudflare Worker). There it's used to make public lookups for visitors who have no key, up to 50 calls/min per visitor. It's never shown to anyone. Untick the box to withdraw it, or delete the key in Torn. Limited and Full keys are never shared. |
| **Key access level** | **Public** is enough. Please use a Public key. |

Rate limiting: the tool never makes more than your chosen budget of calls in any 60-second window (default 80/min, hard cap 100/min, Torn's per-user limit). Watching uses at most half of that budget. It never fetches torn.com pages, never opens the attack page and never attacks on its own.

## Shared keys

Visitors without a key make their calls through the key pool server, which rotates through the donated keys. It skips a key for a minute when it hits Torn's rate limit, drops keys Torn rejects, and re-checks every key daily. It only allows the public lookups the site uses. The server code lives in a private repo.

## Running locally

It's a single static file. Open `index.html` in a browser.
