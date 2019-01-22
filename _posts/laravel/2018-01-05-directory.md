---
title: '[Laravel] 5. 디렉토리 구성'
layout: post
categories: laravel
---

* app
    * 애플리케이션 소스 파일
    * 라우트 설정, 모델, 컨트롤러
* bootstrap
    * 부팅에 필요한 파일
    * 속도 향상을 위해 컴파일된 php 파일
* config
    * 애플리케이션 설정 파일
* database
    * migration : 데이터베이스 스키마 관리
    * seed data : 초기 데이터 설정
    * factory : 모델에 데이터 입력
* public 
    * 정적 리소스
    * index.php
* resources 
    * less : css 전처리기
    * 자바스크립트 프레임워크에서 사용하는 리소스
    * 뷰 코드
    * 언어별 메시지 파일
* storage
    * **웹서버나 php-fpm 이 이 폴더를 쓸수 있도록 권한 설정되어야 함**
        * *sudo chown -R www-data:www-data*
    * 컴파일된 템플릿 파일
    * 캐시 데이터
    * 로그 파일
* tests
    * PHPUnit 으로 테스트 할 경우 
* vendor
    * 의존성 있는 외부 라이브러리
    * 일반적으로 CVS 에 추가하지 않고 컴포저를 통해 관리
    