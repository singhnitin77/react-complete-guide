# Understanding the Base Features & Syntax

_Useful Resources & Links_

- [create-react-app](https://github.com/facebookincubator/create-react-app)
- [Introducing JSX](https://reactjs.org/docs/introducing-jsx.html)
- [Rendering Elements](https://reactjs.org/docs/rendering-elements.html)
- [Components & Props](https://reactjs.org/docs/components-and-props.html)
- [Listenable Events](https://reactjs.org/docs/events.html)

### Introduction

1. React Core Syntax and JSX.
2. Working with components.
3. Working with Data.

### Components
* Component are reusable building blocks in our user interface.
* Compnonents in the end are just a combination of HTML code.
* CSS code for styling and possibly Javascript code for some logic.

* React embraces this concept of components because of that reusablity aspect and it allows us to separate our concerns.

* Having reusable building blocks helps us avoid repition.

* Having a separation of concerns help us with keeping our code base small and manageable. 

### How is a component built
Mostly react components are about combining HTML and Javascript.

Thus React allows us to create re-usable and reactive components consisting of HTML and Js.

React uses Declarative Approach.

### 2. The Build Workflow

Before we setup a local project, we need to use a **more elaborate workflow** (than just using Codepen or jsbin). It is recommended for both SPAs and MPAs.

**Why?**

- **Optimise** code: we want to ship code that is **as small as possible** and **as optimized as possible**, because that increases the performance of our app.
- Use **next-gen JavaScript features**: it makes our life as a developer much easier! The code is _leaner_,_ easier to read_, _faster_, _less error prone_ and many other reasons. **+ compatibility reasons**, we need a build workflow that actually compiles these features to support as many browsers possible.
- Be **more productive**, it includes next generation JavaScript features which often allow us to write **more condensed code** but it also includes things like CSS auto-prefixing (increase the browser support for CSS features). Or **linting**.

**How?**

- Use **dependency management tool**: `NPM` or `yarn`.
- Use a **bundler**: here we're going to use **Webpack**.
- Use **compiler** (next-gen JavaScript): **Babel** + presets.
- Use a **development server**.

_Note: Create React App is a tool which have everything above out of the box – perfect to start a new React project :)_

### Using Create React App

```sh
# create a new create-react-app project
npx create-react-app react-complete-guide --scripts-version 1.1.5
```

### Understanding the Folder Structure
* React code is just javascript code.
index.js will be executed initially.
* We are importing ReactDOM from 'react-dom', which means that we are importing some ReactDOM object from the react-dom third party library, which is one of our dependencies, downloaded and installed locally.
* In the package.json file, we have 2 react dependicies
* public folder holds one imp file index.html. This is the single HTML file which is the end loaded by the browser here because with react we build so-called single page application.
* Only one HTML file is delivered to the browser and hosted by the browser or rendered by the browser but on this single file we import the finished React application code. and it's that code what we see on the screen.
* App in the end is a component

* App.js file - It holds a function named App & then we export this function



```
/node_modules
/public
/src
.gitignore
package.json
README.md
yarn.lock
```

### Understanding Component Basics

Here is our first component. React is **all about component**!

```js
import React, { Component } from 'react'; // React and Component from react library
import './App.css';

// class App extends Component
class App extends Component {
  // render method is the only one which is required
  render() {
    // just below it is now HTML but JSX
    return (
      <div className="App">
        <h1>Hi, I'm a React App!</h1>
      </div>
    );
  }
}

// we need to export this component
export default App;
```

### Understanding JSX

* JSX code basically the HTML code inside of Javascript.
* JSX stands for Javascript XML. 
Working without JSX, replace it with `React.createElement`.

```js
import React, { Component } from 'react';
import './App.css';

class App extends Component {
  render() {
    // return (
    //   <div className="App">
    //     <h1>Hi, I'm a React App!</h1>
    //   </div>
    // );
    const h1 = React.createElement('h1', null, "Hi, I'm a React App!");
    return React.createElement('div', { className: 'App' }, h1);
  }
}

export default App;
```

### HOW REACT WORKS
* With react we ultimately build our own custom HTML elements, components i.e that are just HTML element


### JSX Restrictions

For example, `class` can't be used in JSX, because JSX is JS and `class` is **a reserved word**. Also we can't return more than one root element (solution using Fragment `<></>`).

### Creating a Functional Component

```js
// src/Person/Person.js
import React from 'react';

const person = () => {
  return <div>I'm a Person!</div>;
};

export default person;
```

```js
// src/App.js
import React, { Component } from 'react';
import Person from './Person/Person';
import './App.css';

class App extends Component {
  render() {
    return (
      <div className="App">
        <h1>Hi, I'm a React App!</h1>
        <Person />
      </div>
    );
  }
}

export default App;
```

### 9. Components & JSX Cheat Sheet

Components are the **core building block of React apps**. Actually, React really is just a library for creating components in its core.

A typical React app therefore could be depicted as a **component tree** - having one root component ("App") and then an potentially infinite amount of nested child components.

Each component needs to return/ render some **JSX** code - it defines which HTML code React should render to the real DOM in the end.

**JSX is NOT HTML** but it looks a lot like it. Differences can be seen when looking closely though (for example `className` in JSX vs `class` in "normal HTML"). JSX is just **syntactic sugar** for JavaScript, allowing you to write HTMLish code instead of nested `React.createElement(...)` calls.

When creating components, you have the choice between **two different ways**:

1. **Functional components** (also referred to as "**presentational**", "**dumb**" or "**stateless**" components - more about this later in the course) => `const cmp = () => { return <div>some JSX</div> }` (using ES6 arrow functions as shown here is recommended but optional)

2. **class-based components** (also referred to as "**containers**", "**smart**" or "**stateful**" components) => `class Cmp extends Component { render () { return <div>some JSX</div> } }`

### 10. Working with Components & Re-Using Them

```js
// src/App.js
import React, { Component } from 'react';
import './App.css';
import Person from './Person/Person';

class App extends Component {
  render() {
    return (
      <div className="App">
        <h1>Hi, I'm a React App!</h1>
        <Person />
        <Person />
        <Person />
      </div>
    );
  }
}

export default App;
```

### 11. Outputting Dynamic Content

```js
// src/Person/Person.js
import React from 'react';

const person = () => {
  return (
    <p>I'm a Person and I'm {Math.floor(Math.random() * 30)} years old!</p>
  );
};

export default person;
```

We output random/dynamic content into our HTML.

```
I'm a Person and I'm 29 years old!

I'm a Person and I'm 2 years old!

I'm a Person and I'm 5 years old!
```

### 12. Working with Props

```js
// src/App.js
import React, { Component } from 'react';
import './App.css';
import Person from './Person/Person';

class App extends Component {
  render() {
    return (
      <div className="App">
        <h1>Hi, I'm a React App!</h1>
        <Person name="Max" age="29" />
        <Person name="Jerôme" age="26" />
        <Person name="Morgane" age="27" />
      </div>
    );
  }
}

export default App;
```

```js
// src/Person/Person.js
import React from 'react';

const person = (props) => {
  return (
    <p>
      I'm a {props.name} and I'm {props.age} years old!
    </p>
  );
};

export default person;
```

_Note: class based component, use `this.props`._

### 13. Understanding the "children" Prop

```js
// src/App.js
//...
<Person name="Jerôme" age="26">
  My hobbies: Racing
</Person>
//...
```

We can access it via `props.children`.

```js
// src/Person/Person.js
import React from 'react';

const person = (props) => {
  return (
    <div>
      <p>
        I'm a {props.name} and I'm {props.age} years old!
      </p>
      <p>{props.children}</p>
    </div>
  );
};

export default person;
```
