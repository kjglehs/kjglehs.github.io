---
title: '[Laravel] 11. 기본 컨트롤러와 라우트'
layout: post
categories: laravel
---

1. 생성
    * *php artisan make:controller TaskController*
    * *php artisan make:controller Admin/AdminController*
    
2. 생성된 위치 
    * app/http/controllers

3. example
    * HelloController
        ```php
        namespace App\Http\Controllers;
        
        use Illuminate\Http\Request;
        
        class HelloController extends Controller
        {
            public function index() {
                return view('hello')->with('name', 'kjg');
            }
        
            public function param($id = 1, $arg = 'kjg') {
                return ['id' => $id, 'arg' => $arg];
            }
        }
        ```
    * AdminController
        ```php
        namespace App\Http\Controllers\Admin;
        
        use Illuminate\Http\Request;
        use App\Http\Controllers\Controller;
        
        class AdminController extends Controller
        {
            public function index() {
                return view('admin.index');
            }
        }
        ```

4. 라우트 설정
```php
Route::get('hello', 'HelloController@index');
Route::get('hello/param/{id}/{arg?}', 'HelloController@param');
Route::get('admin', 'Admin\AdminController@index');
```

5. 뷰 생성
    * resources/views/hello.blade.php
    * resources/views/admin/index.blade.php

6. 암시적 컨트롤러
    * routes.php 파일 수정 없이 컨트롤러에 URL을 추가할 수 있는 컨트롤러
        ```php
        Route::controller('test', 'TestController')
        ```  
