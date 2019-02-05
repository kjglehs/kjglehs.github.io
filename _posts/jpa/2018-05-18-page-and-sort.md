---
title: '[Jpa] 18. paging and sort'
layout: post
categories: jpa
---

```java
@GetMapping("/posts")
public Page<Post> getPosts(Pageable pageable) {
    return postRepository.findAll(pageable);
}
```

```java
@Test
public void getPosts() throws Exception {
    Post post = new Post();
    post.setTitle("jpa");
    postRepository.save(post);

    mockMvc.perform(get("/posts")
                .param("page", "0")
                .param("size", "10")
                .param("sort", "id,desc"))
            .andDo(print())
            .andExpect(status().isOk());
}
```
- sort 의 value 에 띄어쓰기 들어가면 안됨