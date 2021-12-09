---
layout: post
title: Array Basics
subtitle: Understand How To Work With Arrays And Basic Array Operations
tags: [iterables, arrays]
readtime: true
gh-repo: enigma6174/javascript-blogs
gh-badge: star
---

**Arrays** are simply a list of items! In JavaScript, a single array can hold different types of data which means an array can have **Numbers**, **Strings**, **Boolean** etc.

> A JavaScript array can even have arrays and objects as it's array elements!

Unlike many other programming languages, in JavaScript, arrays are _dynamic in nature_. This means that array size need not be specified when an array is created. And elements can be added to or removed from an array without any explicit sizing and resizing of the array by the developer!

A JavaScript array is a very important data structure and as a developer it is one of the most important and frequent ones you will work with. 

{: .box-note}
**Note** Array elements are **0-indexed** which means that the index (i.e. _position in the array_) of the first element is 0, the index of the second element is 1 and so on. Any element in the array can be accessed using the square bracket notation **[i]** where **i** is the index of the element we want to access. For example if we want to access the 2nd element (index 1) of an array **buffer** the code snippet will be ```buffer[1]```. Also, every array has an attribute called length which returns the length of the array. So if the array **buffer** has 5 elements, ```buffer.length``` will return 5.

Here is some basic code to get started with arrays!

{% highlight javascript %}
// Basic array initialization
const array1 = [1, 2, 3.5, -0.044, 2.3e3, 45e-2];
console.log(array1);

// Another way to initialize an array
const array2 = Array(5, 2);
console.log(array2);

// This will create an empty array of length 5
// Default initialized values will be undefined
const array3 = Array(5);
console.log(array3);
console.log(array3[0]);

// Alternative way to create array
const array4 = Array.of(1, 2);
console.log(array4);
console.log(array4[0]);

// Does not work like Array(n)
// Array.of(i) will create an array with a single element i
const array5 = Array.of(5);
console.log(array5);
console.log(array5[0]);
{% endhighlight %}

#### The output of the above code

![javascript-arrays-basics-create](/javascript-blogs/assets/img/arrays-basics-create.png)

As mentioned earlier, JavaScript arrays can contain different items. This is not limited to just different data types in an array like **Numbers**, **Strings**, **Booleans** etc. but a JavaScript array can also hold **Objects** and **Arrays** as array elements! The follwing examples will make things clearer

{% highlight javascript %}
// Array of mixed items
const mixedArray = [
  "hello",
  "world",
  34,
  0.011,
  false,
  null,
  ["another", "array"],
  { key: "value" },
  { key: "value" },
  [{ key1: "value1", key2: "value2" }],
];
console.log("mixedArray", mixedArray);
console.log(`mixedArray.length : ${mixedArray.length}`);
console.log("mixedArray[6]", mixedArray[6]);
console.log("mixedArray[7]", mixedArray[7]);
console.log("mixedArray[8]", mixedArray[8]);
console.log("mixedArray[9]", mixedArray[9]);
console.log("mixedArray[6][0]", mixedArray[6][0]);
console.log("mixedArray[9][0]", mixedArray[9][0]);
{% endhighlight %}

#### The output of the above code

![javascript-arrays-basics-multi](/javascript-blogs/assets/img/arrays-basics-multi.png)

There are other array like objects that implement the **iterable** protocol for example **NodeList** and **HTMLCollections** but the difference is that while we can iterate over the elements many array operations are not supported by these array like objects. Hence, it is important to convert any iterable to an array.
JavaScript allows us to convert any array like object to an array using the ```Array.from(v)``` method where **v** is the array like object (or iterable) that needs to be converted.

{: .box-note}
Consider the following example:  
**NOTE:**
The accompanying HTML code for the following is not included but you can have a look here:
[javascript-arrays-basics-github](https://github.com/enigma6174/javascript-course/blob/main/arrays/index.html)

{% highlight javascript %}
// Get a list of all li items in DOM
// This returns an array-like object
const listItems = document.querySelectorAll("li");
console.log(listItems);

console.log('After Conversion')

// Convert the array-like object to JavaScript array
// Array.from() is used to convert iterables into arrays
const listItemsArray = Array.from(listItems);
console.log(listItemsArray);

const moreListItems = document.getElementsByTagName("li");
console.log(moreListItems);

console.log('After Conversion')

const moreListItemsArray = Array.from(moreListItems);
console.log(moreListItemsArray);
{%  endhighlight %}

#### The output of the above code

![javascript-arrays-basics-convert](/javascript-blogs/assets/img/arrays-basics-convert.png)

Just before we conclude this section, let us have a quick look at how to traverse through an array using basic for loops. There are better ways to get this done using in built array methods and we will have a look at them in another post!

{% highlight javascript %}
// Print the elements of 1D array
const array1D = [29, 0.99, 10, 3, 56];
for (const value of array1D) {
  console.log(value);
}

console.log("\n");

// Print the elements of 2D array
const array2D = [
  [10, 13, 15],
  [0.1, 0.3, 0.9],
  [-9, -61, -14],
];
for (const innerArray of array2D) {
  console.log("inner array", innerArray);
  for (const value of innerArray) {
    console.log(value);
  }
}
{% endhighlight %}

#### The output of the above code

![javascript-arrays-basics-loops](/javascript-blogs/assets/img/arrays-basics-loops.png)

And that's it folks!! We have reached the end of this post and hopefully by now, you have a basic idea of arrays, how they work, how to create and access array items etc. 