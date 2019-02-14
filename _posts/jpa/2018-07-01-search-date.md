---
title: '[Jpa] 날짜 검색'
layout: post
categories: jpa
---

### String -> Date나 TimeStamp로 변환 후 검색(joda time)
```java
DateTimeFormatter fmt = DateTimeFormat.forPattern("yyyy-MM-dd hh:mm:ss");
DateTime dt = fmt.parseDateTime("2016-08-01 23:32:22")
Timestamp ts = new Timestamp(dt.getMillis());

//datetime(joda) to date
Date date = dt.toDate()
```