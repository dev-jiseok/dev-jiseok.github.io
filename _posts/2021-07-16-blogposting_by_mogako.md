---
layout: post
title: Oechul_Front_Survey_No.2 by 모각코
color: rgb(204,102,255)
tags: [hufstory, team, web, front-end, project, css]
---

### CSS Grid

- Flex는 한 방향 레이아웃 시스템이고 (1차원)
- Grid는 두 방향(가로-세로) 레이아웃 시스템 (2차원)

<p align="center"><img src = "https://user-images.githubusercontent.com/76767226/125906480-6b077d73-af8d-4b7c-a4dc-97f14b6c612b.jpg" width="75%"></p>

Grif는 Flex보다 더 복합적인 레이아웃 표현이 가능!

<br>

Grid 레이아웃을 만들기 위한 기본적인 HTML 구조는 다음과 같다.

```
<div class="container">
  <div class="item">A</div>
  <div class="item">B</div>
  <div class="item">C</div>
  <div class="item">D</div>
  <div class="item">E</div>
  <div class="item">F</div>
  <div class="item">G</div>
  <div class="item">H</div>
  <div class="item">I</div>
</div>
```

부모 요소인 div.container를 Grid Container(그리드 컨테이너)라고 부르고,

자식 요소인 div.item들을 Grid Item(그리드 아이템)이라고 부른다.

<strong>컨테이너가 Grid의 영향을 받는 전체 공간이고, 설정된 속성에 따라 각각의 아이템들이 어떤 형태로 배치되는 것</strong>

Flex와 마찬가지로, Grid는 컨테이너에 display: grid; 를 설정하는 것으로 시작한다.

```
.container {
  display: grid;
}
```

<p align="center"><img src="https://user-images.githubusercontent.com/76767226/125907153-43c77e1b-4cc8-4317-a928-c2e61ecdc19e.jpg" width="75%"></p>

- 그리드 컨테이너 (Grid Container)
  display: grid를 적용하는, Grid의 전체 영역입니다. Grid 컨테이너 안의 요소들이 Grid 규칙의 영향을 받아 정렬된다고 생각하면 됩니다. 위 코드 <div class=”container”></div>가 Grid 컨테이너예요.

- 그리드 아이템 (Grid Item)
  Grid 컨테이너의 자식 요소들입니다. 바로 이 아이템들이 Grid 규칙에 의해 배치되는 거예요. 위 코드에서 <div class=”item”></div>들이 Grid 아이템입니다.

- 그리드 트랙 (Grid Track)
  Grid의 행(Row) 또는 열(Column)

- 그리드 셀 (Grid Cell)
  Grid의 한 칸을 가리키는 말이예요. <div>같은 실제 html 요소는 그리드 아이템이고, 이런 Grid 아이템 하나가 들어가는 “가상의 칸(틀)”이라고 생각하면 됩니다.

- 그리드 라인(Grid Line)
  Grid 셀을 구분하는 선입니다.

- 그리드 번호(Grid Number)
  Grid 라인의 각 번호입니다.

- 그리드 갭(Grid Gap)
  Grid 셀 사이의 간격입니다.

- 그리드 영역(Grid Area)
  Grid 라인으로 둘러싸인 사각형 영역으로, 그리드 셀의 집합이예요.
