The following is adapted and expanded from a talk I gave in November 2022 at an internal developers conference for the company I worked for.  I'd been thinking a lot about coding styles, and had had an insight that I wanted to share.


## Coding styles are like assholes

You may be familiar with the idiom:

> Opinions are like assholes; everyone has one, and they all stink

And I claim this also of coding styles.  Why?  Because they claim it about themselves:

![A selection of GitHub projects describing themselves as "opinionated"](/img/coding-styles/opinionated-github-slide.png)

The above is a selection of code formatting and style projects on GitHub when you search for "opinionated".  These are _only_ projects relating to code style and formatting, and _only_ ones on GitHub.  There are many other opinionated projects out there, believe me!

I have seen that not only these projects, but the wider software community, seem to use the word "opinionated" as a badge of honour.  As if it is a good and virtuous thing to be opinionated.  One of these projects even gave themselves a *trophy* for being opinionated!

![A Go styleguide gives itself a trophy](/img/coding-styles/opinionated-github-trophy.png)

But if we think about the word, what does it mean to be opinionated?  It means to be biased, dogmatic, and arbitrary.  In fact, if you look up "opinionated" in a thesaurus, you will find a whole heap of words which you probably don't want to see associated with your project or its leadership!

Opinions are divisive, precisely because they are personal and arbitrary.  And when arbirary opinions differ, there can be no resolution but enforcement by authority.  This leads to resentment and division, and is a fuel of the "holy wars" that exist and persist in programming and technology circles.

So if we shouldn't be opinionated, what alternative is there?


### Ancient Greece

![[The School of Athens](https://en.wikipedia.org/wiki/The_School_of_Athens) by Raphael, depicting famous classical Greek philosophers](/img/coding-styles/bunch-of-greeks.jpg)

Over two thousand years ago, the ancient Greeks were already studing logic and reason, denouncing opinion, and seeking objective truth.

And humanity didn't stop with conjecture and rhetoric; in the millennia since, we've developed our collective knowledge of investigation, science, and research; and we today have the tools available to us to find truths, to understand the world around us, to find objectively better ways of doing things - and to find these things beyond reasonable argument.

We who write software like to call ourselves "Engineers", and the basis of what we do is indeed logic and reason - that's how computers work!  But a lot of what we do is still based on instinct, on gut feelings, on opinions.


### Rust

![[Rust Style Team assemble!](https://blog.rust-lang.org/inside-rust/2022/09/29/announcing-the-rust-style-team.html), Sept 2022](/img/coding-styles/rust-style-team.png)

In the early years of the Rust programming language, the Rust Style Team was created to discuss and decide upon a consistent set of style guides for people writing in Rust.  Once the style guide was completed, and the team's job done, the group was disbanded.

In the intervening years, the Rust language didn't sit still, with new features being added, and knowledge and practices being advanced.  So the [Rust Style Team was re-formed](https://blog.rust-lang.org/inside-rust/2022/09/29/announcing-the-rust-style-team.html) to update the existing Rust coding style with guidance on how to use new features of the language.

Since I was already thinking about this subject, I took a look at the announcement.  What I found, buried in their [RFC-3309](https://rust-lang.github.io/rfcs/3309-style-team.html), was this small ray of light:

![Snippet of [Rust RFC-3309](https://rust-lang.github.io/rfcs/3309-style-team.html)](/img/coding-styles/rust-style-rfc.png)

Among the sources that the Rust Style Team announced would be used to inform their decision was research - into language transferability.  This is great.

It's a great start, at least.  Because I believe that there is a great deal more research that such a style team should be consulting!


### What is source code?

As a software developer, what is source code to us?

* It is how we understand the precise function of an application.

* It is how we interact with the inner workings of software.

* It is ***our primary user interface*** to the project we're working on!

We as a society have centuries of research and investigation into how people perceive the world around us, our common biological quirks, the cognitive biases and shortcuts that our brains share, how we understand written words and symbols, and how we interact with our environment and the tools we make.

We don't have to rely on our feelings of the right way to do things, when we have data available to that allows us to make reasoned decisions.


### Odd one out

One of the cognitive shortcuts our brains provide is near instantaneous and effortless recognition and classification of objects based on certain characteristics, such as their shape.  To demonstrate this, we can play some simple games of spotting the odd one out:

![One of these sushi is not like the others](/img/coding-styles/sushi.jpg)

Here we have three pictures of sushi in different environments.  Just by looking at their shape, their construction, we can recognise that the sushi in the middle is different from the other two.  We don't have to know the ingredients, the taste, the texture, or even the names.

![One of these UI elements is not like the others](/img/coding-styles/potato-ui.png)

If you've been familiar with computers for any length of time, you will probably recognise the left two items as buttons.  We don't have to know what it says on the button, or even what language it is written in, to understand that these are things which we as the user can interact with to perform an action.

![One of these code blocks is not like the others](/img/coding-styles/reframe-code.png)

Here we have some Clojure(Script) source code - blurred so we focus only on the shape.  One might expect that the bottom code snippet is the odd one out here.  This is obviously a trick question, however.

The odd one out is actually the first code block, yet we can't tell that from its shape.  When reading this code, to understand the nature of each block, to understand what kind of concept the code represents, we have to stop, read, and parse at least the first line of each block.

For reference, this is code written according to the [Re-Frame framework](https://github.com/day8/re-frame).  The first block represents what is known as a subscription, while the bottom two represent event handlers.

The reason I chose this particular example is because the middle and bottom code blocks, which are visually distinct from each other, in fact provide *the exact same* functionality!  The middle block makes use of a convenience function intended to reduce the need for boilerplate, but in doing so it directs the visual shape of the resultant code toward being indistinguishable from a something which is conceptually very different!


### Source code is a UI

I hope it is now clear that source code is itself a user interface, with which developers interact daily, and that how we design and arrange the code can have a strong effect on how quickly and instinctively we can understand it.

It may be rather unreasonable to ask all software developers to also be UI experts (though I wouldn't object if this were the case!).  However, if you're involved in writing a coding style guide - whether for a programming language, a library, or a whole application - I think it would be a great benefit to have at least a basic grounding in the principles of user interface design.

But whatever you're doing, whether you're writing code or not, writing style guides or not, all I really ask is that you be *reasonable*!
