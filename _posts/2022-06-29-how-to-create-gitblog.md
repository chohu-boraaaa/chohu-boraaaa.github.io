---   
layout: post  
title: "[Making my own Gitblog] 나만의 깃블로그 만들기"
date: 2022-06-29
excerpt: "This post is about how to make gitblog with git, visual studio code, and jekyll."
project: false
tag:
- gitblog
comments: false
---  

<center><b>들어가며</b></center>
     
  데이터 사이언티스트가 되기 위해 깃블로그를 제작하여 공부한 내용을 올리고자 하였습니다.\
  그런데, 깃블로그 만드는 게 이렇게 어려운 일인지 몰랐어요ㅠㅠ\
  그래서 돌고돌아 결국 해내고 말았습니다ㅠㅠ\
  이 글을 읽는 모든 분들은 부디 시간 오래 걸리지 말고 깃블로그를 제작했으면 좋겠습니다ㅠㅠ


저는 [Yeong A Lee님의 블로그 참고하여 제작했습니다!](https://simpled2ev.github.io/develop-github/2019/02/13/2019-01-31-github-make-git-and-jekyll-blog1.html ) 이 블로그 덕분에ㅠ 깃블로그 만들 수 있었어요ㅠㅠ 감사합니다!🙏

## 1. 깃허브 아이디 및 주소 만들기

## 2. Git 설치하기
---
### 1) 깃 설치

### 2) 윈도우 검색창에 **git bash** 입력
![gitbash](https://user-images.githubusercontent.com/77424107/176376359-ccc7e25e-2309-449c-9be1-ccdd616721e9.png)

### 3) 깃허브아이디, 이메일 넣어주기
![image](https://user-images.githubusercontent.com/77424107/176377164-952bc747-0f45-4ea4-966a-28be248fe4bf.png)

## 3. Jekyll 테마 적용하기
---
- 자신이 마음에 드는 테마 선택해서 고르기!
- 저는 moon 테마를 적용하였습니다. [moon 테마 적용하러 가기](https://github.com/TaylanTatli/Moon)
- 위의 moon 테마 소스코드를 내 리포지토리로 **Fork**
- 가져온 리포지토리 이름을 <**사용자아이디.github.io**>로 바꾸기.
- 깃블로그가 publish 될 때까지 약간의 시간이 걸릴 수 있습니다.

## 4. 복사한 jekyll 파일 수정 위해, **Git Bash** 실행
---
### 1) **Git Clone**을 통해 깃허브 리포지토리에 있던 파일들을 로컬에 복사하기
- clone 하는 방법도 [Yeong A Lee님의 블로그를 참고하였습니다!](https://simpled2ev.github.io/develop-github/2019/02/13/2019-02-01-github-make-git-and-jekyll-blog2.html)

### 2) Visual Studio Code 설치
- 다운로드 : https://code.visualstudio.com/download
- vscode에서 깃블로그를 편집하고, 포스트를 올려주면 됩니다.

### 3) _config.yml 파일 수정하기
- 여기에서 title, description, 이메일 주소, sns 주소 등을 설정하여 파일을 수정하면 됩니다.

### 4) 수정한 파일 깃허브에 올리기
- git add '수정한 파일명'
- git commit -m 'commitmessage'
- git push
![image](https://user-images.githubusercontent.com/77424107/176379849-f90a42b8-726d-499c-8a57-8262785f6a40.png)
- 깃블로그가 수정한 대로 publish 될 때까지 약간의 시간이 걸릴 수 있습니다.

## 5. 깃블로그에 포스트 올리기
---
### 1) 확장 프로그램 설치 - Auto-Open Markdown 설치
- vscode>왼쪽 bar의 테트리스 같은 아이콘 클릭
- vscode에서 위 확장 프로그램을 설치하면 markdown을 실시간으로 작성하면서 어떻게 화면에 보이는지 알 수 있습니다.
![image](https://user-images.githubusercontent.com/77424107/176380696-0595f4c1-28a0-4cf6-88ad-52da6db00544.png)

### 2) 포스트는 _posts 폴더에 파일을 추가하여 작성
- 파일 이름 : **yyyy-mm-dd-title.md** 형태
- 마크다운 문법과 같아서 평소 마크다운을 자주 사용하신 분이라면 이 부분은 쉬울 것 같습니다!

### +a) 포스트에 로컬 이미지 삽입 원한다면
- github 리포지토리>Issues>New Issue>이미지 파일 복붙하거나 드래그>주소 자동 생성>submit new issue 안눌러도 됨
- 이 내용은 https://lemonlemon.tistory.com/178 이 분의 블로그에 잘 나와있습니다!

### 3) 포스트 깃허브에 올리기
