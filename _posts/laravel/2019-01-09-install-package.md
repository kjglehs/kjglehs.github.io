---
title: 9. 패키지 설치
layout: post
categories: laravel
---

1. php 패키지 저장소
    * [http://packagist.org](http://packagist.org)
2. 컴포저로 패키지 설치
    * composer require 'intervention.image' '2.3.*'
3. 서비스 프로바이더 등록
    * config/app.php 의 providers 에 등록
4. 파사드 등록(패키지가 라라벨 파사드를 지원할 경우)
    * 정적 메서드를 호출하는 문법으로 사용할 수 있게 함
    * config/app.php 의 aliases 에 등록
    