---
layout: post
title: React⚛ Hooks-UseBeforeLeave
color: rgb(102,153,255)
tags: [websolute, team, React, Hooks, front-end, web, framework]
---

### UseBeforLeave

기본적으로 탭을 닫았을 때, 실행되는 페이지이다.

```javascript
const useBeforeLeave = (onBefore) => {
  if (typeof onBefore !== "function") {
    return;
  }

  const handle = (event) => {
    const { clientY } = event;

    if (clientY <= 0) {
      onBefore();
    }
  };
  useEffect(() => {
    document.addEventListener("mouseleave", handle);
    return () => document.removeEventListener("mouseleave", handle);
  }, []);
};

const App = () => {
  const begForLife = () => console.log("don't leave");
  useBeforeLeave(begForLife);
  return (
    <div className="App">
      <h1>Hello</h1>
    </div>
  );
};
```

```javascript
if (clientY <= 0) {
      onBefore();
    }
  };

const begForLife = () => console.log("don't leave");
```

마우스가 위로 벗어난경우에 argument 함수가 실행돼서 "don't leave"가 console에 뜬다.

`const handle = (event) => {` 에서 console.log로 event결과를 확인하면, 마우스가 위로 벗어나면 음수. 아래로 벗어나면 양수가 나온다.(clientY가)

```javascript
useEffect(() => {
  document.addEventListener("mouseleave", handle);
  return () => document.removeEventListener("mouseleave", handle);
}, []);
```

componentWillUnmount일 때 remove해준다.
