---
layout: post
title: React⚛ Hooks-UseTitle
color: rgb(102,153,255)
tags: [websolute, team, React, Hooks, front-end, web, framework]
---

### UseTitle

```javascript
const useTitle = (initialTitle) => {
  const [title, setTitle] = useState(initialTitle);
  const updateTitle = () => {
    const htmlTitle = document.querySelector("title");
    htmlTitle.innerText = title;
  };
  useEffect(updateTitle, [title]);
  return setTitle;
};

const App = () => {
  const titleUpdater = useTitle("Loading...");
  setTimeout(() => titleUpdater("Home"), 5000);
  return (
    <div className="App">
      <div>Hi</div>
    </div>
  );
};
```

```javascript
const htmlTitle = document.querySelector("title");
```

html tag의 title을 얻는다.

```javascript
useEffect(updateTitle, [title]);
```

componentDidMount이거나 title이 업데이트되면, updateTitle함수 호출을 해준다.

```javascript
setTimeout(() => titleUpdater("Home"), 5000);
```

5초 뒤 title은 Home으로 바뀐다.
