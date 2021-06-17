---
layout: post
title: '[Network]TCP 3-way Handshake'
tags: [JavaScript, Tips, Node]
featured_image_thumbnail:
featured_image: assets/images/posts/2019/laptop.jpg
featured: true
hidden: true
---

## TCP 3-way Handshake  
TCP가 당췌 무엇인지도 모르겠고, 3가지 악수??3번 악수? 악수를 왜 한다는지 잘모르겠다.
아래 그림을 살펴보자.

![TCP Handshake](/assets/images/posts/2021/TCP%20Handshake.png)
<small style="display:block; text-align:center">TCP 3-way Handshake<small>  

먼저, 왼쪽이 클라이언트, 오른쪽이 서버라는 것 같다.  
1. 클라이언트는 요청을 **connect** 펑션을 통해 보내고  
2. 서버는 listen 하고 있다가 요청을 받고 **accept** 펑션으로 응답을 보낸다.  
3. 클라이언트는 서버의 수락 응답을 받고 클라이언트에게 <span style="text-decoration:underline;">잘 받았다는 응답</span>을 보내면 **연결이 성립**!

 


 ```

 작성중
 -------------------------------------------
 주말 마무리예정
 ```

