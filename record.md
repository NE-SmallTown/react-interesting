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
