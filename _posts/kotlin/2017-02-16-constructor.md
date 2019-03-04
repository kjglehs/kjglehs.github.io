---
title: '[Kotlin] 생성자'
layout: post
categories: kotlin
---

### 생성자
> 객체가 생성될 때 호출되는 함수

### 주 생성자
- 하나의 클래스에 하나만 정의 가능
- 클래스 몸체가 아닌 헤더에서 클래스 이름 뒤에 선언

```kotlin
//별도의 생성자가 없다면 컴파일러가 자동으로 매개변수가 없는 주 생성자를 추가한다.
class MyClass1 {}

class MyClass2() {}

class MyClass3 contructor() {}
```

### 매개변수가 있는 주 생성자
```kotlin
class User1 constructor(name: String, age: Int) {}

class User2(name: String, age: Int) {}

val user1 = User1() //에러
val user2 = User1("kkang", 33)
val user3 = User2("kim", 28)
```

### 생성자 매개변수 기본값 명시
```kotlin
class User3(name: String, age: Int = 0) {}

val user4 = User3("kkang")
```

### 생성자 초기화 블록 init
> 클래스의 생성자에 매개변수 이외에 실행문을 작성할 때 사용
```kotlin
class User(name: String, age: Int) {} {} //에러
```
```kotlin
class User(name: String, age: Int) {
    init {
        println("i am init...")
    }
}
```

### 생성자 매개변수 값 이용
- 기본적으로 생성자의 매개 변수는 클래스의 멤버 함수에서는 사용할 수 없다.

```kotlin
class User(name: String, age: Int) {
    //init에서 사용
    init {
        println("i am init...my name is $name")
    }
    //프로퍼티에서 사용
    val upperName = name.toUpperCase()
    
    //멤버 함수에서 사용하면 에러
    fun sayHello() {
        println("hello $name")
    }
    
}
```

### 멤버 함수에서 생성자의 매개변수 사용하기 1
- 생성자의 매개변수를 클래스 프로퍼티에 대입하고 함수에서는 프로퍼티를 이용하는 방법

```kotlin
class User(name: String, age: Int) {
    val name = name
    fun sayHello() {
        println("hello $name")
    }
}
```

### 멤버 함수에서 생성자의 매개변수 사용하기 2
- 생성자 내에서 val, var를 이용해 매개변수를 선언하는 방법

```kotlin
class User(val name: String, val age: Int) {
    val myName = name
    fun sayHello() {
        println("hello $name")
    }
}
```

### 생성자의 매개변수명과 클래스의 프로퍼티명이 같으면..
- 적용되는 곳이 다르므로 주의

```kotlin
class User(name: String, age: Int) {
    val name: String = "kim"
    init {
        println("init $name")
    }
    fun sayHello() {
        println("hello $name")
    }
}

val user = User("kkang", 33)
user.sayHello()
```

- 결과
```text
init kkang
hello kim
```