---
layout: post
title: React⚛ Hooks-UseState
color: rgb(102,153,255)
tags: [websolute, team, React, Hooks, front-end, web, framework]
---

<p align = "center"><img src="https://miro.medium.com/max/6300/1*buOLbtsDPRK8VLxlMTAmLQ.jpeg" width = "75%"></p>

### UseState

useState가 바로 Hook 이다. Hook을 호출해 함수 컴포넌트(function component) 안에 count state를 추가했다. 이 state는 컴포넌트가 다시 렌더링 되어도 그대로 유지될 것이다. useState는 현재의 state 값(count)과 이 값을 업데이트하는 함수(setCount)를 쌍으로 제공한다.
useState는 인자로 초기 state 값을 받는다. 아래 예제에서는 count state 초기 값으로 0을 설정하였다.

```javascript
import React, { useState } from "react";

function Example() {
  // "count"라는 새 상태 변수를 선언한다.
  const [count, setCount] = useState(0);
  const up = () => setCount(count + 1);
  const down = () => setCount(count - 1);
  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={up}>Click Up!</button>
      <button onClick={down}>Click Down!</button>
    </div>
  );
}
```

```javascript
class App extends React.Component {
  state = {
    item: 1,
  };
  render() {
    const { item } = this.state;
    return (
      <div className="App">
        <button onClick={Up}>Increment</button>
        <button onClick={Down}>Decrement</button>
      </div>
    );
  }
  Up = () => {
    this.setState((state) => {
      return {
        item: state.item + 1,
      };
    });
  };
  Down = () => {
    this.setState((state) => {
      return {
        item: state.item - 1,
      };
    });
  };
}
```

위의 코드가 Hooks로 짠것 밑이 class로 짠것이다. Hooks가 훨씬 코드가 짧은것을 알수있다!

<br>
<br>
