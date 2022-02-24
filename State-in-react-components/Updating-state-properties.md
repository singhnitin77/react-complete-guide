
```javascript

class App extends React.Component {
  constructor(props) {
    super(props);

    // This is the only time we do direct assignment
    // to this.state
    this.state = { lat: null };

    window.navigator.geolocation.getCurrentPosition(
      (position) => {
        // we called setstate!!!
        this.setState({ lat: position.coords.latitude });

        /* // We did not!!!
        this.state.lat = position.coords.latitude; */
      },
      (error) => console.log(err)
    );
  }

  // React says we have to define render
  render() {
    return <div>Latitude: {this.state.lat}</div>;
  }
}

ReactDom.render(<App />, document.getElementById("root"));
```
