---
title: Version history
nav_order: 11
---

# Version history

Downloads for every version are on the [Releases page](https://github.com/chriskent/deck-director-releases/releases).

## 1.4.1

- Auto Pages has the same look as the Deck Director Console: the same status pills, deck cards, tables, switches and fields.

## 1.4.0

- New: **[Auto Pages](auto-pages.md)** follows your flight in Microsoft Flight Simulator and switches your Stream Deck to the page for each stage (Startup, Taxi, Takeoff, Cruise, Approach, Landing, Shutdown). Start it from the Start menu: Deck Director → Deck Director Auto Pages.
- Faster: the `list` message answers in under a tenth of a second (it used to take 1–2 seconds).

## 1.3.0

- Profiles on the 15-key **Stream Deck** (original, MK.2 and Scissor Keys), **Stream Deck Mini** and **Stream Deck Neo** can be adopted and switched.
- Deck Director Console: each deck shows its model number beside its name.

## 1.2.3

- Fixed: profiles on a newer revision of the Stream Deck XL (model `20GAT9902`) showed as unsupported and couldn't be adopted. Every revision of the XL, Stream Deck + and Stream Deck + XL is now recognised.

## 1.2.2

- Console message builder: **Include** tick boxes beside Device and Profile, so either can be chosen to list pages but left out of the message.

## 1.2.1

- The Deck Director Console has Flight Sim Manager's look: dark surfaces with the amber accent, Roboto, Material icons and buttons, and coloured status pills.

## 1.2.0

- **Deck Director Console**, a new Start menu tool: see whether Deck Director is answering, every deck and its profiles with adopt switches, with a wildcard filter on each deck, and a message builder that copies or sends the message it builds.

## 1.1.3

- Go To Page keys have a **Profile** setting: pick any adopted profile, and the Page list shows its pages.
- A key aimed at another profile no longer shows a false "has no page" warning.

## 1.1.2

- Deck Director remembers which profile each deck was showing, so after a restart a Go To Page key aimed at another deck, or a message without `profile:`, keeps working.
- The back and previous trails are kept across restarts.
- Clearer messages in the Go To Page key's settings when another deck's pages can't be listed.

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
