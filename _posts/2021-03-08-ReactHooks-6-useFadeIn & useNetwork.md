---
layout: post
title: React⚛ Hooks-UseFadeIn & UseNetwork
color: rgb(242,85,44)
tags: [websolute, team, React, Hooks, front-end, web, framework]
---

### UseFadeIn

서서히 나타나게 만든다. 말그대로 fadein

```javascript
const useFadeIn = (duration = 1, delay = 0) => {
  const element = useRef();

  useEffect(() => {
    if (element.current) {
      //우리가 원하는 DOM을 가리킴
      const { current } = element;
      current.style.transition = `opacity ${duration}s ease-in-out ${delay}s`; //${}:문자열로 반환
      current.style.opacity = 1;
    }
  }, []);
  if (typeof duration !== "number" || typeof delay !== "number") {
    return;
  }

  return { ref: element, style: { opacity: 0 } };
};

const App = () => {
  const fadeInH1 = useFadeIn(1, 2);
  const fadeInP = useFadeIn(5, 10);
  return (
    <div className="App">
      <h1 {...fadeInH1}>Hello</h1>
      <p {...fadeInP}>Hello2</p>
    </div>
  );
};
```

`return {ref:element,style:{opacity:0}};`

opacity=>투명도, component가 mount되면 Hello가 opacity,ease-in-out에 따라 서서히 나타난다.

```javascript
const App = () => {
  const fadeInH1 = useFadeIn(1, 2);
  const fadeInP = useFadeIn(5, 10);
  return (
    <div className="App">
      <h1 {...fadeInH1}>Hello</h1>
      <p {...fadeInP}>Hello2</p>
    </div>
  );
};
```

속성들이 참고돼서 reference,style가 들어온다.

### UseNetwork

navigator가 online 또는 offline이 되는 것을 막아줌(고정느낌)

```javascript
const useNetwork = (onChange) => {
  const [status, setStatus] = useState(navigator.onLine);

  const handleChange = () => {
    if (typeof onChange == "function") {
      onChange(navigator.onLine);
    }
    setStatus(navigator.onLine);
  };

  useEffect(() => {
    console.log("when");
    window.addEventListener("online", handleChange);
    window.addEventListener("offline", handleChange);
    return () => {
      window.removeEventListener("online", handleChange);
      window.removeEventListener("offline", handleChange);
    };
  }, []);
  return status;
};

const App = () => {
  const handleNetworkChange = (on) => {
    console.log(on ? "we just went online" : "we are offline");
  };
  const onLine = useNetwork(handleNetworkChange);
  return (
    <div className="App">
      <h1>{onLine ? "Online" : "Offline"}</h1>
    </div>
  );
};
```

```javascript
const useNetwork =onChange=>{
  const [status,setStatus]=useState(navigator.onLine);
```

network 상태가 바뀔때마다 function을 부른다

navigator.online -> 웹사이트가 온라인인지 아닌지 True & False나타낸다.
