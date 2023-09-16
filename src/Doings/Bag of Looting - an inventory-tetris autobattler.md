## Bag of Looting - an inventory-tetris autobattler

![Bag of Looting title card](/img/bag-of-looting/title-card.png)

[Bag of Looting](https://romlok.itch.io/bagoflooting) is a game I created over the summer of '23.  It combines the falling-shape mechanic of Tetris with a side-scrolling autobattler and a meta-progression system.

As with most games in the Tetris family, the core gameplay involves the arrangement of falling shapes within a limited grid.  However, the autobattler aspect is used to determine both the type and rate of incoming shapes, and to provide the mechanism for clear space in the primary gameplay grid.

<div style="position: relative; padding-top: 56.25%;"><iframe title="Bag of Looting gameplay" width="100%" height="100%" src="https://spectra.video/videos/embed/f848d666-7ce2-4450-885c-dd0265efd050?warningTitle=0&amp;p2p=0" frameborder="0" allowfullscreen="" sandbox="allow-same-origin allow-scripts allow-popups" style="position: absolute; inset: 0px;"></iframe></div>


### Inspiration

![Clockwise from top-left: Save Room, Bag of Holding, Backpack Hero, Resident Evil 4 - Tetris edition](/img/bag-of-looting/inspiration.png)

Watching streamers play [Escape from Tarkov](https://www.escapefromtarkov.com/) and seeing how much time they spent sorting and rearranging their inventory, when compared to time spent actually playing the game, it inspired me to wonder "what if sorting the inventory _was_ the game?  What if the raids were just played out automatically?"

It seems like Resident Evil fans are all over inventory organisation, with games like [Save Room](https://store.steampowered.com/app/1955330/Save_Room__Organization_Puzzle/), and [a random fan game with falling blocks](https://residentevilmodding.boards.net/thread/16458/resident-evil-tetris-edition-v2).

Others followed through on similar ideas, such as [Backpack Hero](https://thejaspel.itch.io/backpack-hero), which successfully implements inventory organisation as a core aspect of gameplay in a roguelite; and a game jam entry [Bag of Holding](https://thoof.itch.io/bag-of-holding), closer to my idea that it even had the same working title!

However, I could find no game which combined the challenge of arranging Tetris-like falling shapes with the metagame of an autobattler.  So with a pioneering spirit, my mind wandered forth!


### Game design

![Arranging falling items in an early prototype](/img/bag-of-looting/inventory.gif)

I decided on a fantasy medieval setting, so that the autobattler part could be a well-understood dungeon crawl;  and on a low-poly (low-vertex?) 2D style, since it's simple and fast to make art for!

The primary gameplay loop superficially resembles the Tetris arrangement, where the player has a game grid (the bag) into which shapes (items) fall, and a queue displaying the shape/s that are next to be deposited in the game grid.

Where Bag of Looting begins to diverge is that the items to be delivered to the bag are determined by the procession of the autobattler element, rather than being determined directly as in the case of Tetris.  This is still random at its root, but provides the potential for the player to influence the generation of items in an intuitive manner.

Another major difference from classic Tetris gameplay is that the falling speed of the items is not determined simply by how much progress the player has made.  I wanted to include this aspect of challenge, but in a manner which could be ameliorated by the player's actions, and also tied to the autobattler.  Thus a "queue pressure" system is used, where the speed of the falling item depends on the number of looted items waiting to be dropped.  This punishes the player for dawdling about placing items, rather than punishing the player simply for playing well.


#### Making room

![](/img/bag-of-looting/potion.png)

For dungeon crawls to last more than a couple of minutes, there needs to be a mechanism for space to be _cleared_ in the bag.

I considered Tetris-like destruction of filled lines, but "destroying" parts of items:  1. didn't mesh well with the idea that the adventurer is going to be selling this stuff; and 2. would require a significant rewrite as to how equipment was already implemented in the prototypes!

One related alternative was that only whole items could be sent to the void.  I could only see two ways of this working however:  Either an item is removed when it contributes to a finished line; or an item is removed only when all the lines it contributes to are finished.  Unfortunately, I see the former as being far too easy to clear the bag, and the latter as far too difficult!

Another alternative I considered was for sharp items like swords to be able to cut holes in the bag itself, letting items fall out!  This would make placement and orientation of items even more meaningful, which appeals to me, but feels like it could make the gameplay too chaotic and prone to catastrophic errors!

![](/img/bag-of-looting/big_axe.png)

Additionally, all of these options flew in the face of another gameplay aspect I wanted to adopt - that the player can nudge the behaviour of the adventurer by having them take an item (weapon, healing potion, etc.) out of the bag to use.

Thus, being able to physically lift items out of the bag, as a reversal of the dropping mechanism, was considered.  However, this conflicts and interferes with the gameplay loop of items constantly falling, and the time/speed pressure that can be applied there.  Further, without some kind of physics implementation, only the topmost layer of items could be lifted, limiting the organisational strategies available to the player.

So instead the game uses a simple select-and-retrieve system.  The player can click an item that has settled in the bag, which will prompt the adventurer to equip it the next time they have a moment.  At that point the item will simply disappear from the bag, and items above it in the game grid will start falling again, and/or leave awkward spaces.  This adds the gameplay dimension that the player needs to consider possible future removal of items when organising the bag content!


#### Auto-battling

![A mockup of a dungeon scene](/img/bag-of-looting/dungeon.png)

The autobattler aspect itself consists of an adventurer - with no sense of self-preservation - moving through a dungeon, searching objects, fighting monsters, and looting corpses.

The dungeon itself is completely linear, randomly populated with encounters of progressively increasing difficulty and increasing reward.  It ends with the inevitable boss monster, whose defeat heralds the end of the game.

The player is able to influence the autobattler through only two means: Allowing the bag to overflow, causing the adventurer to leave the dungeon at their next opportunity; or through selecting items in the bag, which the adventurer will then equip and use when they have a moment.


#### Meta-progression

![The metagame campaign shop between expeditions](/img/bag-of-looting/campaign-screen.png)

I enjoy progression systems in games, both for the sense of continual improvement, and also for allowing more moderately skilled players to experience the whole of a game by providing gradual increases in the player's relative power.

Thus I added a meta-progression campaign, to provide an overview over game completion and discovery/unlocks, and upgrades to make the expeditions easier and last longer.

However, the meta-game is progressed only when the adventurer leaves the dungeon alive.  Thus the player must balance acquiring and organising loot - for use or sale - with strategically arranging for the bag to overflow before it's too late!


### Conclusion

For now I consider Bag of Looting to be complete.  There is of course much more that could be added or improved, but this was never intended to be a long-term project.  I had the good fortune to have both motivation and free time coincide long enough to push this through to where it is, and I'm happy with how it turned out.

<div style="position: relative; padding-top: 56.25%;"><iframe title="Bag of Looting release trailer" width="100%" height="100%" src="https://spectra.video/videos/embed/eaff5d05-7714-4bd1-b058-defe89cdf62e?warningTitle=0&amp;p2p=0" frameborder="0" allowfullscreen="" sandbox="allow-same-origin allow-scripts allow-popups" style="position: absolute; inset: 0px;"></iframe></div>
