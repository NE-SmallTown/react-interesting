# What we do
We are trying to collect anything interesting about react-eco and people who work with it.There are not only good blogs or insights about react-eco,but also some stories or opinions about life and work, etc.

Hope this is helpful for you.

# Table of Contents
- [Something-Interestingly-About-Redux-Or-Its-Author](https://github.com/NE-SmallTown/react-heaven/blob/master/Something-Interestingly-About-Redux-Or-Its-Author.md)

- [Study-React](#study-react)

- [Record something about react itself](https://github.com/NE-SmallTown/react-heaven/blob/master/record.md)

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


### About ShouldComponentUpdate

![](https://facebook.github.io/react/img/docs/should-component-update.png)

Since shouldComponentUpdate returned false for the subtree rooted at C2, React did not attempt to render C2, and thus didn't even have to invoke shouldComponentUpdate on C4 and C5.

For C1 and C3, shouldComponentUpdate returned true, so React had to go down to the leaves and check them. For C6 shouldComponentUpdate returned true, and since the rendered elements weren't equivalent React had to update the DOM.

The last interesting case is C8. React had to render this component, but since the React elements it returned were equal to the previously rendered ones, it didn't have to update the DOM.

Note that React only had to do DOM mutations for C6, which was inevitable. For C8, it bailed out by comparing the rendered React elements, and for C2's subtree and C7, it didn't even have to compare the elements as we bailed out on shouldComponentUpdate, and render was not called.

