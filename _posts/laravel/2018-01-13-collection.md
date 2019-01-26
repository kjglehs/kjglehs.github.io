---
title: '[Laravel] 13. 컬렉션'
layout: post
categories: laravel
---

**[https://laravel.kr/docs/5.7/collections](https://laravel.kr/docs/5.7/collections)**

### 기본 사용법
```php
namespace App\Http\Controllers;

use Illuminate\Http\Request;

class CollectionController extends Controller
{
    public function index() {
        $collection = collect([1, 'apple', '', 'banana', null, 3])
            ->map( function($name) {
                return strtoupper($name);
            })
            ->reject(function($name) {
                return is_numeric($name);
            })
            ->reject(function($name) {
                return empty($name);
            });

        dump($collection);
    }
}
```

### all()
* 모든 요소 반환
```php
collect([1,2,3])->all()
=> [1,2,3]
```

### chunk()
* 정해진 개수만큼 잘라서 새로운 컬렉션을 반환
```php
$col = collection([1,2,3,4,5,6,7]);
$chunks = $col->chunk(3);
$chunks->toArray()
=>
[
    [1,2,3],
    [4,5,6],
    [7]
]
```

* contains(), count(), max(), min(), sum(), implode(), filter(), list()  등 많은 메서들 제공함
 