---
title: '[Jpa] 21. Specification'
layout: post
categories: jpa
---

### Specification
> QueryDSL 과 비슷한 동적 쿼리 기능

- type safe

```xml
<dependency>
    <groupId>org.hibernate</groupId>
    <artifactId>hibernate-jpamodelgen</artifactId>
</dependency>
```

#### Intellij 설정
![intellij setting](/asset/image/jpa/2018052101.png)
- org.hibernate.jpamodelgen.JPAMetaModelEntityProcessor

```java
@Entity
public class Comment {

    @Id @GeneratedValue
    private Long id;

    private String comment;

    private int up;

    private int down;

    private boolean best;
}
```

```java
public interface CommentRepository extends JpaRepository<Comment, Long>, JpaSpecificationExecutor<Comment> {
}
```

```java
public class CommentSpecs {
    public static Specification<Comment> isBest() {
        return new Specification<Comment>() {
            @Override
            public Predicate toPredicate(Root<Comment> root,
                                         CriteriaQuery<?> criteriaQuery,
                                         CriteriaBuilder criteriaBuilder) {
                return criteriaBuilder.isTrue(root.get(Comment_.best));
            }
        };
    }
}
```

- 람다
```java
public class CommentSpecs {
    public static Specification<Comment> isBest() {
        return (root, criteriaQuery, criteriaBuilder) -> criteriaBuilder.isTrue(root.get(Comment_.best));
    }
}
```

```java
@Test
public void getComment() {
    commentRepository.findAll(CommentSpecs.isBest());
}
```