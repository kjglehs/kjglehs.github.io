---
title: '[MySql] 레인지 파티션'
layout: post
categories: mysql
---

### 파티션의 종류
- 레인지 파티션
- 리스트 파티션
- 해시 파티션
- 키 파티션

### 레인지 파티션
- 날짜 기간 데이터
- 범위 기반으로 데이터를 균등하게 나눌 수 있을 때\
- 파티션 키 위주로 검색이 자주 실행될 때

#### 권장 파티션 키
- YEAR(date_column) 
- TO_DAYS(date_column) 
 
#### 파티션 생성
 
```mysql
CREATE TABLE employees (
  id INT NOT NULL,
  hired DATE NOT NULL,
  PRIMARY KEY (id)
)
PARTITION BY RANGE (year(hired)) (
  PARTITION p0 VALUES LESS THAN (1991) ENGINE=InnoDB,
  PARTITION p1 VALUES LESS THAN (1996) ENGINE=InnoDB,
  PARTITION p2 VALUES LESS THAN (2001) ENGINE=InnoDB,
  PARTITION p3 VALUES LESS THAN MAXVALUE ENGINE=InnoDB 
);
```

- p0 : 입사 년도가  1990년 이하
- p1 : 입사 년도가 1991년 이상 1995년 이하
- p3 : 입사 년도가 1996년 이상 2000년 이하
- p3: 입사 년도가 2001년 이상

#### 파티션 추가

```mysql
ALTER TABLE employees ADD PARTITION ( PARTITION p3 VALUES LESS THAN (2001));
```

- maxvalue 파티션이 이미 정의되어 있을 경우에는 새로운 파티션을 추가할 수 없다.
- 이 때는 maxvalue 파티션을 분리하는 방법을 사용한다.

#### 파티션 삭제
- 아주 빠르게 처리되므로 오래된 데이터를 삭제하는 용도로 자주 사용

```mysql
ALTER TABLE employees DROP PARTITION p0;
```

#### 파티션 분리
- 기존의 값들은 파티션 분리에 따라 자동으로 재배치된다.

```mysql
ALTER TABLE employees
REORGANIZE PARTITION p3 INTO (
  PARTITION p3 VALUES LESS THAN (2012),
  PARTITION p4 VALUES LESS THAN MAXVALUE 
);
```

#### 파티션 병합

```mysql
ALTER TABLE employees 
    REORGANIZE PARTITION p2, p3 INTO (
    PARTITION p23 VALUES LESS THAN (2012)
    )

```