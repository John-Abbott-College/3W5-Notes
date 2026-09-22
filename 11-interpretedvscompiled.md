
# How does JavaScript Work?

JavaSCRIPT is a SCRIPTING language, but what exactly does that mean? How does it differ from traditional compiled languages?

## Compiled Languages

Compiled languages work like this:

- human-readable code translated to machine-readable code (bits)
- step before being able to run
- catch errors - fix once, run many times, but have to regenerate executable
- precompiled runs faster

Some examples include:

- Java
- C#

## Scripting Languages

Scripting languages, on the other hand, function differently:

- interpreters translate into machine-readable code on the fly
- always rely on the source-code
- hit same error every run, but just reload once fixed.
- translating less performant in theory (but caching, optimizations)
- Line getting blurred (compile JavaScript into an exec, very fast compilation JIT)

Some examples include:

- JavaScript
- PHP
- Python


# Where can I run JavaScript?

## In the browser

avaScript was originally designed to run ONLY in browsers. All browsers have a JS Engine that allow you to execute the code.

For example, in firefox and chrome, the Javascript engine that's used is spider monkey and v8.

## But what happens if we want to run JavaScript outside of the browser?

Well in 2009, a smart dude named Ryan Dahl took the open-source JavaScript engine that was in chrome and embedded it inside a C++ program. He called this Node.

Now with Node we can run JavaScript outside of a browser allowing us to use JavaScript for the backend for our web and mobile applications.

This innovation is largely why it continues to establish itself as the most popular coding language.

