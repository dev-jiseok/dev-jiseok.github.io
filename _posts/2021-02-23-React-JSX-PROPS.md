---
layout : post
title : React⚛ JSK & PROPS
color: rgb(242,85,44)
tags: [websolute,team,React,front-end,web,framework]
---

### Creating your first React Component

```javascript
//src/App.js

import React from "react";
 import Potato from "./Potato";

 function App() {
   return (
     <div>
       <h1>Hello</h1>
       <Potato />
     </div>
   );
 }
 ```

```javascript
//src/Potato.js 

import React from "react";

 function Potato() {
   return <h3>I love potato</h3>;
 }

 export default Potato;
```

> ```index.js```에 있는 ```<App />```는 component이다.

> <strong>react의 모든 것은 component로 동작한다.</strong> 
> 웹을 만들기 위해서 component를 만들어야 하고 component를 보기 좋게 꾸며야하고, component가 data를 보여주게 만들어야한다. 
> component란 HTML을 반환하는 함수이다.

<br>

>```App.js```에 우리는 function application을 가지고 있고 이것은 HTML을 반환해준다. ```index.js```에 있는 ```<App />```이 우리가 사용할 component의 형태이다. react는 component를 사용해서 HTML처럼 작성하려는 경우에 필요하다. 이러한 자바스크리트와 HTML사이의 조합을 jsx라고 부른다.

>jsx는 자바스크립트안의 HTML이다.

>react application은 한 번에 하나의 component만 rendering할 수 있다. (index.js에 2개의 component를 넣는 방법이 아니라 ```index.js```에 App component를 넣었으면 ```App.js```안에 또 Potato component를 넣는 방식)

<br>
<br>

### Reusable Components with JSX + Props 

```javascript
import React from "react";


 function Food({ favourite }) {
   return <h1>I like {favourite}</h1>;
 }

 function App() {
   return (
     <div>
       <h1>Hello</h1>
       <Food favourite="kimchi" />
       <Food favourite="ramen" />
       <Food favourite="samgiopsal" />
       <Food favourite="chukumi" />
     </div>
   );
 }
export default App;
```

(function App에서 function Food로 정보를 보내는 방법)

> ```<Food />``` 를 ```<Food favourite="kimchi" />```로 수정한다.
>food component에 kimchi라는 value로 prop name을 준 것

Food component에 props를 추가해준다.

<br>
<br>

### Dynamic Component Generation

```javascript
import React from "react";

 function Food({ name, picture }) {
   return (
     <div>
       <h2>I like {name}</h2>
       <img src={picture} />
     </div>
   );
 }

 const foodILike = [
   {
     name: "Kimchi",
     image:
       "http://aeriskitchen.com/wp-content/uploads/2008/09/kimchi_bokkeumbap_02-.jpg"
   },
   {
     name: "Samgyeopsal",
     image:
       "https://3.bp.blogspot.com/-hKwIBxIVcQw/WfsewX3fhJI/AAAAAAAAALk/yHxnxFXcfx4ZKSfHS_RQNKjw3bAC03AnACLcBGAs/s400/DSC07624.jpg"
   },
   {
     name: "Bibimbap",
     image:
       "http://cdn-image.myrecipes.com/sites/default/files/styles/4_3_horizontal_-_1200x900/public/image/recipes/ck/12/03/bibimbop-ck-x.jpg?itok=RoXlp6Xb"
   },
   {
     name: "Doncasu",
     image:
       "https://s3-media3.fl.yelpcdn.com/bphoto/7F9eTTQ_yxaWIRytAu5feA/ls.jpg"
   },
   {
     name: "Kimbap",
     image:
       "http://cdn2.koreanbapsang.com/wp-content/uploads/2012/05/DSC_1238r-e1454170512295.jpg"
   }
 ];

 function App() {
   return (
     <div>
       {foodILike.map(dish => (
         <Food name={dish.name} picture={dish.image} />
       ))}
     </div>
   );
 }
export default App;
```

>```App.js``` 파일에 새로운 배열을 생성해준다.
>function App()에 map함수를 이용해서 foodILike 배열에 있는 people과 name을 각각 출력할 수 있도록 코드를 만든다.
>그리고 function Food에 name과 number의 object가 각각 들어갈 수 있도록 함수를 작성해준다.

<br>
<br>

### map Recap

