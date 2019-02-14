---
title: '[Kotlin] Type System'
layout: post
categories: kotlin
---

### ?.
```kotlin
fun foo(s: String?) {
    s?.toUpperCase()
}
```
아래 식과 같음
```kotlin
fun foo(s: String?) {
    if(s != null) s.toUpperCase() else null
}
```

### ?:
- 좌항이 null 일때 값을 설정

```kotlin
fun foo(s: String?) {
    val t: String = s ?: ""
}
```

### as
- type cast

### as?
- as 는 지정한 타입으로 바꿀수 없으면 ClassCastException 이 발생함

```kotlin
class Person(val firstName: String, val lastName: String) {
    override fun equals(o: Any?): Boolean {
        val otherPerson = o as? Person ?: return false
        return otherPerson.firstName == firstName && otherPerson.lastName == lastName 
    }
}
```

### let
- null 이면 아무 일도 발생하지 않는다

```kotlin
fun sendEmailTo(email: String) {
    println("sending email to $email")
}
var email: String? = "kjg@gmail.com"
email?.let { sendEmailTo(it) }
>>> sending email to kjg@gamil.com

email = null
email?.let { sendEmailTo(it) }
>>> 아무 일도 발생하지 않는다.
```

### Any
> java 의 object 와 같은 최상위 타입

### Unit
> 
- java 의 void 와 같은 기능
- void 와 달리 Unit을 타입 인자로 쓸 수 있다.

### Nothing
> 이 함수는 결코 정상적으로 끝나지 않음을 표시

```kotlin
fun fail(massage: String): Nothing {
    throw IllegalStateException(mesage)
}
```