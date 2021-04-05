---
layout: post
title: React⚛ Hooks-UseConfirm & UsePreventLeave
color: rgb(102,153,255)
tags: [websolute, team, React, Hooks, front-end, web, framework]
---

### UseConfirm & UsePreventLeave

이 두개의 Hooks는 실제로 Hooks가 아니다. 이 이유는 UseState와 UseEffect가 사용되지 않기 때문이다.

### UseConfirm

- 사용자가 버튼을 클릭하는 작업을 하면 이벤트를 실행하기 전에 메세지를 보여준다.

```javascript
const useConfirm = (message = "", onConfirm, onCancel) => {
  if (!onConfirm || typeof onConfirm !== "function") {
    return;
  }
  if (onCancel && typeof onCancel !== "function") {
    return;
  }
  const confirmAction = () => {
    if (window.confirm(message)) {
      onConfirm();
      //ok 누르면 실행
    } else {
      onCancel();
      //취소 누르면 실행
    }
  };
  return confirmAction;
};

const App = () => {
  const deleteWorld = () => console.log("Deleting the world");
  const abort = () => console.log("Aborted");
  const confirmDelete = useConfirm("Are you sure?", deleteWorld, abort);
  return (
    <div className="App">
      <button onClick={confirmDelete}>Delete the world</button>
    </div>
  );
};
```

버튼을 누르면 confirmDelete가 실행된다.

confirmDelete는 useConfirm실행해서 return 해주고 confirlAction 실행

### UsePreventLeave

```javascript
const usePreventLeave = () => {
  const listener = (event) => {
    event.preventDefault();
    event.returnValue = "";
  };
  const enablePrevent = () => window.addEventListener("beforeunload", listener);
  const disablePrevent = () =>
    window.removeEventListener("beforeunload", listener);
  return enablePrevent, disablePrevent;
};

const App = () => {
  const { enablePrevent, disablePrevent } = usePreventLeave();
  return (
    <div className="App">
      <button onClick={enablePrevent}>Protect</button>
      <button onClick={disablePrevent}>Unprotect</button>
    </div>
  );
};
```

`event.preventDefault();` 표준에 따라 기본동작 방지!

window창을 닫을 때 아직 저장했냐 안했냐 물어봄