```javascript
import React from "react";

 const foodILike = [
   {
     id: 1,
     name: "Kimchi",
     image:
       "http://aeriskitchen.com/wp-content/uploads/2008/09/kimchi_bokkeumbap_02-.jpg"
   },
   {
     id: 2,
     name: "Samgyeopsal",
     image:
       "https://3.bp.blogspot.com/-hKwIBxIVcQw/WfsewX3fhJI/AAAAAAAAALk/yHxnxFXcfx4ZKSfHS_RQNKjw3bAC03AnACLcBGAs/s400/DSC07624.jpg"
   },
   {
     id: 3,
     name: "Bibimbap",
     image:
       "http://cdn-image.myrecipes.com/sites/default/files/styles/4_3_horizontal_-_1200x900/public/image/recipes/ck/12/03/bibimbop-ck-x.jpg?itok=RoXlp6Xb"
   },
   {
     id: 4,
     name: "Doncasu",
     image:
       "https://s3-media3.fl.yelpcdn.com/bphoto/7F9eTTQ_yxaWIRytAu5feA/ls.jpg"
   },
   {
     id: 5,
     name: "Kimbap",
     image:
       "http://cdn2.koreanbapsang.com/wp-content/uploads/2012/05/DSC_1238r-e1454170512295.jpg"
   }
 ];

 function Food({ name, picture }) {
   return (
     <div>
       <h2>I like {name}</h2>
       <img src={picture} alt={name} />
     </div>
   );
 }

 function App() {
   return (
     <div>
       {foodILike.map(dish => (
         <Food key={dish.id} name={dish.name} picture={dish.image} />
       ))}
     </div>
   );
}

export default App;
```

>Warning: Each child in a list should have a unique "key" prop. 문구가 뜨는데
>foodILike Array 각각에 id를 주고 key prop을 사용해서 dish.id를 추가해준다. 
>return 시키지 않아서 출력되지는 않지만 에러가 사라진 것을 볼 수 있다. id는 react 내부에서 쓰기 위해서 정의한 것을 알 수 있다.

<br>
<br>

### Protection with PropTypes

```
//package.json

  "version": "0.1.0",
   "private": true,
   "dependencies": {
     "prop-types": "^15.7.2",
     "react": "^16.8.6",
     "react-dom": "^16.8.6",
     "react-scripts": "3.0.1"
```

>prop-types를 설치하여 내가 전달받은 props가 내가 원하는 props인지를 확인해 준다.
>터미널에 npm i prop-types 명령어를 통해서 prop-types를 설치해준다. 
>prop-types를 통해서 우리가 맞는 prop을 받았는지 확인이 가능하다.



<br>

```javascript
//src/App.js

import React from "react";
 import PropTypes from "prop-types";

 const foodILike = [
  {
    id: 1,
    name: "Kimchi",
    image:
      "http://aeriskitchen.com/wp-content/uploads/2008/09/kimchi_bokkeumbap_02-.jpg"
  },
   {
     id: 2,
     name: "Samgyeopsal",
     image:
       "https://3.bp.blogspot.com/-hKwIBxIVcQw/WfsewX3fhJI/AAAAAAAAALk/yHxnxFXcfx4ZKSfHS_RQNKjw3bAC03AnACLcBGAs/s400/DSC07624.jpg",
     rating: 4.9
   },
   {
     id: 3,
     name: "Bibimbap",
     image:
       "http://cdn-image.myrecipes.com/sites/default/files/styles/4_3_horizontal_-_1200x900/public/image/recipes/ck/12/03/bibimbop-ck-x.jpg?itok=RoXlp6Xb",
     rating: 4.8
   },
   {
     id: 4,
     name: "Doncasu",
     image:
       "https://s3-media3.fl.yelpcdn.com/bphoto/7F9eTTQ_yxaWIRytAu5feA/ls.jpg",
     rating: 5.5
   },
   {
     id: 5,
     name: "Kimbap",
     image:
       "http://cdn2.koreanbapsang.com/wp-content/uploads/2012/05/DSC_1238r-e1454170512295.jpg",
     rating: 4.7
   }
 ];

 function Food({ name, picture, rating }) {
   return (
     <div>
       <h2>I like {name}</h2>
       <h4>{rating}/5.0</h4>
       <img src={picture} alt={name} />
     </div>
   );
 }

 Food.propTypes = {
   name: PropTypes.string.isRequired,
   picture: PropTypes.string.isRequired,
   rating: PropTypes.number
 };

 function App() {
   return (
     <div>
       {foodILike.map(dish => (
         <Food
           key={dish.id}
           name={dish.name}
           picture={dish.image}
           rating={dish.rating}
         />
       ))}
     </div>
   );
}
export default App;
```

>Food.propTypes 안에 코드를 채워넣고 코드를 통해서 맞게 prop이 나오고 있는지 확인할 수 있다.