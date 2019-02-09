---
title: '[Kotlin] Constructor'
layout: post
categories: kotlin
---

### 주 생성자
- 아래 세 선언은 모두 같음

```kotlin
class User(val name: String)
```
```kotlin
class User constructor(_name: String) {
    val name: String
    init {
        name = _name
    }
}
```
```kotlin
class User(_name: String) {
    val name = _name
}
```

### 부 생성자
```kotlin
open class View {
    constructor(ctc: Context) {
    
    }
    constructor(ctc: Context, attr: AttributeSet) {
        
    }
}
```

### this()
```kotlin
class MyButton {
    constructor(ctx: Context): this(ctx, MY_STYLE) {
    
    }
    
    constructor(ctx: Context, attr: AttributeSet) {
    
    }
}

```