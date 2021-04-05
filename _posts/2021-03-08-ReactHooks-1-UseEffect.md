---
layout: post
title: React⚛ Hooks-UseEffect
color: rgb(102,153,255)
tags: [websolute, team, React, Hooks, front-end, web, framework]
---

### UseEffect

UseEffect는 componentDidMount, ComponentWillunMount, componentDidUpdate와 비슷하다.(동일)

```javascript
const App = () => {
  const sayHello = () => {
    console.log("Hello");
  };
  const [number, setNumber] = useState(0);
  const [aNumber, setAnumber] = useState(0);
  useEffect(sayHello, []);
  return (
    <div className="App">
      <button onClick={() => setNumber(number + 1)}>{number}</button>
      <button onClick={() => setAnumber(aNumber + 1)}>{aNumber}</button>
    </div>
  );
};
```

위의 코드에서 UseEffect는 2개의 인자를 받는데 첫번째는 function으로써의 effect이다.
두번째는 dependency이다. 만약 deps가 있다면 effect는 deps(리스트)에 있는 값일 때만 값이 변하도록 활성화 될거다.
deps(리스트)에 있는 값일때만 값이 변하도록(실행) 활성화(componentWillUpdate)
component가 mount되었을 때만 실행시키고 싶다면 빈 dependency전달해준다.
