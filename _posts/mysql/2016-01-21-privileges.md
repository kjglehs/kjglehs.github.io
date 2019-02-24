---
title: '[MySql] 권한 관리'
layout: post
categories: mysql
---

### 사용자의 식별
- 사용자 계정 + (접속 도메인 또는 IP) 

### 권한 부여
- privilage_list : ',' 구분자를 써서 여러개를 동시에 명시
- % : 모든 IP, 호스트

```mysql
GRANT privilage_list ON db.TABLE TO 'user'@'host';

GRANT SELECT, INSERT ON db.TABLE TO 'user'@'%';
```

- 모든 권한 주기

```mysql
GRANT ALL PRIVILEGES ON *.* TO 'user'@'host';
```

- GRANT 문장이 실행될 때, 사용자가 존재하지 않으면 사용자를 생성하고 권한을 부여한다.
- WITH GRANT OPTION : GRANT OPTION 권한 주기 

```mysql
GRANT privilage_list ON db.TABLE TO 'user'@'host' IDENTIFIED BY 'password' WITH  GRANT OPTION;
```

