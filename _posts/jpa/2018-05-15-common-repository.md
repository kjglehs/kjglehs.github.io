---
title: '[Jpa] 15. Common Repository'
layout: post
categories: jpa
---

### Common Repository
> 모든 리포지토리에 공통 기능 추가

1. JpaRepository 를 상속 받은 인터페이스 정의
    - @NoRepositoryBean
1. 기본구현체(SimpleJpaRepository)를 상속 받는 커스텀 구현체 만들기
1. @EnableRepositories 설정
    - repositoryBaseClass
    
```java
@NoRepositoryBean
public interface MyRepository<T, ID extends Serializable> extends JpaRepository<T, ID> {
    boolean contains(T entity);
}
```

```java
public class SimpleRepositoryBean<T, ID extends Serializable> extends SimpleJpaRepository<T, ID> implements MyRepsitory<T, ID> {
    
    private EntityManager entityManager;
    
    public SimpleRepository(JpaEntityInformation<T, ?> entityInformation, EntityManager entityManager) {
        super(entityInformation, entityManager);
        this.entityManager = entityManager;
    } 
    
    @Override
    public boolean contains(T entity) {
        return entityManager.contains(entity);
    }
}
```

```java
@EnableRepositories(repositoryBaseClass = SimpleMyRepository.class)
```

```java
public interface PostRepository extends MyRepository<Post, Long> {
}
```