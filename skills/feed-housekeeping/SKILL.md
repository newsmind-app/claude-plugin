---
name: feed-housekeeping
description: Add, remove, organise or diagnose feeds on an account that already has some — adding a site, folders, a feed that stopped updating, OPML export. For a new or unconnected account, use setup.
---

# Keeping the feed list in order

## Adding

`subscribe_to_feed` takes `url` and accepts a site's homepage, not only a
feed URL — it discovers the feed from the page. Pass `folder` to file it on
the way in.

When it declines, relay the reason it gives instead of retrying. It
distinguishes "this page carries no feed" from "the publisher's own feed URL
is serving a web page" from a publisher that blocks automated fetching, and
those need different answers from the user. Some sites simply have no feed.

`import_opml` takes an OPML document for a bulk move; `get_import_status`
reports how it is going, since a large import continues after the call
returns.

## Organising

`move_feed_to_folder` moves one feed by `feed_id`, or accepts `opml` to
restructure in bulk. `get_feeds` lists what exists, `get_feed` details one,
and `get_articles_by_feed` shows what a single feed has carried lately —
useful when the user asks "is this one worth keeping?"

## When a feed goes quiet

`get_feed_health` is the diagnosis tool. Filter with `status` to see only
the failing ones, or pass `feed_id` for a single feed.

Report what it says plainly. A feed failing at the publisher's end is not
something the user can fix, and telling them it is "being checked" is more
honest than implying they misconfigured something. If it looks like a
problem on Newsmind's side, `report_issue` sends it to the operator —
confirm with the user before you file one, and tell them it was filed.

## Leaving and exporting

`export_opml` produces a portable OPML file of everything they follow. Offer
it freely: it is their data, and a reader people can leave is a reader worth
staying with. `unsubscribe_from_feed` removes one feed.

`get_account_info` shows plan, feed count and limits — Pro holds 1,000
feeds, Max 2,500 — and is the right call before telling someone they are
near a cap.
