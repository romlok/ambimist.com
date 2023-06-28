## Blocking Meta from the Fediverse

Recently, reports have come out that Meta, owner of Facebook, Instagram, and WhatsApp, have plans for [a service which connects to other platforms using a federated protocol](https://www.platformer.news/p/meta-is-building-a-decentralized).  Seemingly focused on [ActivityPub](https://en.wikipedia.org/wiki/ActivityPub), a protocol which has been brought to the limelight by Mastodon.

I'm personally ambivalent toward Meta joining the Fediverse, however I believe a large dollop of caution is well warranted.

### Those who forget history

Imagine for a moment if Microsoft entered a nascent market for user interfaces to what I like to call a "world wide web".  Due to the size of their existing user base, Microsoft's implementation of the web standards quickly becomes the de-facto accepted interpretation, including all its bugs, quirks, and inconsistencies.

Microsoft then adds some enticing new features, and websites start coding specifically to Microsoft's client. This forces competing clients to have to play to Microsoft's tune or go out of business - or, eventually, both.

Then, having captured the market and dominated the ecosystem, Microsoft loses interest.  After all, there's no return on making improvements to a product or service which has no competition.  Most grey-beard web devs can tell you that the subsequent Internet Explorer 6 era was not a great time for innovation - or security - on the web.

Now imagine if Meta entered a nascent market for clients to display what one might call a "fediverse".  Due to the sheer size of Meta's existing user base, developers will do their best to interoperate with the quirks of Meta's implementation of the standard, no matter how quirky, making Meta's interpretation the de-facto correct interpretation...

#### Are doomed to repeat it?

Or look to the history of [OpenID](https://en.wikipedia.org/wiki/Openid).

For a brief, golden, glorious time in the mid-2000s we had true federated logins.  I would post comments on random Wordpress blogs, and sign in to Stack Overflow, by providing the site only my own website's URL.  Anyone could set up their own ID provider, or proxy one through their own domain (as I did), and any website supporting OpenID logins would accept it.

But you don't see that any more, do you?  The only third-party login options you commonly see are for the big identity gatekeepers - Google, Apple, Facebook, Twitter.  What happened to federation?

What happened is that the big identity gatekeepers got involved in setting the standard.  It got new, more complex versions, and it got moved on top of OAuth.  This de-facto killed the true federation, as each website essentially then had to explicitly authorise every third-party identity provider, else implement an optional extension that would complicate their already complex authentication systems.  And few are going to bother with that when 99.99% of people will just use Google, Apple, Facebook, or Twitter.

["Embrace, extend, extinguish"](https://en.wikipedia.org/wiki/Embrace,_extend,_and_extinguish) is still quoted precisely because *it works*!

#### Eternal September, 2023

Even notwithstanding the possibility of deliberate action to undermine true federation, Meta is the gatekeeper for some of the largest online user bases on the internet.  Should Meta choose to connect one of these existing user bases to the Fediverse, they would more than likely instantly create the largest single community on the network by far.  The majority of this community will likely know little about federation, and care about it even less.

When a large group of people arrives in a more sparsely populated region, the sheer numbers of the newcomers tend to push out and marginalise the peoples and cultures who lived there before - either through insular disinterest, or deliberate self-assured action.

Thirty years on, will the Fediverse suffer its own [Eternal September](https://en.wikipedia.org/wiki/Eternal_September)?

### So should Meta be blocked from joining a network?

Were Meta to join the Fediverse, the sheer quantity of users, developers, and societal clout at their disposal would provide them an enormous amount of influence over the evolution of the network, and ActivityPub as a standard.

Do you trust that Meta will be a good citizen of the network?  Does the network have procedures and systems in place to prevent one or a small number of powerful parties from dominating both the technological and societal evolution?

I can't say I know one way or the other, but I remember OpenID.

!["Remember OpenID" scrawled on a wall of Babylon 5](/img/remember-openid.jpeg)

See also: [Ploum writing about the fall of XMPP](https://ploum.net/2023-06-23-how-to-kill-decentralised-networks.html)
