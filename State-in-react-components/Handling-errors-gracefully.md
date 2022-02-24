

```javascript
class App extends React.Component {
  constructor(props) {
    super(props);

    // This is the only time we do direct assignment
    // to this.state
    this.state = { lat: null, errorMessage: "" };

    window.navigator.geolocation.getCurrentPosition(
      (position) => {
        // we called setstate!!!
        this.setState({ lat: position.coords.latitude });

        /* // We did not!!!
        this.state.lat = position.coords.latitude; */
      },
      (err) => {
        this.setState({ errorMessage: err.message });
        /* If anything goes wrong with get current position request */
      }
    );
  }

  // React says we have to define render
  render() {
    return (
      <div>
        Latitude: {this.state.lat}
        <br />
        Error: {this.state.errorMessage}
      </div>
    );

    return <div>Latitude {alsf}</div>;
  }
}
```
