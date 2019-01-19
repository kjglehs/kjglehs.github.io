---
title: 개발 환경 구축
layout: post
categories: laravel
---

### 라라벨5 요구사항
* PHP >= 5.5.9
* PHP Extension : Mcrypt, OpenSSL, Mbstring, tokenizer

### 홈스테드
* Vagrant를 통해 라라벨 개발 환경을 구축할 수 있게 하는 프로젝트
* 가상 머신에 우분투, 웹서버, DBMS, PHP 스택 자동 설치 및 설정

### Vagrant
* 특정 환경의 가상 머신을 만들어 개발 환경 구축

#### Vagrant 설치
1. VirtualBox 설치
2. Git 설치
3. Vagrant 설치
    * [https://www.vagrantup.com/](https://www.vagrantup.com/)
    * 시스템 재부팅
    
### 홈스테드 구성
1. 라라벨 박스 생성
    * 사용자 홈 디렉토리
    * *vagrant box add laravel/homestead*
2. 환경 구성
    * 사용자 홈 디렉토리
    * *git clone https://github.com/laravel/homestead.git Homestead*
    * *cd Homestead*
    * *bash init.sh*
    * 설정 파일 : Homestead.yaml
        * authorize, keys : SSH 키 설정
        * folders : 공유 폴더 설정(workspace)
3. SSH 키 쌍 설정
    * 가상 머신을 연결할 때 사용할 키
    * *ssh-keygen -t rsa -C "이메일"*
4. 공유 폴더(workspace) 지정
    * 가상 머신과 공유할 디렉토리 지정
    * Homestead.yaml 의 공유 폴더 설정과 같은 경로에 폴더 생성
5. 웹 사이트 설정
    * Homestead.yaml -> sites 설정
    * hosts 파일 설정
        * 192.168.10.10 Homestead.yaml 의 sites 의 map 값
6. 박스 구동 및 중지
    * Homestead 폴더로 이동
    * 구동 
        * *vagrant up*
            * Vagrant network collides with a non-hostonly network 에러
                * Homestead.yaml 의 ip가 충돌 -> 다른 IP로 수정 , hosts 파일 수정
                    * [https://stackoverflow.com/questions/39049717/vagrant-network-collides-with-a-non-hostonly-network](https://stackoverflow.com/questions/39049717/vagrant-network-collides-with-a-non-hostonly-network)
    * 일시 중지
        * *vagrant suspend*
    * 박스 및 가상 머신 종료 
        * *vagrant halt*
7. 가상 머신에 SSH 연결
    * *vagrant ssh*
8. 로컬 DB tool 에서 homestead DB 연결
    * 이미 설정된 사용자 정보
        * root / secret
        * homestead / secret
    * host 명 : homestead IP (192.168.10.10)
      
    