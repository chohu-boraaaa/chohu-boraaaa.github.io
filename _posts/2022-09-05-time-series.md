---   
layout: post  
title: "[TimeSeries] 시계열의 여러가지 방법론"
date: 2022-07-29
excerpt: "시계열 예측에 참고할만한 여러 방법론입니다."
tag:
- TimeSeries
comments: true
--- 

출처 : 논문 [🔗연속적인 시계열 예측을 위한
디노이징 다변량 시계열 모델링
(Denoising Multivariate Time Series Modeling for
Multi-step Time Series Prediction)](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/56bc92ef-7dac-474d-a7e8-b52067163d1e/%EC%97%B0%EC%86%8D%EC%A0%81%EC%9D%B8_%EC%8B%9C%EA%B3%84%EC%97%B4_%EC%98%88%EC%B8%A1%EC%9D%84_%EC%9C%84%ED%95%9C_%EB%94%94%EB%85%B8%EC%9D%B4%EC%A7%95_%EB%8B%A4%EB%B3%80%EB%9F%89_%EC%8B%9C%EA%B3%84%EC%97%B4_%EB%AA%A8%EB%8D%B8%EB%A7%81.pdf?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220905%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220905T091742Z&X-Amz-Expires=86400&X-Amz-Signature=4b1fb81c9193e48c13a93ed1d94774f251a007243d949143b67fb7b3e32e91e3&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25EC%2597%25B0%25EC%2586%258D%25EC%25A0%2581%25EC%259D%25B8%2520%25EC%258B%259C%25EA%25B3%2584%25EC%2597%25B4%2520%25EC%2598%2588%25EC%25B8%25A1%25EC%259D%2584%2520%25EC%259C%2584%25ED%2595%259C%2520%25EB%2594%2594%25EB%2585%25B8%25EC%259D%25B4%25EC%25A7%2595%2520%25EB%258B%25A4%25EB%25B3%2580%25EB%259F%2589%2520%25EC%258B%259C%25EA%25B3%2584%25EC%2597%25B4%2520%25EB%25AA%25A8%25EB%258D%25B8%25EB%25A7%2581.pdf%22&x-id=GetObject)

![image1](https://user-images.githubusercontent.com/77424107/188415885-92af14f4-cef2-45d5-8ea6-77e5a5335aeb.png)

![image2](https://user-images.githubusercontent.com/77424107/188416039-3cad13c7-2f71-4937-a5eb-e2c2ed417837.png)

![image](https://user-images.githubusercontent.com/77424107/188416157-bc88dde7-ccdc-47ed-a6d8-e8f993378fa9.png)