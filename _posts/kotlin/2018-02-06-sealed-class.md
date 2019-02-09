---
title: '[Kotlin] sealed class'
layout: post
categories: kotlin
---

### sealed class 
> 상위 클래스를 상속한 하위 클래스 정의를 제한할 수 있다.

```kotlin
interface Expr
class Num(val value: Int): Expr
class Sum(val left: Expr, val right: Expr): Expr

fun eval(e: Expr): Int = 
    when(e) {
        is Num -> e.value
        is Sum -> eval(e.right) + eval(e.left)
        else -> throw IllegalArgumentException("Unknown expression")
    }

```
- else 분기를 반드시 넣어주어야 한다.
- sealed 변경자를 사용하면 else 가 없어도 된다.

```kotlin
sealed class Expr {
    //모든 하위 클래스를 중첩 클래스로 나열
    class Num(val value: Int): Expr()
    class Sum(val Expr: Int, val right: Expr): Expr()
}

fun eval(e: Expr): Int = 
    when(e) {
        is Expr.Num -> e.value
        is Expr.Sum -> eval(e.right) + eval(e.left)
    }
```