---
layout: post
title: "Haskell code coverage on Coveralls"
description: "hpc-coveralls release announcement: Haskell code coverage support for coveralls.io"
category: haskell
tags: [haskell, hpc, coverage, coveralls]
---
{% include JB/setup %}

This is a quick post to announce the first version of [hpc-coveralls](https://github.com/guillaume-nargeot/hpc-coveralls/),
a small project I've been working on during the past few days,
which provides functionality to send [hpc](http://www.haskell.org/haskellwiki/Haskell_program_coverage) code coverage report for
Haskell projects to [coveralls.io](http://coveralls.io/).

In order to use hpc-coveralls with [Travis CI](http://travis-ci.org),
you just have to add the following commands to your `.travis.yml` file.

##### 1. Install of hpc-coveralls in the *before_install* section:
{% highlight yaml %}
  - cabal install hpc-coveralls
{% endhighlight %}

##### 2. Configure cabal for code coverage in the *script* section:
{% highlight yaml %}
  - cabal configure --enable-tests --enable-library-coverage
  - cabal build
  - run-cabal-test [optional-cabal-test-arguments]
{% endhighlight %}

Note that you have to use the `run-cabal-test` command instead of the usual
`cabal test` command, as hpc 0.6 makes the build fail (bug which should be
fixed in hpc 0.7, not yet available on Travis CI).

##### 3. Finally, call hpc-coveralls in the *after_script* section:
{% highlight haskell %}
  - hpc-coveralls [your-test-suite-name]
{% endhighlight %}

That's all!

Please note that there is currently one limitation: due to the fact that
Coveralls doesn't support yet partial line coverage, hpc-coveralls uses the
following convention to convert hpc detailed coverage information into
coveralls line hit count:
 - `0` : the line is never hit,
 - `1` : the line is partially covered,
 - `2` : the line is fully covered.

All contributions are welcome, so [fork me on GitHub](https://github.com/guillaume-nargeot/hpc-coveralls)!
