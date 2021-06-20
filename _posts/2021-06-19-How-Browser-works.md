---
layout: post
title: '[Network]How Browser works?'
tags: [Browser, Computer Science, Network]
featured_image_thumbnail:
featured_image: assets/images/posts/2018/6.jpg
---

## 브라우저 동작원리

> 브라우저는 어떤 과정을 거쳐 우리에게 보여질까?

### 브라우저의 주요기능

> 사용자가 선택한 자원을 서버에 요청, 브라우저 표시

- 자원은 html, pdf, image 등 **다양**하다.
- 브라우저는 html,css의 명세(어떻게 구현할지)에 따라 **html을 해석해서** 표시한다.
- 표준 명세는 웹 표준화 기구인 W3C에서 정해짐  
  (**따르지 않으면 호환성 문제 발생**)

### 브라우저의 인터페이스

> 시간이 지나면서, 사용자에게 필요한 서비스들로 서로 모방하며 갖춰지게됨.

- URI 입력하는 주소 표시줄
- 이전, 다음 버튼
- 북마크(즐겨찾기)
- 새로고침 버튼
- 홈버튼

### 브라우저 기본 구조

![BrowserStructure](/assets/images/posts/2021/BrowserStructure.png)
<small>Browser Structure</small>

- ##### 사용자 인터페이스

- ##### 브라우저 엔진
- ##### 렌더링 엔진
- ##### 통신
- ##### UI 백엔드
- ##### 자바스크립트 해석기
- ##### 자료 저장소
