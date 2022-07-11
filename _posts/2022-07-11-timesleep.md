---   
layout: post  
title: "[Crawling] 크롤링에서 time.sleep() 해주는 이유"
date: 2022-07-11
excerpt: "크롤링 할 때 time.sleep()이 왜 필요할까요?"
tag:
- mysql
comments: true
---  

### 1. 코드의 실행속도가 너무 빨라, 웹 서버에 전송이 느려, 실제 사이트가 열리지도 않았는데 코드가 먼저 실행되는 경우.

### 2. 반복적 크롤링 작업은 서버에 많은 부하를 유발하여 ip가 정지당할 수도 있음. 쉬어감의 미학이 필요.

- 출처 : [https://ongbike.tistory.com/470](https://ongbike.tistory.com/470)