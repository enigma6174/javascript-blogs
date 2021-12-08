---
layout: post
title: Iterator And Iterables
subtitle: A Deep Dive Into The Concept Of Iterators And Iterables In JavaScript
tags: [iterables, arrays]
readtime: true
gh-repo: enigma6174/javascript-blogs
gh-badge: star
---

An **iterable** is a JavaScript object that can be looped over using the **for-of** loop. This is a very basic non technical definition. Technically speaking, JavaScript objects that implement the **iterable** protocol and have an **@@iterator method**.

![javascript-iterables](/javascript-blogs/assets/img/js-iterators.png)

{: .box-note}
**Iterable** can also be defined as an interface that allows a JavaScript object to be accessible sequentially like a list by implementing the Symbol.iterator method.

{: .box-note}
**Iterators** are JavaScript objects that can access items from a collection one by one and also keep a track of it's current position. 

The **iterable protocol** allows JavaScript objects to define or customize their iteration behavior for example, what values are looped over (using the ```for...of``` construct). In order to be an **iterable** the object must implement the **@@iterator** method, which means that the object (or one if it's objects up the prototype chain) must have a property with ```@@iterator``` key which is available via the constant ```Symbol.iterator```.

Whenever an object needs to be iterated, it's ```@@iterator``` method is called with no arguments and the returned **iterator** is used to obtain the values to be iterated.

The **iterator protocol** defines a standard way to produce a sequence of values (either finite or infinite) and potentially a return value when all values have been generated.

An object is an iterator when it implements a ```next()``` method as per the following semantics:

![javascript-iterator-next](/javascript-blogs/assets/img/js-iterator-next.png)


##### Common JavaScript Objects That Use Iterables
- Arrays
- Strings
- Maps
- Sets
- NodeList


