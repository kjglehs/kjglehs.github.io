---
title: '[Kotlin] with, apply'
layout: post
categories: kotlin
---

### with
> 객체의 이름을 반복하지 않고 연산을 수행

```kotlin
fun alphabet(): String {
    val result = StringBuilder()
    for (letter in 'A'..'Z') {
        result.append(letter)
    }
    result.append("\nNow I know the alphabet!")
    return result.toString()
}

println(alphabet())
>>> ABCDEFGHIJKLMNOPQRSTUVWXYZ
>>> Now I know the alphabet!
```
```kotlin
fun alphabet(): String {
    val stringBuilder = StringBuilder()
    return with(stringBuilder) {
        for (letter in 'A'..'Z') {
            this.append(letter)
        }
        append("\nNow I know the alphabet!")
        this.toString()
    }
}
```

### apply
> with 와 같은 기능 + 자기 자신에게 전달된 객체를 반환

```kotlin
fun alphabet() = StringBuilder.apply {
    for (letter in 'A'..'Z') {
        append(letter)
    }
    append("\nNow I know the alphabet!")
}.toString()
```
- 객체 초기화시 사용 가능

```kotlin
val poeple = People.apply {
    name = "kjg"
    age = 10
}
```