# Katamari
<img align="right" src="/etc/katamari.jpg" width=300/>

[![Clojars Project](http://clojars.org/me.arrdem/katamari/latest-version.svg)](https://clojars.org/me.arrdem/katamari)

> King of All Cosmos: We are moved to tears by the size of this thing.

**TL;DR** A file sets based build tool. In Clojure, for Clojure.

## Manifesto

Build tools are tricky things.
It's often said that the [two hardest problems in computer science are cache invalidation, naming things and off by one errors](https://twitter.com/codinghorror/status/506010907021828096).
Unfortunately, build tools run right smack into both of these problems.

Programmers, well adapted to wrangling complexity and pipelines, do all kinds of things when packaging and building their software.
Build systems are in the most common case mere shell scripts used to glue together programs of all kinds.
The essential problem of gluing together Unix programs is that each program could have arbitrary effects.
There's no good way to understand what configuration a task consumed, or what results it produced.

"real" build tools try to solve this problem by rendering build steps declarative, so that the declared dependency relationships can be used to derive incremental compilation behavior.
This is the approach taken by Bazel, Buck, Pants, Maven, Boot and more.

As a Twitter employee I spent a lot of...
quality time with Pants and came to appreciate the repeatability properties it provided, and its change detection facilities.
Unfortunately because Pants and friends try to be efficient general purpose solutions for many toolchains, their particular machinery is greatly complicated by the needs of those tools.
For instance Pant's Java compilation pipeline is inextricably bound to Scala's incremental compilation engine because that was a high priority for the Pants developers.
As these tools are institutional, they're thinly documented at best.
All their primary customers are internal, and cultivating an external user base is nobody's priority.

Many build tasks are honestly pretty trivial, and just get re-computed because it's more engineering effort than it's worth to write special purpose change detection machinery.
The hope of Katamari is that, by "firing your customers" the size of the problem domain can be meaningfully constrained and a simple system with adequate performance can be produced just by leveraging content addressing of build products.

## Documentation

- [System Architecture](/docs/system-architecture.md)
- [Build Graph & Targets](/docs/build-graph.md)

## License

Copyright © 2018 Reid "arrdem" McKenzie

Distributed under the [Eclipse Public License](/LICENSE) either version 1.0 or (at your option) any later version.
