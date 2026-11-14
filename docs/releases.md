---
title: Version history
nav_order: 9
---

# Version history

Downloads for every version are on the [Releases page](https://github.com/chriskent/deck-director-releases/releases).

## 1.1.1

- The Adopt Profile key shows how many of the 50 slots are in use, e.g. "6/50 used", or "0 free" when they're all taken.
- Its settings show in use, free and total, with a tick box to hide the count on the key.
- The key's text sits higher, clear of the deck's edge.

## 1.1.0

- **50 adoption slots, shared across all your decks.** Before, each deck type had 10 of its own; now any mix works, such as 30 on a Stream Deck + XL and 20 on a Virtual Stream Deck. Profiles you've already adopted carry on as they are.
- The adopt tool's list shows how many of the 50 are in use.

## 1.0.1

The first release from GitHub. The same features as 1.0.0, plus:

- An update check: `ping` and the test tool's `list` say when a newer version is available. Turn it off with `"updateCheck": false` in `config.json`.
- `ping` replies include the version number.

## 1.0.0

The first public release.

- Go to a page by name or number, or step to the next or previous page, wrapping round.
- Back follows a breadcrumb as many levels deep as you go; Previous retraces your exact path.
- Home returns to the page with the Set Home Page key.
- Choose the deck and profile in the message, in any order, or send JSON.
- Three keys: Go To Page, Set Home Page and Adopt Profile.
- Adopt up to 10 of your own profiles per deck type: Stream Deck + XL, XL, +, Virtual and Mobile. Smart Profiles keep working.
- Send a test message tool in the Start menu.
- Port 41555 (test builds used 50555).
