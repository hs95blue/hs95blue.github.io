---
layout: post
title: '[Network]Blocking & Non Blocking I/O (feat.Sync, Async)'
tags: [Startup, Tips, Network]
featured_image_thumbnail: assets/images/posts/2018/4_thumbnail.jpg
featured_image: assets/images/posts/2018/4.jpg
featured: true
---

## Blocking & Non Blocking I/O

> 시스템을 호출할 때 **로직이 멈추느냐 안멈추느냐**의 차이!

### Blocking  

> 자신의 작업을 하다가 다른 주체의 작업이 시작되면 끝날때까지 **기다렸다가** 작업을 시작하는 것  

- I/O작업이 진행되는 동안 User Process(Thread)는 자신의 작업을 중단한 채 대기  
- Resource낭비가 심함(<m>I/O작업이 CPU자원을 거의 쓰지 않아서</m>)  


![Blocking](https://grip.news/wp-content/uploads/2019/06/bio_01.gif)
  <small>Blocking</small>

### Non Blocking

> 다른 주체와 **상관없이** 자신의 일을 하는 것  

- 



![Non-Blocking](https://grip.news/wp-content/uploads/2019/06/bio_02.gif)
 <small>Non-Blocking</small>




#### 궁금증
1. Kurnel은 무엇인가요?어떤 역할을 하나요?
2. context switch는 무엇인가요?
3. 프로세스와 스레드의 차이에 대해 설명해보세요
4. Sync Async와의 차이에 대해 설명해보세요