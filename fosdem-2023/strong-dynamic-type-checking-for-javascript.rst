Strong Dynamic Type Checking for JavaScript
===========================================

Actual situation
----------------

Strong type-checking implies there is a binding between a variable and type, so each time you use this variable it will have the corresponding time.
Javascript is a dynamically typed language, so it is unpredictable.

Typescript addresses this issue by adding type to Javascript, it has exponential growth over the 10 previous years.
The developer experience with typescript is good, thanks to, among others, easy refactoring.
Typescript type safety can be easily defeated because mechanism just says to compiler "I know what I am doing" but it is false.
You also need to deal with a lot unpredictable things like Browser API, client-side stored data and, last but no least, user inputs.

Sadly, the Typescrit compiler cannot help as it occurs at runtime due to dynamic behavior.
Type errors should be runtime errors.
And we need to validate all the time, not only once.

Object Model
------------

Object Model is a library to add strong dynamically typed to Javascript.
To use this library, you need to:

1. Define model which will represent your dynamic types.
2. Bind the models to data.
3. Now, your data is type safe, if you try to give a boolean to an int, you will get a ``TypeError``.

It underlyingly uses JavaScript ``Proxy``, which were introduce in 2015 with ES6, which can check assigment for you.
Models can check types but also values!

Sadly, this library comes with performance penalty on data with very frequent mutations, you should avoid using it on data mutating more than 100 times per second.

As a conclusion, you should use both static and dynamic checking.
