# Study-React

[this is the case](http://codepen.io/snakajima/pen/JbYQvL)

### Let's go through each one and figure out which one is state. Simply ask three questions about each piece of data:

- Is it passed in from a parent via props? If so, it probably isn't state.
- Does it remain unchanged over time? If so, it probably isn't state.
- Can you compute it based on any other state or props in your component? If so, it isn't state.

### For each piece of state in your application:

- Identify every component that renders something based on that state.
- Find a common owner component (a single component above all the components that need the state in the hierarchy).
- Either the common owner or another component higher up in the hierarchy should own the state.
- If you can't find a component where it makes sense to own the state, create a new component simply for holding the state and add it somewhere in the hierarchy above the common owner component.

### React makes this data flow explicit to make it easy to understand how your program works, but it does require a little more typing than traditional two-way data binding.

- If you try to type or check the box in the current version of the example, you'll see that React ignores your input. This is intentional, as we've set the value prop of the input to always be equal to the state passed in from FilterableProductTable.



> While it may be a little more typing than you're used to, remember that code is read far more than it's written, and it's extremely easy to read this modular, explicit code. As you start to build large libraries of components, you'll appreciate this explicitness and modularity, and with code reuse, your lines of code will start to shrink. :)

