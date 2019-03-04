---
title: '[Kotlin] 보조 생성자'
layout: post
categories: kotlin
---

### 선언
> 
- 주 생성자 : 클래스 헤더에 선언
- 보조 생성자 : 클래스 몸체에 constructor로 선언
- 클래스를 선언할 때 최소한 하나 이상의 생성자를 정의해야 하는데,  
만약 보조 생성자를 선언했으면 주 생성자는 선언하지 않아도 된다.
- 주 생성자든 보조 생성자든 개발자가 생성자를 추가하면 컴파일러는 주 생성자를 자동으로 추가하지 않는다.

```kotlin
//보조 생성자 선언
class User {
    constructor(name: String) {}
}

val user = User() //에러
```

### 생성자 오버로딩
```kotlin
class User {
    constructor() {}
    constructor(name: String) {}
    constructor(name: String, age: Int) {}
}
```

### 보조 생성자의 매개변수 이용
 - 클래스 프로퍼티에 대입한 후 이용
 - 보조 생성자 매개변수에 var, val 선언 불가능
 
### 주 생성자와 보조 생성자를 함께 선언했을 때는 반드시 보조 생성자에서 주 생성자를 호출하는 구문을 작성해야 한다.
- 주 생성자를 선언했다면 객체 생성시 어떠한 경우라도 주 생성자는 실행되어야 한다.
- 객체 생성 시 보조 생성자를 이용했더라도 주 생성자는 반드시 실행되어야 한다.
- 따라서 주 생성자를 선언했다면 보조 생성자를 선언할 때 주 생성자 호출문을 생략할 수 없다.
- 보조 생성자에서 주 생성자 호출문은 this()를 이용한다.

- 에러
```kotlin
class User(name: String) {
    constructor(name: String, age: Int) {
    
    }
}
```
- 수정
```kotlin
class User(name: String) {
    constructor(name: String, age: Int): this(name) {
    
    }
}

fun main(args: Array<String>) {
    //주 생성자로 생성
    val user1 = User("kkang")
    //보조 생성자로 생성
    val user2 = User("kkang", 33)
}
```

- this() 예제

```kotlin
class User(name: String) {
    constructor(name: String, age: Int): this(name) {}
    constructor(name: String, age: Int, email: String): this(name, age) {}
}
```