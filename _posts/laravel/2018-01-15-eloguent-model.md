---
title: '[Laravel] 14. 엘로퀀트 ORM 모델링'
layout: post
categories: laravel
---

### 일대일 관계

```php
class User extends Model
{
    public function profile() {
        return $this->hasOne(Profile::class);
    }
}

class Profile extends Model
{
    public function user() {
        return $this->belongsTo(User::class, 'fk_user_id');
    }
}

$profile = User::find(1)->profile;
```


### 일대다 관계

```php
class Project extends Model
{
    public function tasks() {
        return $this->hasMany(Task::class);
    }
}

class Task extends Model
{
    public function project() {
        return $this->belongsTo(Project::class, 'project_fk_name');
    }
}

public function getOneToMany($id) {
    $tasks = Project::findOrFail($id)->tasks()->orderBy('id')->get();
}
```

### 다대다 관계

```php
class User extends Model
{
    public function roles() {
        return $this->belongsToMany(Role::class);
    }
}

class Role extends Model
{
    public function users() {
        return $this->belongsToMany(User::class);
    }
}

class RoleUser extends Model
{
    protected $table = 'role_user';
}

public function getManyToMany($id) {
    $users = Role::findOrFail($id)->users()->get();
}
```