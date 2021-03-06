# Programming in Scala, First Edition
by Martin Odersky, Lex Spoon, and Bill Venners

스칼라의 창시자로부터 배우는 스칼라 (저자직강?)

http://www.artima.com/pins1ed/

## 밑줄긋기

  * Chapter 1 A Scalable Language
    * Instead of providing all constructs you might ever need in one "perfectly complete" language, Scala puts the tools for building such constructs into your hands.
    * Scala lets you add new types that can be used as conveniently as built-in types.
    * If we were forced to name just one aspect of Scala that helps scalability, though, we'd pick its **combination of object-oriented and functional programming**.
    * Functional programming is guided by two main ideas.
      * The first idea is that **functions are first-class values**.
      * The second main idea of functional programming is that **the operations of a program should map input values to output values rather than change data in place** .
    * **Immutable data structure** are one of the cornerstones of functional programming.
    * Another way of stating this second idea of functional programming is that **methods should not have any side effects**.
    * Scala's syntax avoids some of the boilerplate that burdens Java programs.
    * Scala's **type inference** is another factor that contributes to its conciseness.
    * Edsger Dijkstra said, **testing can only prove the presense of errors, never their absence**.
    * At the surface level, Scala adopts a large part of the syntax of **Java** and **C#**
    * Scala also owes much to other languages. Its **uniform object model** was pioneered by **Smalltalk** and taken up subsequently by **Ruby**.
    * Its idea of **universal nesting** (almost every construct in Scala can be nested inside any other construct) is also present in **Algol**, **Simula**, and, more recently in **Beta** and **gbeta**.
    * Its approach to **functional programming** is quite similar in spirit to the **ML** family of languages, which has **SML**, **OCaml**, and **F#** as prominent members.
    * Many **higher-order functions** in Scala's standard library are also present in **ML** or **Haskell**.
    * Scala's **actor-based concurrency library** was heavily inspired by **Erlang**.
    * We think you'll find it a rewarding intellectual experience that will expand your horizons and make you think differently about program design.
  * Chapter 2 : First Steps in Scala
    * In fact, one of the main aims of this book is to help you become as comfortable with the functional style as you are with imperative style.
    * One of the main characteristics of a functional language is that **functions are first class constructs**.
  * Chapter 3 : Next Steps in Scala
    * arrays in Scala are accessed by placing the index inside parentheses, not square brackets as in Java.
    * One of the big ideas of the functional style of programming is that **methods should not have side effects**. A method's only act should be to compute and return a value. Some benefits gained when you take this approach are that methods become less entangled, and therefore more reliable and reusable. Another benefit (in a statically typed language) is that everything that goes into and out of a method is checked by a type checker, so logic errors are more likely to manifest themselves as type errors. **Applying this functional philosophy to the world of objects means making objects immutable**.

# Effective Scala
by Marius Eriksen, Twitter Inc.

http://twitter.github.io/effectivescala/


---


참조

  * First-class function: http://en.wikipedia.org/wiki/First-class_function

> this means the language supports passing functions as arguments to other functions, returning them as the values from other functions, and assigning them to variables or storing them in data structures.

  * Scala by example [pdf](pdf.md) http://www.scala-lang.org/docu/files/ScalaByExample.pdf

  * Coursera https://www.coursera.org/course/progfun

http://metagear.de/articles/scala-exercises/index.html