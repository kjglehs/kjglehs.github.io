---
title: '[Jpa] 20. Projection'
layout: post
categories: jpa
---

### Projection
> 엔티티의 일부 데이터만 가져오기

```java
@Entity
public class Comment {

    @Id @GeneratedValue
    private Long id;

    private String comment;

    private int up;

    private int down;

    @ManyToOne(fetch = FetchType.LAZY)
    private Post post;
}
```

```java
public interface CommentSummary {

    String getComment();
    int getUp();
    int getDown();

    default String getVotes() {
        return getUp() + " " + getDown();
    }
}
```

```java
public interface CommentRepository extends JpaRepository<Comment, Long> {
    List<CommentSummary> findByPost_Id(Long id);
}
```

### Dynamic Projection
> Projection 이 여러개일 때 
프로젝션 용 메소드 하나만 정의하고 실제 프로젝션 타입은 타입 인자로 전달

```java
public interface CommentRepository extends JpaRepository<Comment, Long> {
    <T> List<T> findByPost_Id(Long id, Class<T> type);
}
```

```java
@Test
public void getComment() {
    commentRepository.findByPost_Id(1L, CommentSummary.class);
}
```