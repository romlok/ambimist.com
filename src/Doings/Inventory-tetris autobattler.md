## Inventory-tetris autobattler

![Our hero finds a chest in the dungeon, but what dangers could lurk in the dark?](/img/bag-of-holding/wide.png)

Watching streamers play [Escape from Tarkov](https://www.escapefromtarkov.com/) and seeing how much time they spent sorting and rearranging their inventory, when compared to time spent actually playing the game, it inspired me to wonder "what if sorting the inventory _was_ the game?  What if the raids were just played out automatically?"

It seems like Resident Evil fans are all over inventory organisation, with games like [Save Room](https://store.steampowered.com/app/1955330/Save_Room__Organization_Puzzle/), and [random fan games with falling blocks](https://old.reddit.com/r/residentevil/comments/uxqjvg/resident_evil_4_tetris_edition_fangame_i_made/).

However, I could find no game which combined the challenge of arranging Tetris-like falling shapes with the metagame of an autobattler.

Others later followed through on similar ideas, such as [Backpack Hero](https://thejaspel.itch.io/backpack-hero), which successfully implements inventory organisation as a core aspect of gameplay in a roguelite; and a game jam entry [Bag of Holding](https://thoof.itch.io/bag-of-holding), closer to my idea that it even has the same working title!

Yet still no falling shapes.


### The story so far

![Arranging falling items in an early prototype](/img/bag-of-holding/inventory.gif)

I decided on a fantasy medieval setting, so that the autobattler part could be a well-understood dungeon crawl;  and on a low-poly (low-vertex?) 2D style, since it's simple and fast to make programmer art for!

The primary gameplay loop so far superficially resembles the Tetris arrangement, where the player has a game grid (the bag) into which shapes (items) fall, and a queue displaying the shape/s that are to be deposited in the game grid.

Whereas in the case of Tetris the next shape/s are determined directly, at random or by some algorithm, the items to be delivered to the bag in this game are determined by the procession of the autobattler element.  This is still random at its root, but provides the potential for the player to influence the generation of items in an intuitive manner.

A further difference from classic Tetris gameplay is that the falling speed of the items is not determined simply by how much progress the player has made.  I wanted to include this aspect of challenge, but in a manner which could be ameliorated by the player's actions, and also tied to the autobattler.  Thus a "queue pressure" system is used, where the speed of the falling item depends on the number of looted items waiting to be dropped.  This punishes the player for dawdling about placing items, rather than punishing the player simply for playing well.

#### Going on adventures

![Facing off against goblins](/img/bag-of-holding/dungeon.png)

As it stands in the initial alpha release, each game session is called an "adventure", and each of these autobattled adventures has two possible endings - either the items in the bag overflow, in which case the hero notices and leaves the dungeon with their loot; or else the hero falls in combat with the denizens of the dungeon.

Thus, the player must balance acquiring and organising loot with strategically arranging for the bag to overflow before it's too late!


<div style="position: relative; padding-top: 56.25%;"><iframe title="Bag of Holding pre-alpha gameplay" src="https://spectra.video/videos/embed/6228d1ac-26d2-4b92-a85d-6545776c939f?warningTitle=0&amp;p2p=0" allowfullscreen="" sandbox="allow-same-origin allow-scripts allow-popups" style="position: absolute; inset: 0px;" width="100%" height="100%" frameborder="0"></iframe></div>

For those wanting to try it out for themselves, I've made executables available as [Bag of Holding on Itch](https://romlok.itch.io/bagofholding), though I've only been able to personally test the Linux binary, so YMMV.


#### Combat

![RIP](/img/bag-of-holding/rip.png)

Right now, combat is very simple and deterministic.  Both the hero and the enemies do a static amount of damage and have a static amount of health (though "Custom adventures" can modify these fixed values).

I intend to keep combat simple, automatic, and likely deterministic, but the intention is for the player to be able to influence the hero to keep them alive, so affecting combat with actions such as switching weapons and drinking potions is the ultimate aim.


### To be implemented

While the future of the project is still somewhat uncertain, I have developed not so much a plan as a set of ideas for making this into a more complete game.


#### Opening the bag

![](/img/bag-of-holding/potion.png)

I toyed with ideas of how the ~~Tetris~~ _legally distinct falling shape puzzle_ aspect could work, since there needs to be a way for items to _leave_ the bag, for dungeon crawls to last more than a couple of minutes.

I considered Tetris-like destruction of filled lines, but "destroying" parts of items  1. didn't mesh well with the idea that the hero's going to be selling this stuff; and 2. would require a significant rewrite as to how equipment was implemented in game.

One related alternative was that only whole items could be sent to the void.  I could only see two ways of this working however:  either an item is removed when it contributes to a finished line; or an item is removed only when all the lines it contributes to are finished.  Unfortunately, I see the former as being far too easy to clear the bag, and the latter as far too difficult!

Another alternative I considered was for sharp items like swords to be able to cut holes in the bag itself, letting items fall out!  This would make placement and orientation of items even more meaningful, which appeals to me, but feels like it could make the gameplay too chaotic and prone to catastrophic errors, and detract from the organisational aspect.

![](/img/bag-of-holding/big_axe.png)

Additionally, all of these options flew in the face of another gameplay aspect I wanted to adopt - that the player can nudge the behaviour of the hero by having them take an item (weapon, healing potion, etc.) out of the bag to use.

Thus, being able to physically lift items out of the bag, as a reversal of the dropping mechanism, was considered.  However, this conflicts and interferes with the gameplay loop of items constantly falling, and the time/speed pressure that can be applied there.  Further, without some kind of physics implementation, only the topmost layer of items could be lifted, limiting the organisational strategies available to the player.

So the current plan is simply to use magic!  The player will highlight an item that has settled in the bag, prompting the hero to pull it out when they have a chance.  At that point the item will simply disappear from the bag, and items above it in the game grid will start falling again, and/or leave awkward spaces.  This adds the gameplay dimension that the player needs to consider possible future removal of items when organising the bag content!


#### Exploration

![](/img/bag-of-holding/rocks.png)

The current dungeon is linear, but branching could be added with the inclusion of keys and side-doors.  For example, the player uses a key as the hero is approaching a side-door, and instead of continuing on the current path, the hero will unlock and enter a door to a different region of the dungeon.


#### Metagame

![](/img/bag-of-holding/coin.png)

Apparently every autobattler needs metagame progression, and this concept seems rife with possibilities for variations and progression:  hero classes, hero traits, starting equipment, bag size, queue size, etc.

Talk about scope creep!
