## Don't indent Clojure code

I first came to the [Clojure programming language](https://clojure.org/) from a most recent background heavy in Python and Python-like languages.  As such, I was (and still am) a strong advocate of indentation of blocks to denote scope and context of code, and particularly of so-called "hard" tabs as a token representing "one indentation level".

```python
def my_function(
		some_parameter,
		another_parameter,
		optional_parameter = "There's a horse walking past as I write this"
		):
	"""
		It's my function, I'll do what I like!
	"""
	do_stuff(
		foo = some_parameter,
		bar = {
			baz: another_parameter,
			fez: optional_parameter,
			},
		)
```

Thus it grated on me when I first approached Clojure, with its explicit and exclusive use of spaces for indentation, and the frequently inconsistent width and rules for such.  That was, until I had a realisation:

*Clojure doesn't have indentation, it only has alignment and non-alignment.*

While many confuse or conflate the terms indentation and alignment when used in the context of source code, including in the [Clojure community style guide](https://guide.clojure.style/), there is a clear difference between the semantics of the terms.

Indentation as a term describes code's _position_ relative to its _container_, whereas alignment describes instead how code _relates_ to its _siblings_.

The term indentation is indeed used by the Clojure style guide and other such places to refer to positioning code in relation to eg. form opening syntax.  However, I argue that this idea of indentation is irrelevant to Clojure, and that solely thinking in terms of alignment leads to clearer thinking, and clearer code.

### Alignment

As described by the [Gestalt principles](https://en.wikipedia.org/wiki/Gestalt_psychology), human beings tend to group individual items in terms of their proximity to each other, and treat them as a single cognitive unit.  This is also true when individual items are laid out as a continuous path.

Thus, when we lay out code we should be mindful that when we align two terms, our brains will instinctively group those tokens into a single semantic collection.  This can reduce the cognitive load necessary to understand the code, but conversely can *increase* the cognitive load if one needs to override those instincts should the terms _not_ be semantically equivalent.

The Clojure style guide references this tendency when [discussing function arguments](https://guide.clojure.style/#vertically-align-fn-args):

> Vertically align function (macro) arguments spanning multiple lines.

> ```clj
> ;; good
> (filter even?
>         (range 1 10))
> ```

> The reasoning behind this guideline is pretty simple - the arguments are easier to process by the human brain if they stand out and stick together.

However, the very next section instructs that, should one not have enough horizontal space to align the arguments so, one should instead:

> Use a single space indentation for function (macro) arguments when there are no arguments on the same line as the function name.

> ```clj
> ;; good
> (filter
>  even?
>  (range 1 10))
> ```

While _technically_ the arguments are still aligned, by aligning them also with the function name itself, we are conflating their purpose even as their semantics are clearly different.  The guide even admits that this makes them essentially indistinguishable from a "regular list literal", which is correct syntactically, but semantically unhelpful.

### No body

The purpose of falling back to "use a single space indentation", aka aligning arguments with the function name, appears to be to distinguish regular arguments from the "body" of a function (macro) call.

However, there doesn't appear to be any clear definition of what counts as "body".  The style guide provides these as examples of "good" code:

```clj
(when something
  (something-else))

(with-out-str
  (println "Hello, ")
  (println "world!"))

(or
 ala
 bala
 portokala)
```

All of these are macros, all of them take an arbitrary number of extra arguments, so why is `or` not considered to have a body?

Certainly, `when` and `with-out-str` are defined with parameters named specifically `body`, but then what of `cond` or `as->` which are also named in the document as to be indented as they have a body?  The parameter in question for those is named `clauses` and `forms`, respectively, so maybe we can check for those too?  Any more?  Almost certainly.

Perhaps we can instead promote `or` to be considered having a body, and make the defining characteristic of a "bodied" function/macro that they take an arbitrary number of parameters?

```
user=> (doc def)
-------------------------
def
  (def symbol doc-string? init?)
...
```

Crap.

### Non-alignment

So rather than try to develop a convoluted system of rules, or a necessarily incomplete list of special case functions and macros, I propose three simple rules:

1. Align semantically equivalent things
2. **Do not align** semantically dissimilar things
3. Don't talk about "indentation"

These rules intentionally do not specify distances or directions.  Nor do they specify language structures or features.  Their purpose is only to emphasise that it is the semantic arrangement of the code which aids understanding, not the implementation details or exact distances from here nor there.

So by these rules, all of the following could be considered equally valid:

```clj
(or ala
    bala
    portokala)

(or
  ala
  bala
  portokala)

(when something
  (something-else))

(when something
    (something-else))

(with-out-str
  (println "Hello, ")
  (println "world!"))

(with-out-str (println "Hello, ")
              (println "world!"))
```

You may balk at some of these, I know I did.  But when you do instinctively recoil in revulsion, ask yourself if the unusual alignment objectively hampers understanding the code?  If so, then perhaps we can analyse that to discover an exception or a greater rule.  Though in any case, I don't expect it would have anything to do with "indentation"!

#### Not only, but also

Other existing guidelines naturally flow from these rules, such as those for aligning [bindings](https://guide.clojure.style/#bindings-alignment), [map keys](https://guide.clojure.style/#map-keys-alignment), or literal collections:

```clj
;; list literal
(1
 2
 3)

;; vector literal
[1
 2
 3]

;; set literal
#{1
  2
  3}
```

Further, by following only such rules of semantic alignment, we can gain additional benefits when laying out our data, eg:

```clj
;; A map of data where related values are aligned, but unrelated are not
{:id 123
 :title "Foobar"
 :width    1
 :height 234
 :depth   56
 :my.project.author/name  "Foo Barbaz"
 :my.project.author/email "foo@bar.baz"}
```

[Hiccup](https://github.com/weavejester/hiccup) too, with its structural similarity to function/macro calls, can benefit from semantic non-alignment:

```clj
;; Using non-alignment of the keyword, props, and children
;; allows us to see the document structure intuitively:

[:div {:style "color: red"}
  [:marquee
    [:font {:color "hotpink"}
      "Hello"
    [:blink "World!"]]]]

;; In comparison to a strict indentation equivalent
;; which visually commingles props and children:

[:div
 {:style "color: red"}
 [:marquee
  [:font
   {:color "hotpink"}
   "Hello"
  [:blink "World!"]]]]
```

### Conclusion

So, if you're developing with Clojure (or perhaps more generally with any LISP dialect, I couldn't say), I ask that you consider eschewing the very concept of indentation!  Push it from your mind, ban it from your code linter, and remove it from your documentation spell-checker!

Embrace instead aligning - and non-aligning - your code along semantic lines.  It may not always be as simple, but, when you come to revisit the code in 10 years' time, I believe your tired brain will thank your past self for making the effort to enshrine the code's semantics in the structure itself.
