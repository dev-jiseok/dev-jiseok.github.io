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

#### class component와 function component 차이
function component 는 return 하고 screen에 표시
class component 는 class이지만 react component로부터 확장되고 screen에 표시되며 render method안에 넣어야 한다.
react는 자동적으로 모든 class component의 render method를 실행하고자 한다. 또한 state를 가지고 있다.

<br>

#### state
object이고 component의 data를 넣을 공간이 있고 그 data는 변한다. (state를 사용하는 이유)

<br>

#### class App extends React.Component
render method를 가지고 있다.
state={count:0}; 형식으로 표현 , state를 render에 사용하고 싶을 경우, {this.state.count} 형식으로 표현

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

setState는 새로운 state를 받는다. setState를 호출할 시, react는 state를 refresh하고 render function을 호출 , setState를 사용하지 않으면 새 state와 함께 render function이 호출되지 않는다.

>this.setState({count: this.state.count+1});
>이렇게 할 수도 있지만 state에 의존하는 것은 크게 좋은방법은 아니다.

>this.setState(current=>({count: current.count+1}));
>이것이 state를 set할 때, react에서 state에 의존하지 않는 가장 좋은 방법!


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

#### mounting : component가 screen에 표시되는 것
constructor() 호출
render() 호출
componentDidMount() : component가 처음 render 하는 것을 알려줌 (render() 이후 적용)
#### updating : 사용자가 만든 함수에 의해 update (setState를 호출할떄마다 발생)
render() 호출
componentDidUpdate () 호출
<strong>(setState 호출 -> component호출 -> renfer 호출 -> 업데이트 완료되면 componentDidUpdate 호출)</strong>
#### unmounting : component가 죽는 것
componentWillUnmount() : component가 죽을 때 호출

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

render 안에는 isLoading 이 항상 지금 state 가져오게 해준다. true 일때는 로딩이 뜨게 하고 false일때는 we are ready를 띄운다.
