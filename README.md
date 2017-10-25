# jnsl 
**Joy Narical's simplest lootfilter** for [Path of Diablo](https://pathofdiablo.com).
# \[[DOWNLOAD](https://raw.githubusercontent.com/narical/jnsl/master/item.filter)\]

(*More information about loot filtration syntax can be found [here](http://pathofdiablo.com/wiki/index.php/Loot_Filtration)*)

### Before:
![Without lootfilter](/images/before.png)

### After:
![With lootfilter](/images/after.png)

## Overview
The most basic lootfilter, created with KISS (*Keep It Simple, Stupid*) principle in mind.  
This filter was intended to be used from the acts 4-5 of "Normal" difficulty onwards.

### Goals
* clear almost useless trash
* keep game experience as vanilla as possible
* be short and crystal clear to understand
* ease of modification

### Features
* names of very common items shortened
* exceptional items have red asterix mark after their name, elite items have two
* all ethereal items now preceded with word "etherial"
* uniques and runewords have 'uniq' and 'runeword' marks for ease of distinguish
* socketed items have number of sockets followed after their names
* potentially expensive staves, wands and scepters with less then 5 sockets show their vendor price
* different display options for every set of items' tier (normal, exceptional, elite), quality (inferior, superior, magic etc.) and number of sockets
* show charms, jewelry, uniques, set items and other important stuff
* minimal size of gold piles shown limited to 500
* only Super/Greater potions left, white and gray respectively
* hide (non-rare) arrows, bolts, chipped and flawed gems, throwing potions, and keys
* tp/identify scrolls, thawing and antidote potions now barely visible

## How it works
Every line represents single rule, which consist of "conditions" and "display" parts.  
ItemDisplay\[ *conditions* \]: *what to display*  
If *display* part of the rule (after colon) is empty - game hides an item.  
For every item on screen, game checks rules list in plain order until *conditions* are met, and draw item's name according to *display* part of that particular rule. **All following rules for that item are discarded, even if their conditions match the item.**

For example, if there's two rules, first to show rares, second to show socket number next to socketed items, all rares will be shown without socket number even if they have sockets. You can workaround that by adding new rule before others, which checks if item is rare AND have sockets simultaneously. JNSL sometimes ignoring such cases for internal simplicity, implying that player will check good item anyway (for example, it draw white scepters with vendor price, and rare/unique scepters without it)

Main filter part consist of three blocks (one per item tier - normal, exceptional and elite), which configure how to show all possible properties combinations of that tier. Here's the block for normal items:
<pre>
// NORMAL ITEMS
ItemDisplay[NORM NMAG !SUP !INF !RW SOCK<5]:
ItemDisplay[NORM NMAG !SUP !INF !RW SOCK>4]: %NAME% [%SOCKETS%]
ItemDisplay[NORM INF]:
ItemDisplay[NORM MAG]:
ItemDisplay[NORM ETH SUP SOCK<2]:
ItemDisplay[NORM ETH SUP SOCK>1]: Ethereal %NAME% [%SOCKETS%]
ItemDisplay[NORM SUP SOCK<5]:
ItemDisplay[NORM SUP SOCK>4]: %NAME% [%SOCKETS%]
ItemDisplay[NORM ETH RARE SOCK=0]: Ethereal %NAME%
ItemDisplay[NORM ETH RARE SOCK>0]: Ethereal %NAME% [%SOCKETS%]
ItemDisplay[NORM RARE	SOCK=0]: %NAME%
ItemDisplay[NORM RARE	SOCK>0]: %NAME% [%SOCKETS%]
ItemDisplay[NORM ETH UNI]: Ethereal %NAME% (uniq)
ItemDisplay[NORM UNI]: %NAME% (uniq)
ItemDisplay[NORM ETH RW ]: Ethereal %NAME% (runeword)
ItemDisplay[NORM RW]:	%NAME% (runeword)
ItemDisplay[NORM SET SOCK=0]: %NAME%
ItemDisplay[NORM SET SOCK>0]: %NAME% [%SOCKETS%]
</pre>

It begins with **if normal-tier, non-magical, not superior, not inferior, not runeword item have less then five sockets  - hide it**.  
Then **if same item have five or six sockets - show it's name with number of sockets (with brakes) after it**.  
Then **if normal-tier item is inferior - hide it**  
Last part of block means that all rare, unique, runeword and set items will be shown, with *etherial* added before etherial, *uniq* and *runeword* added after corresponding item name.  
Exceptional and elite blocks configured the same way.

## Installation
Download **item.filter** file and place it in *Path of Diablo* folder. Enable **custom loot filter** option in PoD settings (CTRL+click in bottom-left corner).
