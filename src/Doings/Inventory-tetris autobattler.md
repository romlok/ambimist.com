## Inventory-tetris autobattler

Watching streamers play [Escape from Tarkov](https://www.escapefromtarkov.com/) and seeing how much time they spent sorting and rearranging their inventory, when compared to time spent actually playing the game, it inspired me to wonder "what if sorting the inventory _was_ the game?  What if the raids were just played out automatically?"

It seems like Resident Evil fans are all over inventory organisation, with games like [Save Room](https://store.steampowered.com/app/1955330/Save_Room__Organization_Puzzle/), and [random fan games with falling blocks](https://old.reddit.com/r/residentevil/comments/uxqjvg/resident_evil_4_tetris_edition_fangame_i_made/).  And then there is [Backpack Hero](https://thejaspel.itch.io/backpack-hero), which successfully combines inventory organisation with an auto-battler.  However, I could find no game which combined the challenge of arranging Tetris-like falling shapes with the metagame of an autobattler.

### The story so far

![](/img/bag-of-holding/inventory.gif)

I decided on a fantasy medieval setting, so that the autobattler part could be a well-understood dungeon crawl;  and on a low-poly 2D style, since it's simple and fast to make programmer art for!

The primary gameplay loop so far superficially resembles the Tetris arrangement, where the player has a game grid into which shapes fall (the bag), and a queue displaying the shape/s that are to be deposited in the game grid.

Whereas in the case of Tetris the next shape/s are determined directly, at random or by some algorithm, the shapes to be delivered to the bag in this game are determined by the procession of the autobattler element.  This is still random at its root, but provides the potential for the player to influence the generation of shapes in an intuitive manner.

In the current prototype, the game ends when the bag inevitably overflows.  The intent is for this to be a neutral or successful ending, since the bag overflowing indicates to the autobattling hero that there's no more space for loot and it's time to leave and go sell it.  Other endings are intended to be added, such as hero death or boss defeat.

<div style="position: relative; padding-top: 56.25%;"><iframe title="Inventory-tetris autobattler prototype" src="https://spectra.video/videos/embed/79282256-de3f-4c2b-908c-161441678931?warningTitle=0&amp;p2p=0" allowfullscreen="" sandbox="allow-same-origin allow-scripts allow-popups" style="position: absolute; inset: 0px;" width="100%" height="100%" frameborder="0"></iframe></div>

For those wanting to try it out for themselves, I've made the prototype's executables available as [Bag of Holding on Itch](https://romlok.itch.io/bagofholding), though I've only been able to personally test the Linux binary, so YMMV.

### To be implemented

The project got shelved (again) after I got to this prototype stage, but I have developed not so much a plan as a set of ideas for making this into a more complete game.

#### Time pressure

![l00t!](/img/bag-of-holding/loot.gif)

Tetris and the like become more challenging as one proceeds, by gradually increasing how quickly shapes fall.  I wanted to include this aspect of challenge, but to also tie it to the autobattler aspect - punishing players for dawdling, rather than merely for playing well.

Thus, the plan is for the speed of items falling to be affected by the number of items waiting in the queue - beyond a certain point, the more pending items in the queue, the faster items fall in the bag, and the more the player needs to act quickly to prevent overflowing.

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

#### Combat

![Godot vs Goblot, the eternal conflict](/img/bag-of-holding/fight.gif)

Right now, combat in the prototype is just a time sink.  The hero is currently invulnerable, and the two types of enemy are destined to die in a predetermined number of hits.  However, the primary challenge of the game is intended to be that of influencing the hero to keep them alive, so we want there to be risk to the combat.

Since the basic combat is and will be automatic, the player's primary interaction will be through item use.  This will mean things like switching weapons, drinking potions, or even offering bribes to avoid fighting entirely!

#### Exploration

![](/img/bag-of-holding/rocks.png)

The prototype's dungeon is linear, but branching could be added with the inclusion of keys and side-doors.  For example, the player uses a key as the hero is approaching a side-door, and instead of continuing on the current path, the hero will unlock and enter a door to a different region of the dungeon.

#### Metagame

![](/img/bag-of-holding/coin.png)

Apparently every autobattler needs metagame progression, and this concept seems rife with possibilities for variations and progression:  hero classes, hero traits, starting equipment, bag size, queue size, etc.

Whew, talk about scope creep!
