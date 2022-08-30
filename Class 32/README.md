# Class 32

Live link: [React3](https://muhammadqasemtarboush1.github.io/reading-notes/Class%2032/)

## React Context for Beginners – The Complete Guide (2021)

React context is an essential tool for every React developer to know. I lets you easily share state in your applications.

> ### What is React context?

React context allows us to pass down and use (consume) data in whatever component we need in our React app without using props.

> ### When should you use React context?

React context is great when you are passing data that can be used in any component in your application.

Why? Because context was not made as an entire state management system. It was made to make consuming data easier.

You can think of React context as the equivalent of global variables for our React components.

> ### What problems does React context solve?

React context helps us avoid the problem of props drilling.

> ### How do I use React context?

Context is an API that is built into React, starting from React version 16.

This means that we can create and use context directly by importing React in any React project.

There are four steps to using React context:

Create context using the createContext method.
Take your created context and wrap the context provider around your component tree.
Put any value you like on your context provider using the value prop.
Read that value within any component by using the context consumer.

> ### What is the useContext hook?

Another way of consuming context became available in React 16.8 with the arrival of React hooks. We can now consume context with the useContext hook.

Instead of using render props, we can pass the entire context object to React.useContext() to consume context at the top of our component.

> ### You may not need context

The mistake many developers make is reaching for context when once they have to pass props down several levels to a component.

> ### Does React context replace Redux?

Yes and no.

For many React beginners, Redux is a way of more easily passing around data. This is because Redux comes with React context itself.

However, if you are not also updating state, but merely passing it down your component tree, you do not need a global state management library like Redux.

> ### React context caveats

Why it is not possible to update the value that React context passes down?

While it is possible to combine React context with a hook like useReducer and create a makeshift state management library without any third-party library, it is generally not recommended for performance reasons.

This may not be a performance issue in smaller apps with few state values that are not updated very often (such as theme data). But it is a problem if you will be performing many state updates in an application with a lot of components in your component tree.

## Note

* Props drilling is a term to describe when you pass props down multiple levels to a nested component, through components that don't need it.
* The benefit of the useContext hook is that it makes our components more concise and allows us to create our own custom hooks.

## Resources

### [React context](https://www.freecodecamp.org/news/react-context-for-beginners/)

### [Next js](https://nextjs.org/learn/basics/create-nextjs-app)

---