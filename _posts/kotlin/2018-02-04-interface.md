---
title: '[Kotlin] Interface'
layout: post
categories: kotlin
---

### 사용법
- 일반 메소드는 무조건 구현
- 디폴트 구현이 있는 메소드는 선택 구현

```kotlin
interface Clickable {
    fun click() //일반 메소드 선언
    fun showOff() = println("I'm clickable!") //디폴트 구현이 있는 메소드
}
```
```kotlin
class Button: Clickable {
    override fun click() = println("I was clicked")
}
```

### 동일한 메소드를 포함한 두개의 인터페이스를 구현해야 하는 경우
- 중복되는 메소드를 무조건 구현해야 한다.

```kotlin
interface Focusable {
    fun showOff() = println("I'm focusable!")
}
```
```kotlin
class Button: Clickable, Focusable {
    override fun click() = println("I was clicked")
    //무조건 구현
    override fun showOff() {
        //원하는 상위 타입의 메소드 호출
        super<Clickable>.showOff()
    }
}
```

