```javascript
import React from "react";
import ReactDom from "react-dom";

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
      return <div>Latitude: {this.state.lat}</div>;
    }

    return <div>Loading!</div>;
  }
}

ReactDom.render(<App />, document.getElementById("root"));

```
