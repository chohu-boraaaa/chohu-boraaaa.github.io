---   
layout: post  
title: "[AI CHATBOT] anaconda tensorflow 구동 환경(가상 환경) 설정하기"
date: 2022-07-29
excerpt: "본 게시물은 박성백 강사님의 AI 챗봇 강의 - 5일차 강의를 듣고 배운 내용을 기록하였습니다."
tag:
- chatbot
comments: true
---  
- ❗ 문제 발견 : Solving environment: failed with initial frozen solve. Retrying with flexible solve.
- 🔵 해결 : conda update conda

# 1. conda update
- 시작 > Anaconda3 > Anaconda Prompt(anaconda3) >
- conda update conda
# 2. 가상환경 만들기
---
- 시작 > Anaconda3 > Anaconda Prompt(anaconda3) >
- conda create -n tf26 python=3.7 anaconda
- 만드는 동안 창 클릭하면 멈출 수 있는 데 이 때는 Esc를 누르면 잘 돌아간다.

# 3. tensorflow 설치 (2.6 버전)
---
- 시작 > Anaconda3 > Anaconda Prompt(tf26) >
- conda update conda
- conda install tensorflow==2.6

# 4. 실행
---
- 시작 > Anaconda3 > Jupyter Notebook(tf26)

# 5. 가상환경 삭제
- conda env remove -n tf26

---
## But,,, 실패...
