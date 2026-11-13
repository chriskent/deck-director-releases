---
title: Troubleshooting
nav_order: 8
---

# Troubleshooting

## No reply at all

- Check Stream Deck is running and Deck Director is installed.
- Send `ping` over the other protocol. A reply saying `tcp not listening` or `udp not listening` gives the reason.
- Check the port: `41555`, or whatever `%LOCALAPPDATA%\DeckDirector\config.json` says.

## The port changed in 1.0

Test builds before 1.0 used port 50555. Windows can reserve ports from 49152 upwards at each restart (Hyper-V, WSL and Docker do this), which stopped 50555 working on some PCs. A settings file nobody edited moves to 41555 by itself, but keys and scripts that send to 50555 need changing to 41555.

## "error no connected Stream Deck + XL"

Just after Stream Deck restarts, messages can get this for a few seconds while the deck reconnects.

## "error unknown page …" or the wrong profile

- Send `list` to see the profiles and pages Deck Director can switch, and what each deck is showing.
- The profile must be [adopted](adopting).
- Put a Set Home Page key on page 1 of each profile, so Deck Director knows which profile is showing.
- Don't switch to a duplicated copy of an adopted profile: see [Adopting profiles](adopting#dont-duplicate-an-adopted-profile).

## The log

Every message and its reply is logged, in the newest file ending `.0.log`:

```
%APPDATA%\Elgato\StreamDeck\Plugins\uk.co.mxdesign.deckdirector.sdPlugin\logs
```

## Updates

About a minute after Stream Deck starts, and once a day after that, Deck Director asks GitHub whether there's a newer release. Nothing about you or your PC is sent. If there is one, `ping` and the test tool's `list` say so; download it from [Releases](https://github.com/chriskent/deck-director-releases/releases/latest) and double-click to install over the old one. Your adopted profiles and settings are kept.

To turn the check off, add `"updateCheck": false` to `%LOCALAPPDATA%\DeckDirector\config.json`.
