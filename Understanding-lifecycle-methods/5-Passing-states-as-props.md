We can take state from one component and pass it as a prop down to the child.

index.js
```javascript
import React from "react";
import ReactDom from "react-dom";
import SeasonDisplay from "./SeasonDisplay";

class App extends React.Component {
  state = { lat: null, errorMessage: "" };
  /* Code we writing here is equivalent to defining the constructor function and initializing our state inside there. */

  componentDidMount() {
    window.navigator.geolocation.getCurrentPosition(
      (position) => this.setState({ lat: position.coords.latitude }),
      (err) => this.setState({ errorMessage: err.message })
    );
  }

  render() {
    if (this.state.errorMessage && !this.state.lat) {
      return <div>Error: {this.state.errorMessage}</div>;
    }

    if (!this.state.errorMessage && this.state.lat) {
      return <SeasonDisplay lat={this.state.lat} />;
    }

    return <div>Loading!</div>;
  }
}

ReactDom.render(<App />, document.getElementById("root"));

```

Now season display is going to be very closely linked with the App component.

Anytime that we call the set state inside of the parent component of app and update the latitude the app component is going to rerender itself as we know anytime we call setState, the component updates itself.
that going to cause the season display to be updated as well, because if latitude prop going to changes, the new latitude value is going to be put into season display and season display will be rerendered as well.

___

SeasonDisplay.js
```javascript
import React from "react";

const SeasonDisplay = (props) => {
  console.log(props.lat);
  return <div>Season Display</div>;
};

export default SeasonDisplay;

```
