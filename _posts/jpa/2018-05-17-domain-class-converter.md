---
title: '[Jpa] 17. DomainClassConverter'
layout: post
categories: jpa
---

```java
@Entity
public class Post {

    @Id @GeneratedValue
    private Long id;

    private String title;

    @Temporal(TemporalType.TIMESTAMP)
    private Date createdAt;
}
```

```java
public interface PostRepository extends JpaRepository<Post, Long> {
}
```

```java
@RestController
public class PostController {

    @Autowired PostRepository postRepository;

    @GetMapping("/posts/{id}")
    public String getPost(@PathVariable Long id) {
        Optional<Post> byId = postRepository.findById(id);
        Post post = byId.get();
        return post.getTitle();
    }

    //DomainClassConverter
    @GetMapping("/posts2/{id}")
    public String getPostByDomainClassConverter(@PathVariable("id") Post post) {
        return post.getTitle();
    }
}
```

```java
@RunWith(SpringRunner.class)
@SpringBootTest
@AutoConfigureMockMvc
public class PostControllerTest {

    @Autowired
    MockMvc mockMvc;

    @Autowired
    PostRepository postRepository;

    @Test
    public void getPost() throws Exception {
        Post post = new Post();
        post.setTitle("jpa");
        postRepository.save(post);

        mockMvc.perform(get("/posts/1"))
                .andExpect(status().isOk())
                .andExpect(content().string("jpa"));

        mockMvc.perform(get("/posts2/1"))
                .andExpect(status().isOk())
                .andExpect(content().string("jpa"));
    }
}
```