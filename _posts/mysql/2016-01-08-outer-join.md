---
title: '[MySql] Join'
layout: post
categories: mysql
---

### OUTER JOIN 
- LEFT OUTER JOIN = LEFT JOIN

#### 정상적인 사용법
- mgr.dept_no = 'd001' 만 join 을 한다.

```mysql
SELECT * FROM employees e 
LEFT JOIN dept_manager mgr ON mgr.emp_no = e.emp_no AND mgr.dept_no = 'd001';
```

#### 잘못된 사용법
- mgr.dept_no = 'd001' 만 결과를 가져온다
- 결국 INNER JOIN 을 한것과 같다

```mysql
SELECT * FROM employees e 
LEFT JOIN dept_manager mgr ON mgr.emp_no = e.emp_no 
WHERE mgr.dept_no = 'd001';
```
```mysql
SELECT * FROM employees e 
INNER JOIN dept_manager mgr ON mgr.emp_no = e.emp_no 
WHERE mgr.dept_no = 'd001';
```
