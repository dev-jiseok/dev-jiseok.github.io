---
layout: post
title: React⚛ Hooks-UseTabs
color: rgb(102,153,255)
tags: [websolute, team, React, Hooks, front-end, web, framework]
---

<p align = "center"><img src="https://miro.medium.com/max/6300/1*buOLbtsDPRK8VLxlMTAmLQ.jpeg" width = "75%"></p>

### UseTabs

```javascript
const content = [
  {
    tab: "Section 1",
    content: "I'm the content of the Section 1",
  },
  {
    tab: "Section 2",
    content: "I'm the content of the Section 2",
  },
];

const useTabs = (initialTab, allTabs) => {
  const [currentIndex, SetCurrentIndex] = useState(initialTab);
  if (!allTabs ?? !Array.isArray(allTabs)) {
    return;
  }
  return {
    currentItem: allTabs[currentIndex],
    changeItem: SetCurrentIndex,
  };
};

const App = () => {
  const { currentItem, changeItem } = useTabs(1, content);
  return (
    <div className="App">
      {content.map((section, index) => (
        <button onClick={() => changeItem(index)}>{section.tab}</button>
      ))}
      <div> {currentItem.content} </div>
    </div>
  );
};
```

```javascript
if (!allTabs ?? !Array.isArray(allTabs)) {
  return;
}
```

array가 아니면 실행이 안되게 해준다.

```javascript
const useTabs = (initialTab, allTabs) => {
  const [currentIndex, SetCurrentIndex] = useState(initialTab);
  return {
    currentItem: allTabs[currentIndex],
    changeItem: SetCurrentIndex,
  };
};
```

initialTab = index, allTabs = array

setCurrentIndex = state를 update시켜준다.

changeItem:SetCurrentIndex 는 map의 index를 통해 변화하는 인덱스로 업데이트 하기 위한 변수

```javascript
const App = () => {
  const { currentItem, changeItem } = useTabs(1, content);
  return (
    <div className="App">
      {content.map((section, index) => (
        <button onClick={() => changeItem(index)}>{section.tab}</button>
      ))}
      <div> {currentItem.content} </div>
    </div>
  );
};
```

버튼을 클릭하면 changeItem이 실행되고 index값이 바뀌고

그건 SetCurrentIndex의 item을 바꿔준다.

이는 state를 바꾸고 이로 인해 currentItem의 currentIndex도 바뀌게 된다.
