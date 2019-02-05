---
title: '[Jpa] 19. EntityGraph'
layout: post
categories: jpa
---

### EntityGraph
> 쿼리 메소드 마다 연관 관계의 Fetch 모드를 설정 할 수 있다.

```java
@Entity
@NamedEntityGraph(name = "Comment.post", attributeNodes = @NamedAttributeNode("post"))
public class Comment {

    @Id @GeneratedValue
    private Long id;

    private String comment;

    @ManyToOne(fetch = FetchType.LAZY)
    private Post post;
}
``` 
```java
public interface CommentRepository extends JpaRepository<Comment, Long> {
    @EntityGraph(value = "Comment.post", type = EntityGraph.EntityGraphType.FETCH)
    Optional<Comment> getById(Long id);
}
```
- type 설정
    - FETCH :  설정한 엔티티 애트리뷰트는 EAGER 패치 나머지는 LAZY
    - LOAD: 설정한 엔티티 애트리뷰트는 EAGER 패치 나머지는 기본 패치 전략
    
#### Entity 에 NamedEntityGraph 설정 없이 사용
```java
public interface CommentRepository extends JpaRepository<Comment, Long> {
    @EntityGraph(attributePaths = "post")
    Optional<Comment> getById(Long id);
}
```