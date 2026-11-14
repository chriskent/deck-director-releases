---
title: Choosing the deck, profile and page
nav_order: 4
---

# Choosing the deck, profile and page

One message can name all three, in any order, separated by `;`. Leave out what you don't need.

| Message | Switches |
|---|---|
| `page:AVN` | The deck last used, in the profile it's showing |
| `device:Stream Deck + XL; page:AVN` | That deck, in the profile it's showing |
| `profile:C172 AP Panel; page:AVN` | That profile, on the first connected deck of the type it was made for |
| `device:<deck>; profile:<name>; page:AVN` | Exactly that deck and profile |

**device**
: The deck's name as shown in Stream Deck, or its id. Virtual Stream Deck and Stream Deck Mobile count as decks. Name the deck when you have more than one and a message must always go to the same one.

**profile**
: The profile's name as shown in Stream Deck. It must be [adopted](adopting) and made for that type of deck. Decks of different types can each have a profile with the same name: the one for the deck you named is used, or for the deck last used if you didn't name one. On one type of deck, keep names different.

**page**
: Anything from [Messages](messages): a name, number, `+1`, `back`, `home` and so on.

Keys and names aren't case-sensitive. Names can contain spaces and `:` but not `;`.

## How Deck Director knows which profile is showing

Stream Deck doesn't tell plugins which profile is on a deck. Deck Director finds out from its own keys: when a Set Home Page or Go To Page key comes into view, it knows that profile is showing. If none has appeared since its last switch, it assumes the profile it switched to last. That's why page 1 of each profile you control should have a Set Home Page key.

## The Deck Director keys

**Set Home Page**
: Put it on R1C1 of page 1. That page becomes the profile's home (`page:home` goes there), and pressing it goes home and restarts the breadcrumb.

**Go To Page**
: A key that switches pages by itself, no other app needed. Its settings list the profile's pages, plus next, previous, back, home, first, last or a custom value. **Device**: leave it as *This deck*, or pick another deck for the key to control.

**Adopt Profile**
: Shows whether the profile it's on is adopted and how many of the 50 adoption slots are in use, and adopts or releases it. See [Adopting profiles](adopting#what-the-key-shows).
