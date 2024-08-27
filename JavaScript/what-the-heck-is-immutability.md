### Understanding its counterpart

First off, immutable is the opposite of mutable – and mutable means changeable, modifiable… able to be messed up with.

So something that is immutable, then, is something that cannot be changed.

To understand immutability let's first understand mutability first.

```
let person = {
	firstName: "Bob",
	lastName: "Loblaw",
	address: {
		street: "123 Fake St",
		city: "Emberton",
		state: "NJ"
	}
}
```

```
function favoriteFood(person) {
	person.favFood = "pav bhaji";
	return person;
}
```

```
console.log(person);

// Then we call our function...
let personWithFavFood = favoriteFood(person);

console.log(person);
console.log(personWithFavFood);
```

Try answering this

```
person === personWithFavFood
```

This function favoriteFood mutates the person passed into it. Run this code, and you’ll see that the first time we print out person, Bob has no favFood property. But then, the second time, we know his fav food.

This was all about mutability where we are changing the original object. The object returned from favoriteFood is the same object as the one that was passed in, but its insides have been messed with. Its properties have changed. It has been mutated.

I want to say this again because it’s important: **the internals of the object have changed, but the object reference has not.**

### What are you Immutability?

If we want the favoriteFood function not to modify/mutate the person, we’ll have to make a few changes.

```
function favoriteFood(person) {
  let newPerson = {
    ...person,
    favFood: 'pav bhaji'
  }

  return newPerson;
}
```

Try answering this now

```
person === newPerson
```

### React Prefers Immutability

**In React’s case, it’s important to never mutate state or props.**

```
import { useRef, useState } from "react";

function ItemList(items: any) {
  return (
    <ul>
      {items?.items?.length > 0 &&
        items?.items?.map((item: any) => <li key={item.id}>{item.value}</li>)}
    </ul>
  );
}

function App() {
  const [items, setItems] = useState<any>([]);
  const nextItemId = useRef(0);
  const makeItem = () => {
    // Create a new ID and use
    // a random number as the value
    return {
      id: nextItemId.current++,
      value: Math.random(),
    };
  };

  // The Right Way:
  // create a new array with the new item Immutable way
  const addItemImmutably = () => {
    setItems([...items, makeItem()]);
  };

  // The Wrong Way:
  // mutate items and set it back
  const addItemMutably = () => {
    items.push(makeItem());
    setItems(items);
  };
  return (
    <div>
      <button onClick={addItemImmutably}>Add item immutably (good)</button>
      <button onClick={addItemMutably}>Add item mutably (bad)</button>
      <ItemList items={items} />
    </div>
  );
}

export default App;
```

Try it out!

Click the immutable Add button a few times and notice how the list updates as expected.

Then click the mutable Add button and notice how the new items don’t appear, even though state is being changed.

Finally, click the immutable Add button again, and watch how the ItemList re-renders with all the missing (mutably-added) items.

1. addItemMutably

- Direct mutation:
  This is because directly mutating state will modify the contents inside of state. It will not change its reference.
  React's state management relies on detecting changes by **comparing references**, not by deeply inspecting the state. By mutating the array in place, the reference to items remains the same, which means React may not detect any change.

- Re-render: Because the reference to the items array hasn't changed, React may not trigger a re-render since it assumes that nothing has changed in the state.

2. addItemImmutably

- Immutability: You’re not modifying the existing state directly. Instead, you're creating a new array(means newer reference), which React can detect as a change.

- Re-render: React recognizes that the items array has been replaced with a new reference, so it triggers a re-render.

This article can help you a lot.
https://react.dev/learn/updating-objects-in-state
