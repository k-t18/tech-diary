Let's start with an example.

I came across a question while trying to log something on console.

```
let name = "John";
name.toLowerCase()
console.log(name) // expected output john
```

But I was incorrect. The output was still 'John'. That got me start finding out the reason behind this.

let word = "hello"

The variable word is not the box that contains the value "hello" in it. The variable word points to the box i.e it contains the address of the value.

When we try to reassign it
word = 'World'

What’s actually happening here isn’t that the "hello" is being replaced by "world" – it’s more like an entirely new box is created, and the name is reassigned to point at the new box. (and at some point, the "hello" box is cleaned up by the garbage collector, since nothing is using it)

### Two Types of Types

JavaScript has two broad categories of types, and they have different rules around assignment and referential equality. Let’s talk about those.

There are the primitive types like string, number, boolean (and also symbol, undefined, and null). These ones are **immutable**. a.k.a. read-only, can’t be changed.

When a variable holds one of these primitive types, you can’t _modify_ the value itself. You can only reassign that variable to a new value.

When the value inside a box is a string/number/boolean/symbol/undefined/null, you can’t change the value. You can only create new boxes.

Coming back to the example mentioned at the very start of this page ...

This is why, for example, all of the methods on strings return a new string instead of modifying the string, and if you want that new value, you’ve gotta store it somewhere.

```
let name = "John"
name.toLowerCase()
console.log(name) // John

name = name.toLowerCase()
console.log(name) // john
```

Some more examples

```
let numb = "12.503"
parseFloat(numb)
console.log(numb) // 12.503
console.log(typeof(numb)) // string

let convertedToFloat = parseFloat(numb)
console.log(convertedToFloat) // 12.503
console.log(typeof(convertedToFloat)) // number
```

### Every other type: Objects, Arrays, etc.

The other category is the object type. This encompasses objects, arrays, functions, and other data stuctures like Map and Set. They are all objects.

The big difference from primitive types is that objects are **mutable**! You can change the value in the box.

```
let book = {
  title: "Tiny Habits",
  author: "BJ Fogg",
  isCheckedOut: false
}

book.isCheckedOut = true

console.log(book)
 {
    title: "Tiny Habits",
    author: "BJ Fogg",
    isCheckedOut: true
 }
```

```
a = document.addEventListener('click', () => console.log('clicked'));
b = document.removeEventListener('click', () => console.log('clicked'));

console.log(a === b) // false

```

Every new object (array, function, Set, Map, etc.) lives in a brand new box, unequal to every other box.

Here's another one

```
function minimum(array) {
  array.sort();
  return array[0]
}

const items = [7, 1, 9, 4];
const min = minimum(items);
console.log(min)
console.log(items)
```

What does this print?

The .sort() method on arrays sorts the array in place, meaning it changes the order on the original array without copying it.

This example prints 1 and [1, 4, 7, 9].

Now, this might be what you wanted. But probably not, right? When you call a minimum function, you don’t expect it to rearrange the items in your array.

To fix this, make a copy of the array before sorting it, like in the code below. Here we’re using the spread operator to make a copy of the array (the [...array] part). This is actually creating a brand new array and then copying in every element from the old one.

```
function minimum(array) {
  const newArray = [...array].sort();
  return newArray[0]
}
```

Some more

a = 'hi'

b = 'hi'

a===b // true

arr1 = [1,2,3]
arr2 = [1,2,3]

arr1 === arr2 // false

Why so ?

1. Primitive Values (e.g., Strings, Numbers):

When comparing primitive values, JavaScript checks if the values are the same.
For example, with a and b, both are strings with the value 'hi'. Since they are both primitive values and have the same content, a === b evaluates to true.

2. Objects (e.g., Arrays, Functions):

When comparing objects, JavaScript checks if both references point to the same object in memory, not if their contents are the same.
arr1 and arr2 are two separate arrays with identical contents. However, they are distinct objects in memory, so<br> arr1 === arr2 evaluates to false.
