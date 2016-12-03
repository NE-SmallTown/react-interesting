## The order of The Component Lifecycle methods(about more details, see [answer by bailicangdu](http://react-china.org/t/react-redux/9072/13?u=ne-smalltown))

![](http://mmbiz.qpic.cn/mmbiz_png/meG6Vo0MevhInLnhZibzCk7gnIRP70DHBOgNZKBReh9XPwfiamSeciaiamnicYaNHmf3vo62kTKGTk7nT6ypasxu4ZQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1)

- setState(nextState, callback)

- nextState may be a `function (prevState, props) {}`

- The second parameter is an optional callback function that will be executed once setState is completed and the component is re-rendered. Generally we recommend using componentDidUpdate() for such logic instead.

- setState() does not immediately mutate this.state but creates a pending state transition. Accessing this.state after calling this method can potentially return the existing value.There is no guarantee of synchronous operation of calls to setState and calls may be batched for performance gains.

### Mounting
These methods are called when an instance of a component is being created and inserted into the DOM:

- constructor(props)

- componentWillMount()

- render()

- componentDidMount()

### Updating

An update can be caused by changes to props or state. These methods are called when a component is being re-rendered:

- componentWillReceiveProps(nextProps)

- shouldComponentUpdate(nextProps, nextState)

- componentWillUpdate(nextProps, nextState)

- render()

- componentDidUpdate(prevProps, prevState))

### Unmounting

This method is called when a component is being removed from the DOM:

- componentWillUnmount()

### Other

- forceUpdate(callback)

## Useful Plugins

[Keyed Fragments](https://facebook.github.io/react/docs/create-fragment.html)

## Redux

### Container Components and Presentational Components

#### Presentational Components:

- Are concerned with how things look.

- May contain both presentational and container components** inside, and usually have some DOM markup and styles of their own.

- Often allow containment via this.props.children.

- Have no dependencies on the rest of the app, such as Flux actions or stores.

- Don’t specify how the data is loaded or mutated.

- Receive data and callbacks exclusively via props.

- Rarely have their own state (when they do, it’s UI state rather than data).

- Are written as functional components unless they need state, lifecycle hooks, or performance optimizations.

Examples: Page, Sidebar, Story, UserInfo, List.

#### Container Components:

- Are concerned with how things work.

- May contain both presentational and container components** inside but usually don’t have any DOM markup of their own except for some wrapping divs, and never have any styles.

- Provide the data and behavior to presentational or other container components.

- Call Flux actions and provide these as callbacks to the presentational components.

- Are often stateful, as they tend to serve as data sources.

- Are usually generated using higher order components such as connect() from React Redux, createContainer() from Relay, or Container.create() from Flux Utils, rather than written by hand.

Examples: UserPage, FollowersSidebar, StoryContainer, FollowedUserList.

> When you notice that some components don’t use the props they receive but merely forward them down and you have to rewire all those intermediate components any time the children need more data, it’s a good time to introduce some container components.This way you can get the data and the behavior props to the leaf components without burdening the unrelated components in the middle of the tree

By contrast, here are a few related (but different!) technical distinctions:

#### Stateful and Stateless:
- Some components use React setState() method and some don’t. While container components tend to be stateful and presentational components tend to be stateless, this is not a hard rule. Presentational components can be stateful, and containers can be stateless too.

#### Classes and Functions:
- Since React 0.14, components can be declared both as classes and as functions. Functional components are simpler to define but they lack certain features currently available only to class components. Some of these restrictions may go away in the future but they exist today. Because functional components are easier to understand, I suggest you to use them unless you need state, lifecycle hooks, or performance optimizations, which are only available to the class components at this time.

#### Pure and Impure:
- People say that a component is pure if it is guaranteed to return the same result given the same props and state. Pure components can be defined both as classes and functions, and can be both stateful and stateless. Another important aspect of pure components is that they don’t rely on deep mutations in props or state, so their rendering performance can be optimized by a shallow comparison in their shouldComponentUpdate() hook. Currently only classes can define shouldComponentUpdate() but that may change in the future

> In my experience, presentational components tend to be stateless pure functions, and containers tend to be stateful pure classes. However this is not a rule but an observation, and I’ve seen the exact opposite cases that made sense in specific circumstances.

## Links

[smart-and-dumb-components](https://medium.com/@dan_abramov/smart-and-dumb-components-7ca2f9a7c7d0#.d3cn7lsti)
[You Might Not Need Rudux](https://medium.com/@dan_abramov/you-might-not-need-redux-be46360cf367#.3w59x6s1e)
