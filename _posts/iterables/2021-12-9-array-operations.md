---
layout: post
title: Array Operations
subtitle: A deep dive into all the basic array manipulation operations
tags: [iterables, arrays]
readtime: true
gh-repo: enigma6174/javascript-blogs
gh-badge: star
---

JavaScript provides a lot of inbuilt methods that can be used to modify arrays. Apart from creating an array, we can add elements to an array, delete elements, combine two arrays together, split arrays and much more. It is also important to note that many important array methods are not available to other JavaScript objects that implement the iterable protocol. Let us look at some of the most commonly used array operations.


### Adding New Elements To An Array

Adding new elements to the array is an in-place action which means that it modifies the structure of the existing array instead of returning a new array. It is therefore common to initialize arrays using ```const``` and then using the available methods we can add elements to the same. While ```const``` does not allow us to modify a variable once it has been declared, note that in arrays it works differently. Basically, the JavaScript object in the given location (specified by ```const```) is not modified, rather whatever it holds inside is modified. This is why using ```const``` we can create an array and then modify it. 

Follwing are some of the most popular ways of adding new elements to JavaScript arrays:

#### Push()

This method adds one or more new elements to the end of the array. The elements before the new newly added elements remain unchanged however. This is an inexpensive operation as adding new elements only takes **O(1)** time and the relative order of previous elements remain unchanged.  

The following is the array will be working with for majority of this post.

```javascript
const buffer = ["the", "quick", "brown", "fox"];
const temp = ["the", "lazy", "dog"];
console.log("buffer =>", buffer);
```  
---
```
buffer => [ 'the', 'quick', 'brown', 'fox' ]
```

Every pushed element gets added after the current last element of the array.

```javascript
buffer.push("jumps");
buffer.push("over");
console.log("buffer =>", buffer);
```
---
```
buffer => [ 'the', 'quick', 'brown', 'fox', 'jumps', 'over' ]
```

If we pass an array to the argument of ```push()``` this array gets added as a single element to the end of the existing array (as a sub array). This **does not** add each element of the passed array individually. To achieve that, an alternate technique exists.

```javascript
buffer.push(temp);
console.log("buffer =>", buffer);
console.log("last item of buffer", buffer[buffer.length - 1]);
```
---
```
buffer => [ 'the', 'quick', 'brown', 'fox', 'jumps', 'over', [ 'the', 'lazy', 'dog' ]]  
last item of buffer [ 'the', 'lazy', 'dog' ]
```

The follwing approach is used to push multiple items one by one into the array. The order of insertion into the array is the same as the order in which the elements are passed into ```push()``` as arguments.

```javascript
buffer.push("###", "$$$", "&&&", "@@@");
console.log("buffer =>", buffer);
```
---
```
buffer => [ 'the',
 'quick',
 'brown',
 'fox',
 'jumps',
 'over',
 [ 'the', 'lazy', 'dog' ],
 '###',
 '$$$',
 '&&&',
 '@@@' ]
```

We can also add new elements to JavaScript arrays by explicitly specifying the index. If an element already exists at that index, it gets overwritten by the new one.

```javascript
buffer[buffer.length] = "BACK";
console.log("buffer =>", buffer);
```
---
```
buffer => [ 'the',
 'quick',
 'brown',
 'fox',
'jumps',
 'over',
 [ 'the', 'lazy', 'dog' ],
 '###',
 '$$$',
 '&&&',
 '@@@',
 'BACK' ]
```

If we specify an index larger than the length of the array, then the element gets added at the specified index but the intermediate spaces are empty.

```javascript
buffer[15] = 'hello'
console.log("buffer =>", buffer);
```
---
```
buffer => [ 'the',
 'quick',
 'brown',
 'fox',
'jumps',
 'over',
 [ 'the', 'lazy', 'dog' ],
 '###',
 '$$$',
 '&&&',
 '@@@',
 'BACK',
 <3 empty items>,
 'hello' ]  
```  

#### Unshift()

This method adds one or more elements to the beginning of the array. Since new elements are added at the beginning, all the elements from index 0 gets *shifted one index to the right* for every element that gets added using ```Array.unshift()```. Therefore, the element at index 0 moves to index 1, the element at index 1 moves to index 2 and so on and the last element moves to index *Array.length*. And the element that got added is now present at index 0. From a performance point of view, this is an expensive operation because every single ```Unshift()``` call takes **O(n)** time and also changes the relative order of previous elements in the array. The **O(n)** time is because for every unshift operation, all the **N** array elements are shifted one position to the right.

```javascript
buffer.unshift("FRONT");
console.log("buffer =>", buffer);
```
---
```
buffer => [ 'FRONT',
   'the',
 'quick',
 'brown',
 'fox',
'jumps',
 'over',
 [ 'the', 'lazy', 'dog' ],
 '###',
 '$$$',
 '&&&',
 '@@@',
 'BACK',
 <3 empty items>,
 'hello' ] 
```

Just like ```push()``` we can also pass multiple elements into the ```unshift()``` call and insert multiple new elements to the array. The order of insertion into the array is the same as the order in which the arguments were passed.

```javascript
buffer.unshift("INDEX_0", "INDEX_1", "INDEX_2");
console.log("buffer =>", buffer);
```
---
```
buffer => [ 'INDEX_0',
 'INDEX_1',
 'INDEX_2',
 'FRONT',
   'the',
 'quick',
 'brown',
 'fox',
'jumps',
 'over',
 [ 'the', 'lazy', 'dog' ],
 '###',
 '$$$',
 '&&&',
 '@@@',
 'BACK',
 <3 empty items>,
 'hello' ] 
```

### Removing Elements To An Array

Similar to adding elements to the array, removing elements from an array is also an in-place operation. Most in built methods to remove array elements also return the removed element.

Follwing are some of the most popular ways of removing elements from JavaScript arrays:

#### Pop()

This method is used to remove a single element from the end of the array. The element that gets removed is present in the last index of the array and the length of the array decreases by one. From a performance perspective, this is a fast and inexpensive operation as it takes **O(1)** time to pop a single element from the array. The relative position of the array elements remain unchanged after the pop operation.

```javascript
let value = buffer.pop();
console.log("buffer =>", buffer);
console.log("buffer.pop()", value);
```
---
```
buffer => [ 'INDEX_0',
 'INDEX_1',
 'INDEX_2',
 'FRONT',
   'the',
 'quick',
 'brown',
 'fox',
'jumps',
 'over',
 [ 'the', 'lazy', 'dog' ],
 '###',
 '$$$',
 '&&&',
 '@@@',
 'BACK',
 <3 empty items> ]  
 buffer.pop() hello
```

#### Shift()

This method is also used to remove a single element from the array. Unlike `pop()` this method removes element form the beginning of the array. Every element from index 1 onwards gets shifted one index to the left after the `shift()` operation. From a performance point of view, this is a costly operation as each `shift()` operation takes **O(n)** time due to shifting of **N-1** elements to the left. It also changes the relative order of elements in the array after the operation.

```javascript
value = buffer.shift();
console.log("buffer.shift()", value);
console.log("buffer =>", buffer);
```
---
```
buffer.shift() INDEX_0  
buffer.shift() INDEX_0  
buffer.shift() INDEX_0  
buffer.shift() INDEX_0  
buffer => [ 'INDEX_1',
 'INDEX_2',
 'FRONT',
   'the',
 'quick',
 'brown',
 'fox',
'jumps',
 'over',
 [ 'the', 'lazy', 'dog' ],
 '###',
 '$$$',
 '&&&',
 '@@@',
 'BACK',
<3 empty items> ]
```

{% highlight javascript %}
{% endhighlight %}