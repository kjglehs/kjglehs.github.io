---
title: '[Kotlin] 컬렉션 함수'
layout: post
categories: kotlin
---

```kotlin
data class Person(val name: String, val age: Int)
val people = listOf(Person("kjg", 11), Person("leh", 22))
```

### all
> 모든 원소가 조건을 만족

```kotlin
people.all { it.age <= 11}
>>> false
```

### any
> 하나라도 만족 

```kotlin
people.any { it.age <= 11}
>>> true
```

### find
- 조건을 만족하는 첫 번째 원소 반환, 없으면 null 을 반환
- firstOrNull 과 동일

```kotlin
people.find {it.age <= 11}
>>> Person(name="kjg", age=11)
```

### groupBy
> 컬렉션을 특성에 따라 그룹으로 분리

```kotlin
var poople = listOf(Person("kjg", 11), Person("leh", 22), Person("kjo", 11))
people.groupBy { it.age }
```

### flatMap
> 람다의 결과로 얻어지는 리스트를 하나의 리스트에 모은다.

```kotlin
people.flatMap { it.name.toList()}
```

### flatten
> flatMap 과 같으나 return 할 내용이 없을때

### asSequence
> 함수 연쇄 호출 시 성능 향상

```kotlin
people.map(People::name).filter { it.startWith("A") }
```
- map의 결과를 임시 list 에 저장하고 filter 의 결과를 최종 list 에 저장한다

- asSequense 사용하면 중간 결과를 저장하는 컬렉션이 생기지 않는다.
```kotlin
people.asSequnce().map(Person::name).filter { it.startWith("A") }.toList()
```

