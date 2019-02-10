---
title: '[Kotlin] data class'
layout: post
categories: kotlin
---

### data class
> equals(), hashcode(), toString() 를 자동으로 override 함  
copy() 메소드 구현

### 사용방법
```kotlin
data class Client(val name: String, val postCode: Int)
```

### equals()
> 객체의 동일성 체크

```kotlin
class Client(val name: String, val postCode: Int)
```
```kotlin
val client1 = Client("kjg", 111)
val client2 = Client("kjg", 111)
println(client1 == client2)
>>> false
```
- 결과값을 true 로 하고 싶으면 equals() 메소드를 오바라이드해야 함

```kotlin
class Client(val name: String, val postCode: Int) {
    override fun equals(other: Any?): Boolean {
        if(other == null || other !is Client) return false
        return name == other.name && postCode = other.postCode
    }
}
```

### hashCode()
- JVM 언어에서는 equals()가 true 를 반환하는 두 객체는 반드시 같은 hashCode()를 반환해야 함  
- 따라서 equals 를 오버라이드할 때  반드시 함께 오버라이드 해야 함  

```kotlin
val processed = hashSetOf(Client("kjg", 11))
println(processed.contains(Client("kjg", 11)))
>>> false
```

### copy()
```kotlin
val lee = Client("lee", 123)
lee.copy(postCode = 121)
```