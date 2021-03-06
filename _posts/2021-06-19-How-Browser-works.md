---
layout: post
title: '[Network]How Browser works?'
tags: [Browser, Computer Science, Network]
featured_image_thumbnail:
featured_image: assets/images/posts/2018/6.jpg
featured: true
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
  - 주소표시줄, 이전/다음 버튼, 북마크 등 사용자가 **활용하는 서비스들** (요청한 페이지를 보여주는 창을 제외한 나머지 부분)  
- ##### 렌더링 엔진  
  -  요청한 컨텐츠 표시 (Ex, HTML 요청이 들어오면 html,css 파싱해서 화면에 표시)  
- ##### 브라우저 엔진  
  -  사용자 인터페이스와 랜더링 엔진 사이의 동작 제어
- ##### 통신  
  -  http요청과 같은 **네트워크 호출**에 사용   (플랫폼의 독립적인 인터페이스로 구성됨)-< 무슨소리일까? ???  
- ##### UI 백엔드  
  -  플랫폼에서 명시하지 않은 일반적 인터페이스. 콤보박스 창같은 기본적 장치를 그림  <--얘도 뭔지잘모르겠음. 찾아보자  
- ##### 자바스크립트 해석기  
  -  자바스크립트 코드를 해석하고 실행
- ##### 자료 저장소  
  -  쿠키 등 모든 종류의 **자원을** 하드디스크에 **저장하는** 계층

### 랜더링이란?  
  > 브라우저에 요청받은 내용을 표시해주는 것  
  - 기본적으로 html, xml, 이미지를 표시할 수 있다.  
  - 추가로 플러그인이나 브라우저 확장 기능으로 pdf 등 다른유형도 표시가 가능하다.  

 ##### 랜더링 엔진 종류  
 - 크롬, 사파리 : 웹킷(Webkit) 엔진 사용  
 - 파이어폭스 : 게코(Gecko)엔진 사용  

 - 웹킷(Webkit): 최초 리눅스 플랫폼에 동작하기 위한 오픈소스 엔진  

### 랜더링 동작 과정

![Rendering](../assets/images/posts/2021/Rendering.png)
<small>Rendering</small>

```
먼저 html 문서를 파싱한다.

그리고 콘텐츠 트리 내부에서 태그를 모두 DOM 노드로 변환한다.

그 다음 외부 css 파일과 함께 포함된 스타일 요소를 파싱한다.

이 스타일 정보와 html 표시 규칙은 
렌더 트리라고 부르는 또 다른 트리를 생성한다.

이렇게 생성된 렌더 트리는 정해진 순서대로 화면에 표시되는데, 
생성 과정이 끝났을 때 배치가 진행되면서 
노드가 화면의 정확한 위치에 표시되는 것을 의미한다.

이후에 UI 백엔드에서 렌더 트리의 각 노드를 가로지으며 
형상을 만드는 그리기 과정이 진행된다.

이러한 과정이 점진적으로 진행되며, 렌더링 엔진은 좀더 빠르게 
사용자에게 제공하기 위해 모든 html을 파싱할 때까지 기다리지 않고 
배치와 그리기 과정을 시작한다. (마치 비동기처럼..?)

전송을 받고 기다리는 동시에 받은 내용을 먼저 화면에 보여준다
(우리가 웹페이지에 접속할 때 한꺼번에 뜨지 않고 점점 화면에 나오는 것이 이 때문!!!)
```

### DOM이란?  
**Document Object Model (문서 객체 모델)**

- html, body 같은 태그를 Javascript가 활용할 수 있는 객체로 만들면 <m>문서 객체</m>가 된다.  
- 모델은 말 그대로, 모듈화로 만들었다거나 <m>객체를 인식한다</m> 고 해석하면 된다.  

> 즉, DOM은 웹 브라우저가 html페이지를 인식하는 방식을 말한다.(**트리구조**)  

### 웹킷 동작구조

![Webkit](../assets/images/posts/2021/Webkit.png)
<small>Webkit</small>

### 파싱과 DOM 트리 구축  

- 파싱(parsing) : 브라우저가 코드를 이해하고 사용할 수 있는 구조로 변환하는 것  
- (**어휘 분석, 구문분석**) 과정을 거쳐 파싱 트리를 구축한다.  

- 웹킷은 flex나 bison이라는 파서 생성기를 이용하여 유용하게 파싱을 한다.  
  **그리고 자잘한 실수는 똑똑한 파서가 수정해줌 ㅎㅎ**  

  > 결국 서버로 부터 받은 문서를 부라우저가 이해하고 쉽게 사용할 수있는 DOM트리구조로 변환시켜주는 것!  



  ### 정리  

주소창에 url을 입력하고 Enter를 누르면, 서버에 요청이 전송됨

해당 페이지에 존재하는 여러 자원들(text, image 등등)이 보내짐

이제 브라우저는 해당 자원이 담긴 html과 스타일이 담긴 css를 W3C 명세에 따라 해석할 것임

이 역할을 하는 것이 '**렌더링 엔진**'

렌더링 엔진은 우선 html 파싱 과정을 시작함. html 파서가 문서에 존재하는 어휘와 구문을 분석하면서 **DOM 트리를 구축**

다음엔 css 파싱 과정 시작. css 파서가 모든 css 정보를 스타일 구조체로 생성

이 2가지를 연결시켜 렌더 트리를 만듬. **렌더 트리**를 통해 문서가 시각적 요소를 포함한 형태로 구성된 상태

화면에 배치를 시작하고,**UI 백엔드**가 노드를 돌며 형상을 그림

이때 빠른 브라우저 화면 표시를 위해 '배치와 그리는 과정'은 페이지 정보를 모두 받고 한꺼번에 진행되지 않음. 자원을 전송받으면, 기다리는 동시에 일부분 먼저 진행하고 화면에 표시함




