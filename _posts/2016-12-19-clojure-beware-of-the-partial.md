---
id: 776
title: 'Clojure: beware of the partial'
date: 2016-12-19T00:00:00+00:00
author: Tiago Espinha
guid: https://www.tiagoespinha.net/?p=776
permalink: /2016/12/clojure-beware-of-the-partial/
categories:
  - Software
tags:
  - clojure
---
At some point in time while using [Liberator](http://clojure-liberator.github.io/liberator/) to build *semi-RESTful* APIs, I found myself in a pickle. Essentially, the Liberator library allows you to build an API by specifying a number of handlers (effectively functions) for things like handling a malformed request, handling a non-existant request, and also allowing handlers for determining what *are* malformed or non-existant requests.
{: style="text-align: justify;"}

This approach to building an API is pretty straight forward. To help it, **Liberator** passes a "*context*" argument into each of these handlers by default which carries information such as HTTP headers and whatever else you feel like adding to it throughout the validation pipeline until the request gets handled by the "*handle-ok*" handler.

Then, at some point or another, you will be wanting to pass more arguments into these handlers. Clojure (and functional programming in general) discourage the use of global mutable state and encourages single-purpose, idempotent and side-effect free functions, meaning that you should be able to run the same function twice, with the same arguments, and get the same outcome (this usually will not be possible if the function depends/operates on shared global variables). Then what can you do? Liberator expects single-argument handlers to which it can pass its "*context*" argument but we want to also pass additional arguments to it which will be evaluated and/or resolved at runtime.

After some googling on the issue, I found out a solution: partial functions! When partial is applied on a particular function with a set of arguments, rather than evaluating that function, it will create a wrapper function around it which will pass in the specified arguments plus whatever other arguments are passed in when the function is evaluated. It works something like this:

```clojure
(partial is-malformed? config)
```

In this case, ```partial``` will return another function which will have ```config``` as first argument and also support a **variable** amount of arguments. Great! This works, it solves the problem. Liberator will call the returned function, pass the *context* into it, et voilà! Bob's your uncle, klaar is Kees, job's a good'un.

# But wait!... the title says beware!

Yes, that's because in this case, if you have a preset number of additional arguments that you'd like to pass into your handler, you should **NOT** be using partials! You see, a ```partial``` application results **always** in a variadic function, or a function which supports a variable number of arguments. When you have a varargs function, Clojure will create a list out of the arguments (every. single. time.) and then use ```apply``` to push those arguments into the function. This has a particular performance impact which you should avoid if you can, and... you can!

# So how should it be done?

Hey, it's **functional** programming right? Just evaluate an additional (potentially even anonymous, since it's so small) function which takes a single argument (to validate the requirement for Liberator) and wraps around the handler you've created passing in both the argument (which you will capture as a closure into the anonymous function) and the context argument coming from Liberator. In the end, the same example as above would look something like this:

```clojure
(fn [ctx] (is-malformed? config ctx))
```

Or if you want to use the [reader macro](https://en.wikibooks.org/wiki/Learning_Clojure/Reader_Macros) and make the code more compact:

```clojure
#(is-malformed? config %)
```

And that's it! This is about as efficient and compact as you can make it.

# To conclude...

Don't use ```partial``` unless you have a true need for a **variable** number of arguments at **runtime**. If you need a function which takes more arguments that what a library/whatever passes to your function, just wrap it in another function and enclosure your additional arguments into it.
