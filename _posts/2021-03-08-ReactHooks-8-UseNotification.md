---
layout: post
title: React⚛ Hooks-UseNotification
color: rgb(242,85,44)
tags: [websolute, team, React, Hooks, front-end, web, framework]
---

### UseNotification

```javascript
const useNotification = (title, options) => {
  if (!("Notification" in window)) {
    return;
  }
  const fireNotif = () => {
    if (Notification.permission !== "granted") {
      Notification.requestPermission().then((permission) => {
        if (permission === "granted") {
          new Notification(title, options);
        } else {
          return;
        }
      });
    } else {
      new Notification(title, options);
    }
  };
  return fireNotif;
};

const App = () => {
  const triggertNotif = useNotification("Can I steal your kimchi?", {
    body: "I love kimchi",
  });
  return (
    <div className="App">
      <button onClick={triggertNotif}>Hello</button>
    </div>
  );
};
```

granted는 사용자가 알림받길 승인

UseNotification는 알람이 실행되는 function이다.
