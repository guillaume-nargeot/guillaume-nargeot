---
layout: post
title: "Generalised Hamming Numbers"
description: "Haskell solution to Project Euler problem 204, on Generalised Hamming Numbers"
category: Project-Euler
tags: [project-euler, puzzle, haskell]
---
{% include JB/setup %}

Solving [Project Euler problem 204](http://projecteuler.net/problem=204 "Project Euler problem 204") turned out to be rather simple for a problem in the 200~ series.<br/>
Counting generilized Hamming Numbers is similar to counting coin combinations in [problem 31](http://projecteuler.net/problem=31 "Project Euler problem 31"), but with products instead of sums.<br/>
Below is the original sum counting algorithm:

```haskell
sumCombinationCount 0 _ = 1
sumCombinationCount _ [] = 0
sumCombinationCount r (c:cs) = if r < 0
    then 0
    else sumCombinationCount (r - c) (c:cs) + sumCombinationCount r cs
```

Adapting the recursive algorithm from sum counting to product counting is quite straightforward:

```haskell
prodCombinationCount limit = prodCombinationCount' 1 1
    where prodCombinationCount' count _ [] = count
          prodCombinationCount' count p (m:ms) = if p > limit
              then count - 1
              else prodCombinationCount' (count + 1) (p * m) (m:ms)
                 + prodCombinationCount' 0 p ms
```

Within the given conditions of the problem, this algorithm runs in roughly half a second on my laptop.

Below is the code for a standalone solution:

{% gist 8931069 Problem214.hs %}

The [full solution](https://github.com/guillaume-nargeot/project-euler-haskell/blob/master/src/ProjectEuler/Problem204.hs "Project Euler problem 204 solution on GitHub") is also available on my [Project Euler Haskell solutions repository on GitHub](https://github.com/guillaume-nargeot/project-euler-haskell "Project Euler Haskell Solutions on GitHub").

To go one step further, the problem can also be solved by using logarithms to transform the product counting problem into a sum counting problem.
Kudos to those who came up with this approach!

After earning the "Daring Dozen" award on this one -- 12 problems of 3-digit IDs -- I'm now only 13 solutions away from reaching level 4. There's no time to rest!
