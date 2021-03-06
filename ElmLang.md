# Elm

## Notes

* Compiled language that kinda looks like coffeescript.
* Highly functional, taking a lot of tenants from Haskell.
* Due to the compilation, a `Main.elm` and an `Main` function as 
an entry point is pretty common.
* One of the largest differences from Elm to Haskell is Elm is eager where Haskell is lazy
* The VirtualDom actually calls out to JS's native VDOM
* Frontend work can be tricky to start but, when you have a simple framework it directs your start.
  * lot's of Elm starts by defining a model, building the view, and creating messages that the view responds to.
* The not equal op, like most languages (`!=`) is actually: `/=`

## Conventions

* Namespacing imports seems like a good way of building an app.
  * This can be done during the module exports phase:
  * ex: `module SomeComponent.ComponentName exposing (some_func)`
* Overall architecture often follows the following conventions:
  * An initial model, an initializer, a view function, an update function, and a subscriptions function.
  * An easier way of thinking about this: model, update, view.
* Messages can pass from one module to another much like an event bus pattern.
* Subscriptions are ways for the application to 'listen' to external input.
  * This can be mouse/kb events or something like a Websocket event.

## Functions

* Anonymous or 'lambda' fn's start with a backslash
  * ex: `\n -> n + 1`

## The Model

### Notes

* It's often normal to have an initialModel to be given to the app when it's launched/created

## The View

### Notes

* Collection of functions that compose a virtual dom representation of the dom
* The VirtualDom actually calls out to JS's native VDOM

## The Update

### Notes

* Often times the initial update that's written will simply return the initial model.
* Usually takes a msg, a model and returns a model (the updated model)
* Can also be thought of as a list of messages that the view can send the program.

## General Syntax

* `module` statement acts like a module exports in es6
* `import` used to import modules and expose functions to the script.
* Backticks can be used to force a function to be [infix][1]
* Like many Lisp like languages, function application is performed with spaces, not parens.
  * `bar 5 1` versus `bar(5, 1)`
* All functions are curryable by default.
  * also known as 'partial applications' in the language
  * Since the power of currying is all over the language, one has to weight composition over readability.
  * Often times written with type declarations above the function
    * ex: `double : Int -> Int`
  * Terminology when reading function declaration can be a little different.
    * ex: `List.map : (a -> b) -> List a -> List b`
    * is read as: 'List dot map has type a goes to b, goes to list of a, goes to list of b.'

## Lists

* `++` concats two lists together. Each side of the operator must be a list though
  * this can be expensive because it has to walk the entire length of the prepending list.
* `::` is a cons operator and will therefore add the item to the left of the op to the list on the right.
  * example: in a case statement of a list we could use `x::xs` to assign `x` to a single val and `xs` to the rest of the list.
  * This is actually a super common pattern.
* There are some handy methods built into `List`:
  * `List.head list` returns the first element of the list
  * `List.tail list` returns all but the first element of the list (opposite of above).
  * `List.maximum list` finds the largest 'element' in the list (SUPER handy)
  * `List.member item list` returns true or false if the item is in the list (equally handy)
* Lists, like in Ruby, can be built using range operators `[1..22]` with returns the sequential list

### Tuples

* A type of list but instead of being surrounded by square brackets, surrounded with parens.
  * ex: `([1,2], [2,3], [4,5])`
* Unlike a list, tuples can contain multiple different types.
* Each element must have the same amount of data.
  * This is really when you want to use a tuple, when you know the _exact_ structure of your data.

## Types

* Elm runs with type inference so no need to tell the compiler that an obvious Int is an Int
* All types in Elm are denoted using Capital case (i.e.: `Float` or `Int`).
* Type variables in Elm are written in non capital case (i.e.: `a`) and are of _any_ type.
  * these are usually written as single char variables (`a`, `b`, etc)

## Pattern Matching

* Represented in the language in the form of case expressions.
* Can be done on any data type.
* The compiler will warn if their are cases not taken care of by the case.
  * This can be taken care of by using the `_` wildcard op at the end of the statement.
  * this operator is ALSO the throwaway parameter operator where we don't care about the parameter passed.
* `let <binding> in <expression>` allows the programmer to bind anything to vars, even in expressions.
  * anything assigned in the binding step will be accessible after the `in` declaration.


[1]: https://wiki.haskell.org/Infix_operator
