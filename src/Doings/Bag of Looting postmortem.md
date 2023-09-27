## Bag of Looting postmortem

![](/img/bag-of-looting/rip.png)

I'm not really sure how game postmortems are generally structured, so I'm just going to write out some of the thoughts I collected during and after development.


### The very first

Bag of Looting was the very first game I'd been able to stick with long enough for it to become what I could describe as a "complete" game; eg. having menus, graphics, sound, a start, a progression, and an end.

Mostly, my game projects are focused around implementing a single technical or mechanical challenge, after which I lose interest or motivation.  This is why I've described myself as a tinkerer in video game development, rather than a game developer.


### Not a success?

Obviously I wasn't intending to make a commercial success out of the game, since I released it for free.  It hasn't really had any attention either (not even among the friends that I asked to test it! 😛), which is also expected since I put in next to zero effort in publicising it - and what small effort I made was all on niche platforms like [Mastodon](https://toot.io/@ambimist) and [IRC](https://libera.chat).

And that's all okay, because the point of the project was to prove to myself that I could make a game, not to become rich or famous.  So in that sense it was absolutely a success!


### I don't sound so good

I'm a coder, by profession and by inclination.  It's what I'm good at, and what I love.

I enjoy drawing and CG visual art, though I don't claim to have the experience to be good at doing either.

But I know next to nothing about making audio.  The credits screen of Bag of Looting makes this clear, where the sounds and music are the only parts I didn't create myself.  I would've liked to create all the music and foley audio for the game as well - just to say that I did - but I wanted _some_ baseline level of quality, and I have neither the equipment, the tooling, the skills, nor had the time to become "good enough" for my own standards!

So audio and music creation is something I've a mind to learn more about, but given the low priority I generally give to audio quality in the content I consume (I usually listen with monitor speakers or cheap stereo headphones from 10 years ago), I would have a long road ahead on that journey!


### Motivation

I have an issue with motivation.  As mentioned, I tend to lose interest after solving a core technical challenge in a project.  Or, rather, after solving a technical challenge for a game idea, my brainpower gets freed up and starts wandering to and obsessing over other game ideas or technical challenges.

The original idea for Bag of Looting came about three years ago, and I built a prototype of the core gameplay loop.  And with that done, I lost interest.  Or perhaps I just resumed being mentally exhausted from my job, I'm not sure.  Either way, the project died there like so many of my others.

Then my job evaporated in June 2023, and I found myself with a few months of free time, nothing to do, nothing public to demonstrate my skills in ~5 years, and a pressing desire to distract myself from the dread of imminently having to find a new job.

Fortunately, I'd been sharing videos of my occasional game prototypes privately with my colleagues, so it was a simple decision to sign up to a PeerTube instance and make that archive footage publicly visible.  

The resultant "[Inventory-tetris autobattler prototype](https://spectra.video/w/fXJDR56pnhjRQLp9jZGaSa)" video got a single comment: "Fun idea".  It wasn't much, but getting acknowledgement of the idea from this solitary stranger really did help cement my commitment to reviving and following through on the project.

So if you take anything away from this article, let it be to remember that even small actions can be great encouragements!


### Dropping logs

One thing that I credit with keeping me motivated and the project running, were the dev logs.

During development of the game, about every week as it happened, I uploaded a new alpha version and an accompanying dev log.  Sometimes I really didn't want to write about what I'd done - I find it far more interesting to create new stuff, than write about stuff I've already more or less forgotten I'd done.  But once I'd started publishing them, I felt a pressure to continue writing and publishing the dev logs for the duration - lest people<sup>[who?]</sup> think I'd been slacking or had given up.

Overall, I think the dev logs helped entrench the feeling that progress was being made.  What I'd done was no longer just lines in a commit log, but words and screenshots and videos.  Writing the logs forced me to recognise what I had accomplished in the preceding week.  This served as a great motivator, even if nobody would ever read the articles!


### Disciplining myself

However, the main thing that kept me on-task was my `PLAN` file.  It was a simple text document where I listed what I intended to do next, as well as the next milestone (alpha-n, beta-n, release), and a grab-bag list of ideas for functionality.

On previous projects, I have kept plans pretty much in my head (aside from scattered TODOs in the source code).  This is possibly why I get so easily distracted after completing significant challenges - the plan in my head gets pushed out by the mental effort and forgotten!  So just tracking "what I intend to fix tomorrow" was a major boon for making progress.

The "next steps" section of the `PLAN` was what I was actively working on, and what I intended to complete in the next day or so.  It was intentionally _very_ short term, and used mostly to remind myself "what was I doing again?" after getting distracted by uncovering bugs (which would also get added to the "next steps").

If the "next steps" section became empty, I would transfer one or two items from the milestone to it.  Once the milestone became empty, I would build, publish, and write up the changes; before deciding on what of the wishlist functionality made sense for the next milestone.

I had quickly abandoned any idea of planning for any milestone but the very next one.  I find it's far too easy to start scope-creeping myself, and thereby getting disillusioned and demotivated by how much more there is to do.  Dealing with just one milestone at a time I found kept me from being overwhelmed in the face of all my ideas, while providing clear markers of progress.

While my development was always focused on a single fixed milestone, the wishlist could constantly grow with ideas without me giving it much concern.  It was only toward the end of the project, as I noticed my motivation was flagging and my distractability was increasing, that I decided on what was actually necessary for me to consider it a "complete" game, and took a hatchet to everything out of scope.


### Making a mess

As a developer I like to make my code simple, straight-forward, and thereby understandable even when tired.  But I also consider how functionality could be used beyond the immediate case, including how it could be misused or used in error.  And consolidating these two drives takes significantly more time and effort than just bodging things together, especially in something so multi-faceted and asynchronous as a video game.

So it came something as a relief when I'd brought down the hatchet, and the final set of features was decided upon.  My brain no longer concerned itself with other possible uses of functionality, nor was I so revulsed at hard-coding certain special-cases and generally making a mess.  I knew that, once the final milestone was completed, I'd never need to add to or extend that code again! 😌

I certainly won't say that one should take that attitude for interim milestones - or even a release - if you have any intention to continue development at some point.  Refactoring code to more abstracted concepts saved my sanity on several occasions during the alphas.  But if you never intend to come back to a project, I'd say go nuts!


### Drooping features

As I mentioned, in the end I axed a lot of things I thought were neat ideas to add to the game.

Most of all, I'm still kinda dissatisfied with the shape variety in the game.  Most of the items you find are just one or two tiles in size, and very few are 2-dimensional.  This makes the inventory-organisation aspect less challenging, and less interesting, since items can commonly just be stacked vertically with no gaps or overhangs - even when deeply buried items are equipped and removed from the grid.

Otherwise, in case anyone else is inspired to make something similar, but bigger and better, some of the ideas that I cut include: a tutorial, branching dungeons, encounters which accept items (eg. using keys on side-doors), traps, clothing/armour, true 3D dungeon with shadows and stuff, puddles.


### Bugging out

There are also a couple of known bugs that I left in the released game 🙈

The most annoying one is that, for reasons I wasn't able to discern over multiple debugging attempts, you sometimes simply can't select items in the bag.  Items glow when the mouse hovers them, but the glow disappears as soon as you click to select.  Then at some point in the gameplay, it starts working again! 🤷

The other one is that the main menu music sometimes doesn't play properly, or at all.  I only encountered it occasionally when bouncing back and forth around the menu and game, and since it didn't seem to affect the main happy paths, I didn't spend much time looking into it!


### Conclusion

Bag of Looting is not all I wanted it to be.  I imagined it being so much bigger, with more depth, and much more polish.

But it's done, and I'm happy with that. 😊

