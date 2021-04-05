---
layout: post
title: React⚛ Hooks-UseClick
color: rgb(102,153,255)
tags: [websolute, team, React, Hooks, front-end, web, framework]
---

#### react에 있는 모든 component는 reference element를 가지고 있음

### UseClick

```javascript
const useClick=(onClick)=>{
  if(typeof onClick !=="function"){
    return;
  }
  const element=useRef();
  useEffect(()=>{
    if(element.current){
      element.current.addEventListener("click",onClick);
    }
    return ()=>{
      if(element.current(){
        element.current.removeEventListener("click",onClick);
      }
    };//componentWillunmount일때 return의 function 호출
  },[]);//no dependency
  return element;
};
```

```javascript
 const element=useRef();
  useEffect(()=>{
    if(element.current){
      element.current.addEventListener("click",onClick);
    }

```

component가 mount되었을 때 실행한다.

component가 unmount 일 때, 이벤트가 발생한 후 정리할 필요가 있다..

```javascript
return ()=>{
      if(element.current(){
        element.current.removeEventListener("click",onClick);
      }
    };
  },[]);
```

마지막에 []를 넣어주어 componentDidMount때 단 한번만 실행되라는 의미가 되게 해준다.

componentWillunmount일때 return의 function 호출
