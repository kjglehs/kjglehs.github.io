---
title: '[MySql] 최대 커넥션 설정'
layout: post
categories: mysql
---

```mysql
SHOW GLOBAL VARIABLES LIKE 'max_connections';
```

- 동적 변수라서 MySql 서버 재시작 없이 즉시 적용 됨
```mysql
SET GLOBAL max_connections  = 500
```
