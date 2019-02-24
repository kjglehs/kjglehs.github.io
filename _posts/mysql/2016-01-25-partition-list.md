---
title: '[MySql] 리스트 파티션'
layout: post
categories: mysql
---

### 리스트 파티션
> 범위가 아니라 키 값 하나하나를 리스트로 나열

- 파티션 키 값이 코드값과 같이 고정적일 때
- 키 값이 연속되지 않고 정렬 순서와 관계없을 때
- 키 값을 기준으로 레코드의 건수가 균등할 때
- 검색 조건에 키 값이 자주 사용될 때

#### 파티션 생성

```mysql
CREATE TABLE product (
  id INT NOT NULL ,
  name VARCHAR(30),
  category_id INT NOT NULL 
)
PARTITION BY LIST (category_id) (
  PARTITION p1 VALUES IN (1),
  PARTITION p23 VALUES IN (2, 3)
)
```

### 파티션 분리 병합
- VALUES LESS THAN 이 아닌 VALUES IN 을 사용하는것 말고는 레인지 파티션과 동일