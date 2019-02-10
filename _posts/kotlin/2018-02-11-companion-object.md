---
title: '[Kotlin] companion object'
layout: post
categories: kotlin
---

### companion object
> class 안에 정의된 일반 객체

```kotlin
class A {
    companion object {
        fun bar() {
        
        }
    }
}
```
```kotlin
A.bar()
```

### companion object 의 이름, interface 구현
```kotlin
interface JSONFactory<T> {
    fun fromJSON(jsonText: String): T
}

class Person(val name: String) {
    companion object Loader : JSONFactory<Person> {
        override fun fromJSON(jsonText: String): Person {
        
        }
    }
}
```

### java 에서 호출
```kotlin
class Key(val value: Int) { 
    companion object { 
        @JvmField val COMPARATOR: Comparator<Key> = compareBy<Key> { it.value } 
        @JvmStatic fun bar() {} 
    } 
}
```
```kotlin
Key.COMPARATOR
Key.bar()
```