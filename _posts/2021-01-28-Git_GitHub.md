---
layout : post
title : Git_GitHub
color: rgb(242,85,44)
tags: [websolute,team,git,github]
---

### Git 그리고 GitHub 이란?

<p align="center"><img src="https://media.vlpt.us/images/yejikang/post/bcaee11f-cd1f-4ada-bc8b-bcd38d703af3/gitgithub.png" width="75%"></p>

#### Git 
>분산 소스 버전 관리 시스템
>서버를 분산시켜 구축할 수 있게 하는 소프트웨어
>소스코드를 효율적으로 관리할 수 있게 해주는 형상관리도구

<br>

#### GitHub
>깃(Git)을 사용하는 프로젝트를 지원하는 웹호스팅 서비스
>Git을 업로드 할 수 있는 웹사이트
>개발자들의 버전 제어 및 공동 작업을 위한 플랫폼

<br>
<br>
<br>

### 버전관리란?

<p align="center"><img src="https://evan-moon.github.io/static/99213a89a950fbd4dc194cf9b6cfc530/ee604/thumbnail.png" width="75%"></p>

>소스 하나 또는 묶음을 하나의 버전으로 간주
>파일이나 폴더를 추가, 수정, 삭제 하며 사람이 직접 관리한다.
>원할 때 예전 버전 내용 전체를 되돌려 볼 수 있으며 복잡한 코드를 개발할 때 이전 버전과 비교하기 수월하다는 이점이 있다.

<br>

#### 버전관리가 필요한 이유
>개발자간의 협업에 필요하다. 전체 개발 소스를 공유하면서 개발 파트를 나눌 수 있고 같은 모듈을 개발하더라도 소스를 서로 공유하며 개발할 수 있다.

<br>
<br>
<br>

### Git 필수용어

#### Repository(저장소)​

<p align="center"><img src="https://f1.codingworldnews.com/2019/06/eizfha8vfz.png" width="75%"></p>

>파일이 저장되는 저장소​
>Repo == Project Folder​
>Remote Repository​ : 원격 서버 저장소, 여러 사람과 공유​
>Local Repository​ : 직접 관리, 내 PC에 저장 ​

<br>
<br>

#### Commit​
- 프로젝트 변경이력

<p align="center"><img src="https://t1.daumcdn.net/cfile/tistory/9921A8335AEA9D9532" width="75%"></p>

>어떤 순간 작업공간의 상태를 저장한 것. 작업공간 안에 있는 모든 파일과 파일의 데이터를 사진 찍듯이 복사해서 저장소에 보존.
>즉 커밋은 작업공간의 어떤 시점의 스냅샷이라고 할 수 있다.
>'커밋한다'는 말은 커밋을 추가한다는 뜻. 즉 현재 작업공간의 상태를 커밋으로 만들어서 저장소에 저장한다는 의미.

<br>
<br>

#### Stage(기록)

<p align="center"><<img width="75%" alt="스크린샷 2021-01-28 오전 6 23 25" src="https://user-images.githubusercontent.com/76767226/106055914-60c8db80-6131-11eb-94f3-9f78960f4730.png"></p>

>Index: Commit을 통해 변경사항이 반영되기 전 해당 변경사항들이 저장되는 공간​
>특정 파일이나 코드를 변경시 해당 이력은 Index에 기록​이 기록되는 행위를 Stage 혹은 Staging이라고 함
>여러 변경 사항 중​ 원하는 변경사항만 Stage하고​ 원하지 않는 변경사항은 unstage 한뒤 Commit을 진행한다.

<br>
<br>

#### Branch

<p align="center"><img width="75%" alt="스크린샷 2021-01-28 오전 6 23 09" src="https://user-images.githubusercontent.com/76767226/106055909-5eff1800-6131-11eb-886e-55064c4f0f64.png"></p>

>여러명이 같은 코드를 공유하며 협업하는 경우​ 흐름을 나누고 합쳐야한다​
>Branch == 흐름을 나누는 기점

<br>
<br>

#### CheckOut
>현재 위치한 커밋에서 다른 커밋으로 이동​
>이전 시점으로 되돌아 가거나​ 다른 사람의 브랜치로 전환해 다른 개발자들의 코드 진행상황 확인

<br>
<br>

#### Merge

<p align="center"><img width="75%" alt="스크린샷 2021-01-28 오전 6 22 43" src="https://user-images.githubusercontent.com/76767226/106055899-5c9cbe00-6131-11eb-9bfe-0016e5227b47.png">
</p>

>여러명이 같은 코드를 공유하며 협업하는 경우​ 흐름을 나누고 합쳐야한다​
>Merge == 흐름을 하나로 합침
>Fast-Forward​ : 두 브랜치 자동 병합 -> 일부 문법에서 충돌(Conflict) 발생​
>Non Fast-Forward​ : 충돌 기록을 보면서 일일히 해당 코드를 수정 후 병합​
>Fast-Forward + Non Fast-Forward -> 성공적인 브랜치 병합

<br>
<br>

#### ​​​Clone

>오픈 소스 프로젝트의 시작​
>Clone은 원격저장소에서 특정 프로젝트를 통째로​ 내 로컬 저장소에 다운 받는 것

<br>
<br>

#### Push

>개인 저장소 -> 원격 저장소​
>현재 내 로컬에서 작업한 변경사항들을​ 원격 저장소에 반영하는 것​ 
>작업이 완료될 때 마다 원격 저장소에 PUSH해야​ 다른 사람들이 내 코드 확인 가능​

<br>
<br>

#### PULL

>개인 저장소 -> 원격 저장소​
>원격 저장소에 변경된 사항들을​ 내 로컬로 PULL해서 Update​ 다른 사람들의 코드를 내 작업창에서 확인 가능

<br>
<br>
<br>

### Flow: 고수준 관리 기법

- Feature - Develop - Release - Hotfix - Master​
- 목적에 맞추어 5개로 나누어 관리
<br>

>Master Branch​
>(메인 배포판) 실제로 클라이언트에서 이용하는 최종 형태의 메인 브랜치​
>추가 생성 및 삭제 X ​
<br>

>Develop Branch​
>(메인 개발) 현재 개발이 진행중인 브랜치​
>추가 생성 및 삭제 X​
<br>

>Feature Branch​
>(추가 기능 개발) 새로운 기능 개발을 위한 브랜치, 특정 기능 개발 시 Develop에서 파생 & 개발 완료시 병합​
>가장 많이 추가 및 삭제가 이루어지는 브랜치​
<br>

>Release Branch​
>(배포 준비, 오류 확인) 실제로 프로젝트를 배포하기위한 브랜치, Develop에서 파생​
>각종 오류 및 문제사항들을 검토 & 수정하는 일종의 테스트 서버, 수정 완료시 Master & Develop으로 병합​
<br>

>Hotfix Branch​
>(긴급 오류 수정) Hotfix branch는 배포된 Master branch의 갑작스런 버그가 발생하였을 때 급하게 Develop, Feature단계를 거치지 않고 버그를 수정하는 단계, 수정이 완료되면 Master & Develop으로 병합
