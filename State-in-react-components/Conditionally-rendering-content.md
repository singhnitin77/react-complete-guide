//index.js

```javascript
import React from "react";
import ReactDom from "react-dom";

class App extends React.Component {
  constructor(props) {
    super(props);
    
    this.state = { lat: null, errorMessage: "" };

    window.navigator.geolocation.getCurrentPosition(
      (position) => {
        this.setState({ lat: position.coords.latitude });

      },
      (err) => {
        this.setState({ errorMessage: err.message });
        /* If anything goes wrong with get current position request */
      }
    );
  }

  // React says we have to define render
  render() {
    
    if (this.state.errorMessage && !this.state.lat) {
      return <div>Error: {this.state.errorMessage}</div>
    }

    if (!this.state.errorMessage && this.state.lat) {
      return <div>Latitude: {this.state.lat}</div>
    }

    return <div>Loading!</div>;
  }
}

ReactDom.render(<App />, document.getElementById("root"));

```
