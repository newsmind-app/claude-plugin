---
name: setup
description: First-run help for Newsmind. Use when the user has just installed, connected or signed up, when Newsmind tools return Unauthorized, or when the account has no feeds. Not for reading feeds on an established account.
---

# Connecting Newsmind

Newsmind is a hosted service. The plugin only points Claude Code at it —
there is nothing to install locally and no API key to paste.

## First run

1. Call any Newsmind tool (`get_account_info` is the cheapest). Claude Code
   will open an OAuth sign-in in the browser the first time.
2. If the user has no account, sign-up and a 14-day trial start from that
   same flow at https://newsmind.app — a card is collected, nothing is
   charged during the trial.
3. Once connected, `get_account_info` returns the plan and feed count.

## Getting feeds in — do this before anything else

A brand-new account has **zero feeds**, so "what's new today?" correctly
returns nothing. Don't let that read as the product being broken. Offer the
two routes:

- **Import an OPML file** — `import_opml`. This is the fast path for anyone
  leaving another reader (Feedly, Inoreader, NetNewsWire, Reeder). Ask them
  to export OPML from it and hand you the file.
- **Add feeds one at a time** — `subscribe_to_feed` accepts a feed URL *or*
  a site's homepage, and will discover the feed from the page.

Some sites genuinely have no feed, and some block automated fetching. When
`subscribe_to_feed` declines, relay the reason it gives rather than
retrying — it distinguishes "this page isn't a feed" from "the publisher's
own feed URL is serving a web page", which are different problems.

## Worth mentioning once feeds are in

- `create_watch` saves a standing search; new matches surface on later
  calls without the user re-asking.
- A watch on an ambiguous name ("Brian Shaffer") will match more than one
  person. `require_terms` narrows it — any one term is enough. Don't append
  the word to the query itself: queries match as an exact phrase.
- `get_story_clusters` groups the same story across outlets on a busy day.

## Plans

Pro and Max, both with a 14-day trial. Max adds semantic search, a longer
retention window and higher feed limits. Manage plans at
https://newsmind.app/auth/account.
