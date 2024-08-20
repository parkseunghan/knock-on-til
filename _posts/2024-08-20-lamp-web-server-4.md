---
title: "[3주차 TIL] KnockOn Bootcamp - 게시판 만들기(4) - 검색 & Read/Delete"
published: true
---

|

# 게시물 검색: search.php

search.php에서는 index.php는 같은 함수를 재사용해서 쓰기 때문에 따로 추가하지 않아도 됨.

**`getTotalPosts()`**: 총 게시물 수를 계산

**`getPosts()`**: 모든 게시물 가져오기

**`truncateContent()`**: 게시물 내용(content) 미리보기

|

```php
// functions.php

function getTotalPosts($mysqli, $query) {
    if ($query) { // 이 부분
        $stmt = $mysqli->prepare("SELECT COUNT(*) FROM posts WHERE title LIKE ? OR content LIKE ?");
        $search_term = '%' . $query . '%';
        $stmt->bind_param("ss", $search_term, $search_term);
    } else { 
        $stmt = $mysqli->prepare("SELECT COUNT(*) FROM posts");
    }
    $stmt->execute();
    $stmt->bind_result($total_posts);
    $stmt->fetch();
    $stmt->close();
    
    return $total_posts;
}
```

> $query: 검색어

> title 또는 content에 검색어가 포함된 게시물의 수 계산

> $search_term: '%검색어%' 의 형식으로 문장에서 부분 일치하는 부분을 찾아냄

|

```php
// functions.php

function getPosts($mysqli, $offset, $post_per_page, $query) {
    if ($query) {
        $stmt = $mysqli->prepare("SELECT id, title, content, created_at, updated_at FROM posts WHERE title LIKE ? OR content LIKE ? ORDER BY created_at DESC LIMIT ?, ?");
        $search_term = '%' . $query . '%';
        $stmt->bind_param("ssii", $search_term, $search_term, $offset, $post_per_page);
    } else { // 이 부분
    $stmt = $mysqli->prepare("SELECT posts.id, posts.title, posts.content, posts.created_at, posts.updated_at, posts.file_path, users.username 
                               FROM posts 
                               LEFT JOIN users ON posts.user_id = users.id 
                               ORDER BY posts.created_at DESC 
                               LIMIT ?, ?");
    }

    $stmt->bind_param("ii", $offset, $post_per_page);
    $stmt->execute();
    $result = $stmt->get_result();
    $stmt->close();
    return $result;
}
```

> title 또는 content에 검색어가 포함된 게시물을 가져옴

> ORDER BY created_at DESC: 최신 게시물이 먼저 나오도록 내림차순 정렬(default는 ASC로, 오름차순)

> LIMIT ?, ?: 페이지네이션 적용 offset만큼의 게시물을 건너뛰고, post_per_page개의 레코드를 가져옴

|

```php
//functions.php

function truncateContent($content, $maxLength = MAX_LENGTH) {
    return strlen($content) > $maxLength ? substr($content, 0, $maxLength) . '...' : $content;
}
```

|

---

|

# 게시물 읽기: read_post.php



# 게시물 삭제: delete_post.php