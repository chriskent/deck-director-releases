---
title: Adopting profiles
nav_order: 5
---

# Adopting profiles

Stream Deck only lets a plugin switch profiles that belong to it. Adopting marks one of **your** profiles as Deck Director's, so it can switch its pages.

## What adopting changes

Two fields are added to the profile's settings file. Nothing else changes: your keys, pages, names and Smart Profile (app) switching all keep working. You can go on editing the profile as normal.

Stream Deck must be closed while the file is changed, so adopting or releasing **closes and reopens Stream Deck** by itself. A backup of each changed file goes to `%LOCALAPPDATA%\DeckDirector\backups`.

{: .note }
Adoption relies on undocumented Stream Deck behaviour. It's been tested on Stream Deck 7.5.

## With the Adopt Profile key (easiest)

1. Drag **Adopt Profile** (category Deck Director) onto any page of the profile.
2. Press it twice. The second press must come within 4 seconds; the key's settings can turn that off.
3. Stream Deck closes and reopens, and the key shows **Adopted**.

Press it twice again to release the profile.

## With the adopt tool

1. Start menu › Deck Director › **Adopt a Stream Deck profile**.
2. Type the profile's number to adopt it, or `r` and its number to release it.

## Limits

Up to **50 profiles** can be adopted at once, shared across all your decks: any mix of Stream Deck + XL, XL, Stream Deck +, Virtual Stream Deck and Stream Deck Mobile. The adopt tool's list shows how many are in use. Releasing a profile frees its place for another.

## Don't duplicate an adopted profile

A copy made in the Stream Deck app keeps the adoption fields, so two profiles claim the same place and Deck Director only reaches one of them. If you want a copy as a backup, release it, or don't use it for switching.

## Uninstalling

Uninstalling Deck Director leaves adopted profiles working as normal profiles, and reinstalling picks them up again. Release them first if you want them exactly as they were.
