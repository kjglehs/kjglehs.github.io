---
title: '[Jpa] 4. Value 타입 맵핑'
layout: post
categories: jpa
---

### Composite Value 타입 맵핑
```java
@Entity
public class Account {
    
    @Id @GeneratedValue
    private long id;
    
    private String userName;
    
    @Embedded
    private Adderess address;
}

@Embaddable
public class Address {
    private String street;
    private String city;
}
```
* account 테이블에 street, city 칼럼도 생긴다.

### Composite Value 타입 맵핑 중복 처리
```java
@Entity
public class Account {
    
    @Id @GeneratedValue
    private long id;
    
    private String userName;
    
    @Embedded
    @AttributeOverrides({
            @AttributeOverride(name = "street", column = @Column(name = "home_street"))
        })
    private Adderess homeAddress;
    
    @Embedded
    @AttributeOverrides({
            @AttributeOverride(name = "street", column = @Column(name = "office_street"))
        })
        private Adderess officeAddress;
}
```