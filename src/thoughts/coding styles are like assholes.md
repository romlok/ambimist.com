The following is adapted and expanded from a talk I gave in November 2022 at an internal developers conference for the company I work for.  I'd been thinking a lot about coding styles, and had had an insight that I wanted to share.


## Coding styles are like assholes

You may be familiar with the idiom:

> Opinions are like assholes; everyone has one, and they all stink

So why do I say this also about coding styles?  Because they say it about themselves:

[next slide please]

The above is a selection of code formatting and style projects on GitHub when you search for "opinionated".  These are _only_ projects relating to code style and formatting, and _only_ ones on GitHub.  There are many other opinionated projects out there, believe me!

I have seen that not only these projects, but the wider software community, seem to use the word "opinionated" as a badge of honour.  As if it is a good and virtuous thing to be opinionated.  One of the projects here even gave themselves a trophy for being opinionated!

But if we think about the word, what does it mean to be opinionated?  It means to be biased, dogmatic, and arbitrary.  In fact, if you look up "opinionated" in a thesaurus, you will find a whole heap of words which you probably don't want to see associated with your project or your leadership!

Opinions are divisive, precisely because they are personal and arbitrary.  And when arbirary opinions differ, there can be no resolution but enforcement by authority.  This leads to resentment and division, and is the fuel of the "holy wars" that exist and persist in programming and technology circles.

So if we shouldn't be opinionated, what alternative is there?


### Logic and reason

[next slide please]

These folks knew what it was about.  The ancient Greeks were studing logic and reason over two thousand years ago, denouncing opinion and trying to find objective truth.

And humanity didn't stop with conjecture and rhetoric; in the millennia since, we've developed our collective knowledge of investigation, science, and research; and we today have the tools available to us to find truths, to find objectively better ways of doing things - and to find these things beyond reasonable argument.

We who write software like to call ourselves "Engineers", and the basis of what we do is indeed logic and reason - because that's how computers work!  But a lot of what we do is still based on instinct, on gut feelings, on opinions.


### A good start

[top of next slide please]

The Rust programming language recently re-formed their Coding Style Team.  In the early days of the language this group was created to discuss and decide upon a consistent set of style guides for people writing the language.  Once the style guide was completed, and the Style Team's job done, the group was disbanded.

In the intervening years, the Rust language hasn't sat still, with new features being added, and knowledge and practices being advanced.  So the Coding Style Team was re-formed, to update their existing coding style with guidance on how to use the new features of the language.

Since I was already thinking about this subject, I took a look at the announcement, and buried in the RFC document, I found this small ray of light:

[bottom of slide please]

Among the sources they would use to inform their decision was research - into language transferability.  This is great.

It's a great start, at least.  Because I believe that this isn't the only research a style team should be consulting.


### What is source code?

As a software developer, what is source code to us?

* It is how we understand the function of an application.

* It is how we interact with the inner workings of software.

* It is ***our primary user interface*** to the project we're working on!

We as a society have centuries of research and investigation into how people perceive the world around themselves, our common biological quirks, the cognitive biases and shortcuts that our brains share, how we understand written words and symbols, and how we interact with our environment and the tools we make.


### Odd one out

One of the cognitive shortcuts our brains provide is instantaneous and effortless recognition and classification of objects based on certain characteristics, such as their shape.  To demonstrate this, we can play some simple games of finding the odd one out:

[next slide please]

Here we have some sushi.  Just by looking at the shape, the construction, we can recognise that the sushi on the left is different from the other two.  We don't have to know the ingredients, the taste, the texture, or even the names.

[next slide please]

If you're familiar with computers, you will probably recognise the left two items as buttons.  We don't have to know what it says on the button, or even what language it is written in, to understand that these are things which we as the user can interact with to perform an action.

[next slide please]

Here we have some Clojure source code - blurred so we focus only on the shape.  One might expect that the rightmost code snippet is the odd one out.  This is a trick question, however.

The odd one out is actually the one on the left, but we can't know that from its shape.  When reading this code, to understand the nature of each block, to understand what kind of concept the code represents, we have to stop, read, and parse the first line of each block.

For reference, this is code written for the [Re-Frame framework](https://github.com/day8/re-frame). The block on the left represents a subscription, while the two on the right represent events.

The reason I chose this particular example is because the two code blocks on the right, which are visually distinct from each other, in fact provide exactly the same functionality!  The middle block makes use of a convenience function intended to reduce the need for boilerplate, but in doing so it directs the visual shape of the resultant code toward being indistinguishable from a something which is conceptually very different.


### Source code is a UI

Thus I have described how source code itself is a user interface, and that how we design and arrange the code has a strong effect on how instinctively we can understand it.

So while it's rather unreasonable to ask all software developers to also be UI experts, if you're involved in researching and writing a style guide - whether language, library, or application - it is my belief that you should probably have at least a basic grounding in the principles of user interface design.

But whatever you do, whether you're writing code or not, writing style guides or not, all I really ask is that you be *reasonable*!
