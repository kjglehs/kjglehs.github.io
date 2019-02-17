---
title: '[MySql] Architecture'
layout: post
categories: mysql
---

### MySql 구조
> MySql 엔진 + 스토리지 엔진

- MySql 엔진 : 요청된 SQL 문장을 분석하거나 최적화하는 등 DBMS 의 두뇌에 해당하는 처리를 수행
- 스토리지 엔진 : 실제 데이터를 디스크 스토리지에 저장하거나 디스크 스토리지로부터 데이터를 읽어오는 부분을 전담