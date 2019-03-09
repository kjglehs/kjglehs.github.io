---
title: '[Git] .gitignore'
layout: post
categories: git
---

### .gitignore 파일 규칙
- 빈 라인이나, #으로 시작하는 라인은 무시
- 표준 Glob 패턴 사용
    - Glob 패턴 : 정규 표현식을 단순하게 만든 것
- 슬래시(/)로 시작하면 하위 디렉토리에는 적용되지 않는다.
- 디렉토리는 슬래시(/)를 끝에 사용하는 것으로 표현
- 느낌표로 시작하는 패턴의 파일은 무시하지 않는다.

### 예시
```ignore
# 확장자의 .a인 파일 무시
*.a

# 윗 라인에서 확장자가 .a인 파일은 무시하게 했지만 lib.a는 무시하지 않음
!lib.a

# 현재 디렉토리에 있는 TODO 파일은 무시하고 subdir/TODO 처럼 하위 디렉토리에 있는 파일은 무시하지 않음
/TODO

# build/ 디렉토리에 있는 모든 파일 무시
build/

# doc/notes.txt 파일은 무시하고 doc/server/arch.txt 파일은 무시하지 않음
doc/*.txt

# doc 디렉토리 아래의 모든 .pdf 파일 무시
doc/**/*.pdf

```