# learning-pl

A list of resources for learning programming languages.
All links to papers and books direct you to free online pdfs unless otherwise noted.

# Beginner stuff

[Types and Programming Languages](https://github.com/MPRI/M2-4-2/blob/master/Types%20and%20Programming%20Languages.pdf)

* [Recommendations from mgree](https://discourse.elm-lang.org/t/repl-for-untyped-lambda-calculus/5802/8?u=alienkevin)

You might like [my course notes from CS 131](https://cs.pomona.edu/~michael/courses/csci131s18/), the PL course I’ve taught a few times now. It doesn’t go past the STLC and is pretty implementation focused. I’d rate it as decidedly less difficult than TAPL, which I assign as an optional, supplementary textbook.

Shriram Krishnamurthi’s [PLAI](https://cs.brown.edu/~sk/Publications/Books/ProgLangs/2007-04-26/) book is another nice approach. It’s not written from quite the same formalist perspective as Benjamin Pierce’s TAPL. (Disclosure: Shriram was my undergraduate advisor, and Benjamin was my PhD advisor.)

Matthias Felleisen and Matthew Flatt’s [Programming Languages and Lambda Calculi](https://www.cs.utah.edu/~mflatt/past-courses/cs7520/public_html/s06/notes.pdf) is another well grounded, theory-based approach, with an emphasis on abstract machines.

Jeremy Siek wrote a [nice blog post about notation](http://siek.blogspot.com/2012/07/crash-course-on-notation-in-programming.html) that might be helpful, too.


# Type Inference

* [Recommendations from evancz](https://discourse.elm-lang.org/t/sim-a-delightful-language-for-circuit-design/5737/16?u=alienkevin)

Anyway, I have some resources on type inference! I recommend reading [The Essence of ML Type Inference](http://gallium.inria.fr/~fpottier/publis/emlti-final.pdf) which comes with a prototype implementation:

The propotype is here:
https://github.com/enaudon/TAPL/blob/master/archives/mini-prototype-0.3.tar.bz2

The documentation here:
https://web.archive.org/web/20161013232730/http://yann.regis-gianas.org/public/mini/

I know for Elm, using the Union Find algorithm is really important for performance of global inference on files of 500+ lines. I don’t think I implemented this for about two years, until programs started getting longer in practice, but I bring this up because Union Find requires mutation for the fastest implementation. I don’t know enough about your language to know exactly if you need that, but you may need to use a language like OCaml or Haskell to do that specific optimization. Languages like Scala cannot use Union Find too much because it does not work so well with OO-style sub-typing, so they have to do other things to try to improve performance. Point is, you can get by without, but I’m not personally an expert on what is needed outside of HM(=). I hope that is helpful information!

I also ran into a really impressive language called [Lucid Synchrone](https://www.di.ens.fr/~pouzet/bib/chap_lucid_synchrone_english_iste08.pdf) many years ago, and I recommend reading through that paper! I recall being really impressed that they had used a highly constrained “reactive system” to get really solid and practical proofs about cycle counts and maximum hardware necessary for a given program, but it’s been 6 or 7 years since I’ve read it myself!

# Implement Higher Order Functions in imperative languages

# Closure Conversion

Implement nested functions by making closures and hoist all functions to the top level. Closures is made up of the function and its environment (the variables it references).

[Slides by Michel Schinz](http://lampwww.epfl.ch/teaching/archive/advanced_compiler/2007/resources/slides/act-2007-05-closure-conversion.pdf)

# Defunctionalization

Compile higher order functions into first order functions. Typically followed closure conversions which handles any free variables.

[Wikipedia page](https://www.wikiwand.com/en/Defunctionalization)

[A practical example](https://blog.sigplan.org/2019/12/30/defunctionalization-everybody-does-it-nobody-talks-about-it/)

# Upvalues

You can also implement closures at the Virtual Machine level following Lua 5.x's approach.

[Crafting Interpreters' Closure implementation](https://craftinginterpreters.com/closures.html)

[Closure in Lua](https://pdfs.semanticscholar.org/73a2/e3c03f799956aa5a3188e4eb35c90977a471.pdf)