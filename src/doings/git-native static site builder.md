## An unnamed git-native static site builder

I wanted this website to be just simple static files, so I went looking for a simple no-frills static site generator.  None I found to be satisfactory.  So being a software developer, I of course made my own.

### Principles

* Git native
* Self contained
* Zero install
* Zero configuration

#### Git native

Two of my peeves about a lot of article-based websites are that: They fail to mention when an article is published; and they are not transparent when and what changes are made to published articles.

Since I was inevitably going to be storing my site's content in Git, and Git tracks this information already, I decided to leverage Git's repository metadata to help build the site content.

Once that decision had been made, it didn't take long to realise that one could derive other site information purely from Git metadata.

Thus it was decided:

* If something can be derived from the content or metadata of the Git repository, it should be.
* If something _cannot_ be derived from the Git repository, then one should think carefully if it is really that important.

#### Self contained

The tool should live in the repository with the site it built.  Thus, one always knows what version of the tool was used to build the site.  And, in the spirit of software freedom, to distribute the site is to also distribute its means of production!

For instance, one can see the source of the version used to build this site at [/engine/build](/engine/build).

#### Zero install

Building a few static html pages isn't rocket science, I shouldn't need to download half the internet as dependencies, or install a new application.  Ideally, there should be two requirements for the tool:

* Git
* A posix-compatible `/bin/sh`

Although it was found that, as a practical compromise, `pandoc` is required to be installed if one wants to build articles from Markdown sources.

#### Zero configuration

I don't want to have to mess around with config files, when what I should be doing is writing articles.  I should be able to just write my thoughts to files, and have the site be built sensibly based on the arrangement of those files in the Git repository.


### How it works

I should probably write something here, yeah?