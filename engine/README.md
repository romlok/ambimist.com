# Unnamed git-based static site generator

This is the engine that powers static site generation.

Individual sites should not need to change anything in this subdirectory.
Doing so may lead to conflicts when merging a newer version of the engine.

## Principles

* Git native
* Self contained
* Zero install
* Zero configuration

### Git native

Two of my peeves about a lot of article-based websites are that: They fail to mention when an article is published; and they are not transparent when and what changes are made to published articles.

Since I was inevitably going to be storing my site's content in Git, and Git tracks this information already, I decided to leverage Git's repository metadata to help build the site content.

Once that decision had been made, it didn't take long to realise that one could derive other site information purely from Git metadata.

Thus it was decided:

* If something can be derived from the content or metadata of the Git repository, it should be.
* If something _cannot_ be derived from the Git repository, then one should think carefully if it is really that important.

### Self contained

The tool should live in the repository with the site it built.  Thus, one always knows what version of the tool was used to build the site.  And, in the spirit of software freedom, to distribute the site is to also distribute its means of production!

For instance, one can see the source of the version used to build this site at [/engine/build](/engine/build).

### Zero install

Building a few static html pages isn't rocket science, I shouldn't need to download half the internet as dependencies, or install a new application.  Ideally, there should be two requirements for the tool:

* Git
* A posix-compatible `/bin/sh`

Although it was found that, as a practical compromise, `pandoc` is required to be installed if one wants to build articles from Markdown sources.

### Zero configuration

I don't want to have to mess around with config files, when what I should be doing is writing articles.  I should be able to just write my thoughts to files, and have the site be built sensibly based on the arrangement of those files in the Git repository.


## How it works

To create a new website, one simply needs to branch from `master` and start writing pages and articles in the repository's `src/` directory.  Once your changes are `git commit`ted, running the `engine/build` script will build all the HTML files for the site.

The name of the new site, displayed in the site header, will be taken from the branch name. Or by the name of the nearest `git tag` in the branch history when the site is built.

### Pages

For each file and directory in `src/`, a directory will be created in the repository root mirroring the source structure.  Each such directory will contain an `index.html` for the content of the page, and a `history.html` with a summary of the changelog of the page.

Each `src` subdirectory which does not have an explicit `index` will have a simple index built.  This provides a list of all the documents and any deeper subdirectories.

Any file whose name starts with `DRAFT_` will be built, but not automatically added to any index or navigation.

### Error pages

For compatibility with eg. GitHub Pages, source files whose name without extension is three digits (`[0-9]{3}`) will be treated specially.  The index of such pages will not be placed in the page's subdirectory, but will mirror the location and name of the source file itself.

Eg. the file `src/404.md` will result in `404.html` being built in the site root.  However, it will still have and link to a `404/history.html` file.

### Redirects

If pages are found in the commit log to have been renamed at all, then for each previous name, additional pages are created with an HTML meta redirect to the new URL.

### Navigation

With some exceptions, for each file and directory in the `src/` root itself, an entry will be added to the site's main navigation.

The exceptions are:

1. Directories which are empty or contain only drafts.
2. Numeric error pages, as described above.
3. The file `src/footer.html`, as described above.

### Customising the design

The generated HTML code is static, and mostly pre-defined by the engine.  Customisation of the site design, therefore, is done through CSS.  This is achieved by creating `.css` files in a `css` directory in the repository root.  Any files in this directory will automatically be `link`ed in the HTML `head` of every page.

The page footer can be customised by providing a `src/footer.html`, the content of which will be inserted into the `<footer>` element of every page.
