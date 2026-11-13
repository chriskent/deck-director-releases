---
title: Version history
nav_order: 9
---

# Version history

Downloads for every version are on the [Releases page](https://github.com/chriskent/deck-director-releases/releases).

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
