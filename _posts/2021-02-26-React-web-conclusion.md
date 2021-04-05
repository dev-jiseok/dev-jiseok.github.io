---
layout: post
title: React⚛ CONCLUSIONS
color: rgb(0,153,255)
tags: [websolute, team, React, front-end, web, framework]
---

### Deploying to Github Pages

```
{
  "name": "movie_app_2021",
  "version": "0.1.0",
  "private": true,
  "dependencies": {
    "@testing-library/jest-dom": "^5.11.9",
    "@testing-library/react": "^11.2.5",
    "@testing-library/user-event": "^12.7.0",
    "axios": "^0.21.1",
    "gh-pages": "^3.1.0",
    "prop-types": "^15.7.2",
    "react": "^17.0.1",
    "react-dom": "^17.0.1",
    "react-scripts": "4.0.2",
    "web-vitals": "^1.1.0"
  },
  "scripts": {
    "start": "react-scripts start",
    "build": "react-scripts build",
    "deploy": "gh-pages -d build",
    "predeploy": "npm run build"
  },
  "eslintConfig": {
    "extends": [
      "react-app",
      "react-app/jest"
    ]
  },
  "browserslist": {
    "production": [
      ">0.2%",
      "not dead",
      "not op_mini all"
    ],
    "development": [
      "last 1 chrome version",
      "last 1 firefox version",
      "last 1 safari version"
    ]
  },
  "homepage": "https://dev-jiseok.github.io/movie_app_2021/"
}
```

gh-page를 설치하여 나의 깃헙 아이디 뒤에 movie_app 이름을 치면 페이지와 연결되게 해주자! `"homepage": "https://dev-jiseok.github.io/movie_app_2021/"`을 추가하여 이를 연결해주자

```
"scripts": {
    "start": "react-scripts start",
    "build": "react-scripts build",
    "deploy": "gh-pages -d build",
    "predeploy": "npm run build"
  }
```

스크립트에서 deploy 와 predeploy를 추가하여 이를 완성하자!
