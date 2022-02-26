index.js

```javascript
import React from "react";
import ReactDOM from "react-dom";
import App from "./components/App";

ReactDOM.render(<App />, document.getElementById("root"));
```

App.js

```javascript
import React from "react";
import SearchBar from "./SearchBar";

const App = () => {
  return (
    <div className="ui container" style={{ marginTop: "10px" }}>
      <SearchBar />
    </div>
  );
};

export default App;
```

SearchBar.js

```javascript
import React from "react";

class SearchBar extends React.Component {
  onInputChange(event) {
    /* The name of the callback does not matter, the only name that matters at all it 
    the property name that we are passing that function to.*/
    //   event.target.value
    console.log(event.target.value);
    // This will contain the text that the user just added to input
  }

  onInputClick() {
    console.log("Input was clicked");
  }

  render() {
    return (
      <div className="ui segment">
        <form className="ui form">
          <div className="field">
            <label>Image Search</label>
            <input
              type="text"
              onChange={this.onInputChange} //here it must be onChange
              //   onClick={this.onInputClick}
              //   onChange={(event) => console.log(event.target.value)}
            />
          </div>
        </form>
      </div>
    );
  }
}

export default SearchBar;
```

We don't put on a set of parenthesis whenver we pass a callback function to an event handler

Onchange is a very special property name  

ALTERNATE EVENT HANDLER SYNTAX

```javascript
onChange={(event) => console.log(event.target.value)} 
onChange={(e) => console.log(e.target.value)} 
```

Currently, inside of our search bar component, we have created what is called a UNCONTROLLED form element but we prefer to work with controlled events.

___

CONTROLLED ELEMENT

SearchBar.js
```javascript
import React from "react";

class SearchBar extends React.Component {
  state = { term: "" };

  render() {
    return (
      <div className="ui segment">
        <form className="ui form">
          <div className="field">
            <label>Image Search</label>
            <input
              type="text"
              value={this.state.term}
              onChange={(e) => this.setState({ term: e.target.value })}
            />
          </div>
        </form>
      </div>
    );
  }
}

export default SearchBar;

/* We are initializing our state, having a single property called term with empty string & 
every single time a user types input we are going to update our state, more precisely update 
term property with whatever the current value out of the input */
```

___
___

Difference bw Controlled & Uncontrolled elements

When the component re-renders we take the value of that input or take this.state.term & assign it to the value prop of the input, value prop is going to overwrite whatever text is already inside of the input 










