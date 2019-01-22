---
title: '[Laravel] 7. 데이터 바인딩'
layout: post
categories: laravel
---

### with() 메서드 이용
```php
Route::get('/', function() {
    return view('welcome')->with('name', 'foo');
});

Route::get('/', function() {
    return view('welcome')->with([
        'name' => 'foo',
        'greeting' => 'hello'
    ]);
});
```

### view() 함수 이용
```php
Route::get('/', function() {
    return view('welcome', [
        'name' => 'foo',
        'greeting' => 'hello'
    ]);
});
```