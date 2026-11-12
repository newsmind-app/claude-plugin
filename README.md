# Newsmind — RSS for your AI

Your own RSS and Atom feeds, readable by Claude. Ask what's new since you
last looked, find the article you half-remember, see the same story across
every outlet that ran it, and leave standing watches that surface new
matches without you asking again.

Works in Claude chat on the web, desktop and mobile, in Cowork, and in
Claude Code.

## What you can do with it

- **Catch up** — "what's new in my feeds?" returns what arrived since this
  connection last asked, so nothing repeats and nothing is missed.
- **See the story, not the headlines** — on a busy day, the same event
  arrives from a dozen outlets. Newsmind groups them.
- **Search** — by keyword across everything you follow, or by meaning on
  Max, which finds the article that never used your words.
- **Watch a topic** — a saved search that keeps matching after the
  conversation ends, delivered in-session or by email.
- **Bring your feeds with you** — import an OPML export from any reader,
  and export one whenever you want. Paste a homepage and Newsmind finds
  the feed itself.

## Install

In claude.ai or the desktop app, **Customize > Plugins > Discover**. In
Claude Code:

```
/plugin install newsmind
```

On first use Claude opens an OAuth sign-in at newsmind.app. Newsmind is a
paid service with a 14-day trial; a card is collected at sign-up and
nothing is charged during the trial.

## What's in this repository

Configuration only. It declares Newsmind's remote MCP server and ships
two skills. It installs no software and runs no code on your machine:
no hooks, no agents, no `bin/`, no local server.

```
.claude-plugin/plugin.json   manifest
.mcp.json                    points at https://newsmind.app/mcp
skills/setup/                connecting, and getting the first feeds in
skills/feed-housekeeping/    adding, organising and diagnosing feeds
```

## Authentication

OAuth 2.0 with dynamic client registration. The plugin holds no
credentials and this repository contains no secrets.

## Privacy

Newsmind stores your feed subscriptions and the articles it fetches on
your behalf. Full policy: https://newsmind.app/privacy

## Support

support@newsmind.app · https://newsmind.app/install

## Licence

MIT — see [LICENSE](LICENSE). Applies to this configuration wrapper. The
Newsmind service itself is proprietary and governed by
https://newsmind.app/terms
