---
layout: post
title: "A few weeks using Haskell"
description: "Thoughts on Haskell after a few weeks usage to solve Project Euler problems"
category: haskell
tags: [project-euler, haskell, functional programming]
---
{% include JB/setup %}

It is now two months since I started learning Haskell, primarily by solving
Project Euler problems and reading [Learn You a Haskell for Great Good](http://learnyouahaskell.com/ "Learn You a Haskell for Great Good").
With now a little more than [30 solutions](https://github.com/guillaume-nargeot/project-euler-haskell/ "My Haskell solutions to Project Euler problems") implemented in Haskell,
out of the 90 that I've solved so far,
I'm becoming more familiar with the language.
After a four-year break in solving Project Euler, this fresh restart has been mind opening.

The last period during which I regularily solved problems, I was using Clojure,
transitioning from using Ruby with which I had implemented my first
[60~ solutions](https://github.com/guillaume-nargeot/project-euler/).
As a starting point to learn Haskell, I thought it would be a good idea to try
porting the code from my solutions originally implemented in Clojure.
I soon realized the code I wrote at that time was quite difficult to understand,
and the problem was *recursion*: a good part of the algorithms
were implemented with explicit recusion using the `loop` construct...

Recursion may well be one of the functional programming foundations,
but it seems to sometimes make algorithms even more difficult to understand
than data mutating for-loops in imperative programming languages.

After starting to implement new solutions for unsolved problems, I've found
that Haskell made it really easy to avoid explicit recursion to write complex
algorithms, by instead using higher order functions such as `map`, `foldl`, `filter`,
`scanl`, `groupBy`, `zipWith`, and other list combinators.

The fact that functions are curried by default also allows to chain composed
functions in a very succinct way as opposed to Clojure in which one would have
to use `partial` in order to curry functions, or write anonymous functions.

All this conforts me in thinking that Haskell is a very good language to
implement functional algorithms using elegant abstractions.

Finally, I've found that the performance of Haskell was better and far more
predictable than Clojure, allowing to spend more time focusing on algorithms
core logic rather than implementation details and performance tuning, which
Clojure dynamic nature makes quite obscure.

This said, I'd really like to soon move on some real world project to get a
better idea of what it is to develop software with Haskell.
