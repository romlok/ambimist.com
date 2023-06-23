## Egotism in open source

I have been a minor contributor in the free and open source software (FOSS) ecosystem for many years, and an observer of its many trends and controversies.

On occasion, I've observed project leads take umbrage with how their project is being used, or with who has forked their project.  I feel like there is a fundamental misconception at play in these circumstances.

### Freedom

Freedom is the key word when discussing FOSS, though I feel it is often misunderstood as to what this freedom applies.  Many developers, and even project leads, seem to interpret it as "Freedom for other people to use and improve my software", but this is a misconception.

While the legal terms of the license are necessarily framed in the context of providing rights to other people than the original copyright holder, the effective freedom granted is that of the software itself!  By using a FOSS license for your code, you are freeing the software _from your exclusive control_.

Once a FOSS license is applied to a codebase, even if you have written every single line of code in it, you are now just a member of its caretaker community.  Perhaps you are its only caretaker, but you are no longer the code's master, its owner - the code has been liberated!

As with animals, or human beings, when one creates software one cannot claim for it to have been freed - liberated - if it continues to be held on a leash, able to be denied interaction with others on a whim.

### Something something capitalism bad

This distinction and misunderstanding is perhaps core to the Free/Open philosophical divide, and is fostered - by accident or design - by the corporations which involve themselves in FOSS communities.

Corporations benefit from propagating this confusion because they seek to dominate and control that which their business depends upon.  When independent developers buy in to the mistaken ownership-and-permission understanding of FOSS, then they tacitly accept and accede to corporations' ownership and control over FOSS codebases, and lose the sense of agency and community around the codebase being a shared resource.

Nowhere is this confusion propagated more plainly than by modern code-hosting sites, such as GitHub.

### GitHub considered harmful

The first and most clear aspect of GitHub that encourages the idea that FOSS is owned, is that all codebases are displayed in the context of a single individual or organisation.  While multiple users can have forks of the same repositories, GitHub will only show the repository for what GitHub considers the "canonical" owner.

![Some GitHub search results for "godot"](/img/foss/search-godot.png)

Which user or organisation is considered by GitHub to be the one, true, owner of a repository is initially set at repository creation.  Changing this owner then requires explicit action and cooperation, either between the current "owner" and the claimant, or between the claimant and GitHub themselves.  This makes this concept of "ownership" of a codebase open to political machinations.

#### Forked from

The centralised ownership mindset is further demonstrated by forks being explicitly put in a hierarchy, marked as non-canonical by presenting them as deferential to a single other fork.

![Each codebase has an "official" fork](/img/foss/forked.png)

Not only is this counter to Git's philosophy, where every fork is technologically equal, but it creates a two-tier ecosystem.  The controller of the "official" fork gets to make unilateral decisions about how the codebase is presented, impacting every other developer working on the codebase.

One decision that can be made by such a codebase autocrat is to stop development entirely.  What then if other developers don't agree, and want or need to keep the project supported?

#### Dead project walking

For one reason or another, codebases die.  I've been guilty of losing interest and abandoning codebases before, and I'll probably do it again.  But just because one person or group loses interest, doesn't mean there isn't a desire or need for the codebase to continue.

Unfortunately, especially for codebases with little or no community aspect such as a niche library, individuals who provide ongoing maintenance for their own needs are today essentially hidden from each other, and their ability to collaborate is stymied.  On GitHub, one has to know to delve into the "network graph" and navigate the chart there to see if, and what, other people may be doing.

![Network graph of a dead GitHub project](/img/foss/network-graph.png)

This leads to a situation like the above, where the "official" project is abandoned, but multiple developers continue work on independent forks with little interaction between them.  Most of them are either missing out on fixes and improvements, or replicating the same changes others have already done.

### Manifesto for a code-centric UI

If we could instead guide developers to understand and internalise that FOSS licenses make the _code itself_ free of ownership _by anyone_, then we can encourage people to feel agency to contribute and collaborate without fear of suppression by some central authority.

This leads me to a single overarching tenet:

#### All forks are created equal

> We hold these truths to be self-evident, that all forks are created equal, that they are endowed by their Creators with certain unalienable Rights, that among these are Use, Study, Redistribution, and the pursuit of Improvement.

As a liberated codebase cannot be owned by any one person or group, it is nonsensical for a hosting platform to decree a codebase's sole owner, and promote only their code and metadata.

Forks can only be judged on their own merits, and thus primacy derived solely from the contributions it attracts and has attracted - such as frequency and recency of merges and commits.

An active community should not need to seek permission from a gatekeeper to have their fork rise in prominence, when the evidence of their activity already demonstrates their prominence.

#### Issues of issues

Consequently, meta information such as bug reports and feature requests raised against the codebase should not necessarily be associated with any one fork.  A bug unfixed, or a feature denied, in the most prominent fork may be addressed in a less prominent one.

It does a disservice to both the users and the codebase to hide peoples' work, simply because they have not, or can not, get it accepted into the most popular fork.

### Conclusion

Software released under a FOSS license is itself liberated.  You don't need anyone's permission to engage with it, and you can choose yourself who you associate with to improve it.

Thus we need communities and UIs whose focus is more on the shared commons and collaboration, rather than ownership and segregation.  I don't expect such an initiative to come from corporations, whose pursuit of profit encourages philosophies of ownership, but perhaps other FOSS advocates will be inspired to build something better.
