Constructor function is good place to do our state initialization. We can also do some initial data loading inside of a contructor.

Inside render method we are going to return some JSX, that's the only thing we do inside it. We are not going to make a network request or fetching the user's request.
It's only  to return some JSX.

ComponentDidMount() - Perfect location to do some initial data loading for our component.
Invoked only once.

ReactDocs say's don't do data loading inside constructor function. We can do but it is recommended to do it inside ComponentDidMount() method.

ComponentDidUpdate() - good location to do some data loading that needs to be done every single time that a component is updated.
For E.g - If we want to make some type of network request every single time that a user clicks on a button, or enter some text into an input or every single time that we get some new props from a parent component.

ComponentWillUnmount() - This method is used any time that we about to remove a component from the screen & need to do some cleanup.

__OTHER LIFECYCLE METHODS(rarely used)__

shouldComponentUpdate

getDerivedStateFromProps

getSnapshotBeforeUpdate
