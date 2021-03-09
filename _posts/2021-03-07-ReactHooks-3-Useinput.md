---
layout: post
title: React⚛ Hooks-UseInput
color: rgb(242,85,44)
tags: [websolute, team, React, Hooks, front-end, web, framework]
---

<p align = "center"><img src="https://miro.medium.com/max/6300/1*buOLbtsDPRK8VLxlMTAmLQ.jpeg" width = "75%"></p>

### UseInput

```javascript
const useInput = (initialValue) => {
  const [value, setValue] = useState(initialValue);
  const onChange = (event) => {
    console.log(event.target);
  };
  return { value, onChange };
};
const App = () => {
  const name = useInput("Mr.");
  return (
    <div className="App">
      <input placeholder="Name" {...name} />
    </div>
  );
};
```

`{...name}`은 `value={name.value} onchange={name.onChange}`을 name안에있는 모든것을을 unpack한것.!

<br>
<br>

### UseInput part Two

```javascript
const useInput = (initialValue, validator) => {
  const [value, setValue] = useState(initialValue);
  const onChange = (event) => {
    const {
      target: { value },
    } = event;
    let willUpadate = true;
    if (typeof validator === "function") {
      willUpadate = validator(value);
    }
    if (willUpadate) {
      setValue(value);
    }
  };
  return { value, onChange };
};
```

```javascript
const App = () => {
  const name = useInput("Mr.");
	const maxlen=(value)=>!value.includes(“@”);
  return (
    <div className="App">
      <input placeholder="Name" {...name} />
    </div>
  );
};
```

`const maxlen=(value)=>!value.includes(“@”);`를 추가하여 @들어가면 업데이트 불가능하게 해준다.
