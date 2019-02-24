---
title: '[MySql] 시스템 변수'
layout: post
categories: mysql
---

### 조회
- GLOBAL 이나 SESSION 을 명시하지 않으면 현재 커넥션의 변수 목록을 표시

```mysql
SHOW GLOBAL VARIABLES ;
SHOW GLOBAL VARIABLES LIKE '%connections%';
SHOW SESSION VARIABLES LIKE '%timeout%';
SHOW VARIABLES LIKE '%timeout%';
```

### 변경

```mysql
SET GLOBAL max_connections = 500;
SET wait_timeout = 100;
```

