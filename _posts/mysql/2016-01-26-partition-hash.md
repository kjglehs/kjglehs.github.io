---
title: '[MySql] 해신 파티션'
layout: post
categories: mysql
---

### 해시 파티션
- 레인지 파티션이나 리스트 파티션으로 데이터를 균등하게 나누는게 어려울 때
- 테이블의 모든 레코드가 비슷한 사용 빈도를 보이지만 테이블의 크기가 너무 클 때

#### 파티션 생성

```mysql
CREATE TABLE employees (
  id INT NOT NULL
)
PARTITION BY HASH (id)
PARTITIONS 3 (
  PARTITION p0 ENGINE = INNODB,
  PARTITION p1 ENGINE = INNODB,
  PARTITION p2 ENGINE = INNODB
);
```

#### 파티션 추가, 분리, 병합
- 대상 테이블의 모든 파티션에 저장된 레코드를 재분배하는 작업이 필요 => 많은 부하가 발생한다.

#### 파티션 추가

```mysql
ALTER TABLE clients ADD PARTITION (PARTITION p4 ENGINE = INNODB);
```

#### 파티션 삭제
- 방법 없음

#### 파티션 분할
- 방법 없음

#### 파티션 병합
- 방법 없음