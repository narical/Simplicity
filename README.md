# jnsl
**Joy Narical's simplest lootfilter** for [Path of Diablo](https://pathofdiablo.com).

(*More information about loot filtration syntax can be found [here](http://pathofdiablo.com/wiki/index.php/Loot_Filtration)*)

### Before:
![Without lootfilter](/images/before.png)

### After:
![With lootfilter](/images/after.png)

## Overview
The most basic lootfilter, created with KISS (*Keep It Simple, Stupid*) principle in mind.
This filter was intended to be used from the acts 4-5 of "Normal" difficulty onwards.

### Goals
* clear visual clutter
* keep game experience as vanilla as possible
* be short and crystal clear to understand
* ease of modification

### Features
* show charms, jewelry, uniques, set items and other important stuff
* minimal size of gold piles shown limited to 500
* names of very common items shortened
* only Super/Greater potions left, white and gray respectively
* hide (non-rare) arrows, bolts, chipped and flawed gems, throwing potions, and keys
* tp/identify scrolls, thawing and antidote potions now barely visible
* potentially expensive white/blue staves, wands and scepters with less then 4 sockets show their vendor price
* all ethereal items now preceded with word "etherial"
* uniques and runewords have 'uniq' and 'runeword' marks for ease of distinguish
* exceptional items have red asterix mark after their name, elite items have two
* socketed items have number of sockets followed after their names
* different display options for every set of items' tier (normal, exceptional, elite), quality (inferior, superior, magic etc.) and number of sockets

## Installation
Download **item.filter** file and place it in *Path of Diablo* folder. Enable **custom loot filter** option in PoD settings (CTRL+click in bottom-left corner).
