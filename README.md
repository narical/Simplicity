# Simplicity v2.5

**JNarical's simplest lootfilter** for [Path of Diablo](https://pathofdiablo.com).
(*More information about loot filtration syntax can be found [here](http://pathofdiablo.com/wiki/index.php/Loot_Filtration)*)

# \[[DOWNLOAD](https://raw.githubusercontent.com/narical/jnsl/master/item.filter)\]

### Before:
![Without lootfilter](/images/before.png)

### After:
![With lootfilter](/images/after.png)

## Overview
**Simplicity** is made for **casual Diablo II players** - not for powerplay and high-efficient grind, but for smoother vanilla experience with some non-intrusive quality-of-life features.

Unlike others, this filter is **rather different**. It isn't supposed to hint you about crafting bases or something, it isn't supposed to hide maximum loot as possible, or show names of unidentified uniques and set items like if you already identified it. It isn't supposed to shorten items' names to 2-3 char abbreviations unknown to new players. It supposed to be **sane defaut itemfilter** which doesn't strips out anything important for new players' experience.

As opposed to other lootfilters, consisting of 1000-2000 lines of code, it has only ~100 lines (not including comments), and it's very easy to understand and modify. At character levels 1-4 filter shows everything, from level 5 it hides inferior items, from level 10 it begins to hide more and more items, considered useless, based on certain character level thresholds.

### Goals
* clear almost useless trash
* keep game experience as vanilla as possible
* be short and crystal clear to understand
* ease to modify

### Features
* names of very common items shortened
* exceptional items have red asterix mark after their name, elite items have two
* all ethereal items now preceded with word "etherial"
* uniques and runewords have 'uniq' and 'runeword' marks for ease of distinguish
* socketed items have number of sockets followed after their names
* potentially expensive items show their vendor price
* different display options for every set of items' tier (normal, exceptional, elite), quality (inferior, superior, magic etc.) and number of sockets
* show charms, jewelry, uniques, set items and other important stuff
* minimal size of gold piles limited depending on character level
* only two best tiers of health/mana potions shown, based on character level
* hide lower grade gems, based on character level
* hide (non-rare) arrows and bolts and throwing potions
* thawing, stamina and antidote potions now barely visible

## How it works
Every line represents single rule, which consist of "conditions" and "display" parts.
ItemDisplay\[ *conditions* \]: *what to display*
If *display* part of the rule (after colon) is empty - game hides an item.
For every item on screen, game checks rules list in plain order until *conditions* are met, and draws item's name according to *display* part of that particular rule. **All following rules for that item are discarded, even if their conditions match the item.**

For example, if there's two rules, first to show rares, second to show socket number next to socketed items, all rares will be shown without socket number even if they have sockets. You can workaround that by adding new rule before others, which checks if item is rare AND have sockets simultaneously. **Simplicity** sometimes ignoring such cases for, you know, internal simplicity, implying that player will check good item anyway (for example, it draws white scepters with vendor price, and rare/unique scepters without it)

## Installation
Download **item.filter** file and place it in *Path of Diablo* folder. Enable **custom loot filter** option in PoD settings (CTRL+click in bottom-left corner).
