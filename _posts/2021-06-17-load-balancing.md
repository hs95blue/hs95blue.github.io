---
layout: post
title:  "[Network]로드밸런싱 Load Balancing"
tags: [ Tips, Development, Network  ]
featured_image_thumbnail:
featured_image: assets/images/posts/2018/3.jpg
---

## 로드 밸런싱

> 서버에게 균등하게 트래픽을 분산시켜주는 것  

요즘 시대에는 웹사이트에 접속하는 인원이 엄청나게 많다. 따라서 이 사람들에 대한 모든 트래픽을 감당하기엔 <m>1대의 서버로는 부족하다.</m>  

따라서 대응 방안으로 하드웨어의 **성능을 올리거나(Scale-up)** 여러대의 서버가 나눠서 일하도록(Scale-out) 해야한다.  

하드웨어의 <m>향상 비용이 비싸기도</m> 하고, 서버가 여러대면 서비스가 중단되지 않도록(<m>무중단 서비스</m>)하기 용이하므로 **나누는 것(Scale-out)**이 효과적이다.  

이때, 서버에게 <r>균등하게 트래픽을 나눠주는 것</r>이 **로드 밸런싱**이다.  


![Load Balancing](/assets/images/posts/2021/load%20balancing.png)
<small>Load Balancing</small>  

### 로드밸런서가 서버를 선택하는 방식

  > 이런저런 방식이 있다고 알아두고 넘기자   

  - **라운드 로빈**(Round Robin) : <m>부하 분산 방식</m> 랜덤으로 클라이언트에게 서버를 분배한다.
  - **Least Connections** : 연결 수가 <m>가장 적은 서버</m>를 선택하는 방식. (트래픽으로 세션이 길어질 때 권장)
  - **Source** : 사용자의 IP를 <m>Hashing</m> 하여[^1] 분배 하는 방식 (항상 <r>같은 서버로 연결보장</r>)













[^1]: hashing이란 많은 양의 데이터를 그보다는 작은 데이터테이블로 맵핑하는 것을 말한다.(**짝지어준다!**)

#### 더 자세히
<a href="https://nesoy.github.io/articles/2018-06/Load-Balancer">참고링크</a>