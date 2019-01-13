---
title: Windows에서 github 블로그 만들기
layout: post
categories: etc
---

### 개요
1. WSL설치
* [https://kjglehs.github.io/etc/2019/01/13/install-wsl.html](https://kjglehs.github.io/etc/2019/01/13/install-wsl.html)
2. jekyll 설치, 블로그 생성
3. admin 설치 
4. 테마 설치
5. github 배포

### windows에 jekyll 설치
1. terminal > bash
2. sudo apt-get update -y && sudo apt-get upgrade -y
3. 저장소 추가 및 루비 설치
*  sudo apt-add-repository ppa:brightbox/ruby-ng
*  sudo apt-get update
*  sudo apt-get install ruby2.3 ruby2.3-dev build-essential dh-autoreconf
4. 루비 젬들 업데이트  
* sudo gem update
5. jekyll 설치
* sudo gem install jekyll bundler
6. 설치 확인
* jekyll -v
7. bundler 와 루비 젬의 경로를 설정
* bundle config path vendor/bundle
8. 블로그 생성
* workspace로 이동
* jekyll new 설치할 블로그명(kjglehs.github.io)
9. 설치 확인
* cd kjglehs.github.io
* jekyll serve
* localhost:4000

### Admin설치
1. 추가한 프로젝트 Gemfile에 아래 내용 추가
* gem 'jekyll-admin', group: :jekyll_plugins
2. 설치
* bundle install
3. 서버 재시작
4. http://localhost:4000/admin

### 테마 적용
1. 테마 다운로드([http://jekyllthemes.org/](http://jekyllthemes.org/))
* 적용 테마([http://lanyon.getpoole.com/](http://lanyon.getpoole.com/))
2. 프로젝트 소스에 테마 관련 내용 복사
* _config.yml(설정파일) 수정
* _includes폴더, _layouts폴더, public 폴더 등 복사 

### github push
1. git init
2. .gitignore에 내용 추가
* vendor/**

3. git add .
4. git commit -m 'first commit'
5. git remote add origin https://github.com/kjglehs.github.io.git
6. git remote -v
7. git push origin master

댓글 추가
[https://devmjun.github.io/archive/addComments](https://devmjun.github.io/archive/addComments)