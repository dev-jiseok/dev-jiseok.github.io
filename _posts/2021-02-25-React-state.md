---
layout : post
title : React⚛ STATE
color: rgb(242,85,44)
tags: [websolute,team,React,front-end,web,framework]
---

### Class Components and State

```javascript
//src/App.js

import React from "react";
 import PropTypes from "prop-types";

 class App extends React.Component {
   state = {
     count: 0
   };
   add = () => {
     console.log("add");
   };
   minus = () => {
     console.log("minus");
   };
   render() {
     return (
       <div>
         <h1>The number is: {this.state.count}</h1>
         <button onClick={this.add}>Add</button>
         <button onClick={this.minus}>Minus</button>
       </div>
     );
   }
 }

 export default App;
```

<br>
<br>

### All you need to know about State

```javascript
import React from "react";
import PropTypes from "prop-types";
class App extends React.Component {
  state = {
     count: 0
   };
   add = () => {
     this.setState(current => ({ count: current.count + 1 }));
   };
   minus = () => {
     this.setState(current => ({ count: current.count - 1 }));
   };
   render() {
     return (
      <div>
        <h1>The number is: {this.state.count}</h1>
        <button onClick={this.add}>Add</button>
        <button onClick={this.minus}>Minus</button>
      </div>
    );
  }
}
export default App;
```

<br>
<br>

### Component Life Cycle

```javascript
import React from "react";

 class App extends React.Component {
   state = {
    count: 0
  };
  add = () => {
    this.setState(current => ({ count: current.count + 1 }));
  };
   minus = () => {
     this.setState(current => ({ count: current.count - 1 }));
   };
   componentDidMount() {
     console.log("Component rendered");
   }
   componentDidUpdate() {
     console.log("I just updated");
   }
   componentWillUnmount() {
     console.log("Goodbye, cruel world");
   }
   render() {
     console.log("I'm rendering");
     return (
       <div>
         <h1>The number is: {this.state.count}</h1>
        <button onClick={this.add}>Add</button>
        <button onClick={this.minus}>Minus</button>
      </div>
    );
  }
}
export default App;
```

<br>
<br>

### Planning the Movie Component

```javascript
import React from "react";

 class App extends React.Component {
   state = {
     isLoading: true,
     movies: []
   };
   componentDidMount() {
     setTimeout(() => {
       this.setState({ isLoading: false });
     }, 6000);
   }
   render() {
     const { isLoading } = this.state;
     return <div>{isLoading ? "Loading..." : "We are ready"}</div>;
   }
 }

export default App;
```
