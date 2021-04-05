---
layout: post
title: React⚛ Hooks-UseScroll & UseFullscreen
color: rgb(153,204,255)
tags: [websolute, team, React, Hooks, front-end, web, framework]
---

### UseScroll

유저가 스크롤해서 어디를 지정하거나 지나쳤을 때 나타나게 함

```javascript
const useScroll=()=>{
  const[state,setState]=useState({
    x:0,
    y:0
  });
  const onScroll=()=>{
    console.log(window.scrollY);
    setState({y :window.scrollY},{x :window.scrollX});
  };
  useEffect(()=>{
    window.addEventListener("scroll",onScroll);
    return()=>{
      window.removeEventListener("scroll",onScroll);
    };
  },[]);
  return state;
};

const App=()=>{
  const {y}=useScroll();
  return(
    <div className="App" style=>
      <h1 style=>Hi</h1>
    </div>
  );
};
```

```javascript
const onScroll = () => {
  console.log(window.scrollY);
  setState({ y: window.scrollY }, { x: window.scrollX });
};
```

측정한 window의 scroll으로 set 해준다.

<br>

### UseFullscreen

```javascript
const useFullscreen = (callback) => {
  const element = useRef();
  const triggerFull = () => {
    if (element.current) {
      if (element.current.requestFullscreen) {
        element.current.requestFullscreen(); //fullscreen으로 만들어준다.
      } else if (element.current.mozRequestFullscreen) {
        element.current.mozRequestFullscreen();
      } else if (element.current.webkitRequestFullscreen) {
        element.current.webkitRequestFullscreen();
      } else if (element.current.msRequestFullscreen) {
        element.current.msRequestFullscreen();
      }
      if (callback && typeof onFulls === "function") {
        callback(true);
      }
    }
  };
  const exitFull = () => {
    document.exitFullscreen();

    if (document.current) {
      if (document.current.requestFullscreen) {
        element.current.requestFullscreen(); //fullscreen으로 만들어준다.
      } else if (element.current.mozRequestFullscreen) {
        element.current.mozRequestFullscreen();
      } else if (element.current.webkitRequestFullscreen) {
        element.current.webkitRequestFullscreen();
      } else if (element.current.msRequestFullscreen) {
        element.current.msRequestFullscreen();
      }
      if (callback && typeof onFulls === "function") {
        callback(false);
      }
    }
  };
  return { element, triggerFull, exitFull };
};

const App = () => {
  const onFulls = (isFull) => {
    console.log(isFull ? "We are full" : "We are small");
  };
  const { element, triggerFull, exitFull } = useFullscreen(onFulls);

  return (
    <div className="App">
      <div ref={element}>
        <img ref={element} src="data:image/png;base64" />
      </div>
      <button onClick={triggerFull}>Make fullscreen</button>
      <button onClick={exitFull}>Exit fullscreen</button>
    </div>
  );
};
```

`return {element,triggerFull,exitFull};` 내부함수 자체가 return값이라면 내부함수 외부에서 사용 가능하다.

`const {element,triggerFull,exitFull}=useFullscreen(onFulls);` 내부함수를 사용하기 위해 define

결과 이미지를 풀스크린으로 만드는 버튼인 hooks
