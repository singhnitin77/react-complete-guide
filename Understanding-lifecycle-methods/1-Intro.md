A component lifecycle method is a function that we can optionally define inside of our class based components.

If we decide to implement these methods, they will be called automatically by react at certain points during a component's lifecycle.

These lifecycle methods are functions that are called during very distinct or discrete times during that cycle.

The render method is not optional, It is the one function that we absolutely have to define. Technically the render method is a lifecycle function, It gets called at some point during the life cycle of component.

```javascript
  componentDidMount() {
    /* This function will be automatically called one time when our component first gets rendered onto the screen */
    console.log("My component was rendered to the screen");
  }

  componentDidUpdate() {
    /* It will be called anytime when our component updates itself
    Any time that the component did update gets called right before its technically render will be called 
    Any time our component updates, the render method will be called, returning JSX shown on the screen
    */
    console.log("My component was just updated - it rendered!");
  }
```
