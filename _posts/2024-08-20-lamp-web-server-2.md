---
title: "[3주차 TIL] KnockOn Bootcamp - 게시판 만들기(2) - 초기 설정 및 메인 화면"
published: true
---

|

# 초기 설정 파일 생성

파일에서는 init.php만 require할 수 있도록 초기 파일들 생성 후 require

```php
// init.php

require_once 'config.php';

require_once 'db.php';

require_once 'functions.php';
```

> require:

> require_once:

> include:

> include_once

|

---

|

## MySQL 연결

config.php파일에서 DB 설정

```php
// config.php

define('DB_SERVER', 'your_servername');
define('DB_USERNAME', 'your_username');
define('DB_PASSWORD', 'your_password');
define('DB_NAME', 'your_dbname');
```

|

db.php에서 MySQL 연결

```php
// db.php

// MySQL 연결
$mysqli = new mysqli(DB_SERVER, DB_USERNAME, DB_PASSWORD, DB_NAME);

// 연결 확인
if ($mysqli->connect_error) {
    die("Connecion failed: " . $mysqli->connection_error);
}
```

|

index.php에서 init.php파일 require

```php
// index.php

require_once 'init.php' 

// 추가 코드...
```

|

---

|

# 메인 페이지 - index.php

```php
// config.php

define('POST_PER_PAGE', 7); // 한 페이지에 표시할 게시물 수
define('MAX_LENGTH', 100); // 미리보기 내용
```

|

functions.php파일에 다음 함수 추가

**`getTotalPosts()`**: 총 게시물 수를 계산

**`getPosts()`**: 모든 게시물 가져오기

**`truncateContent()`**: 게시물 내용(content) 미리보기

|

```php
// functions.php

function getTotalPosts($mysqli, $query) {
    if ($query) {
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

> 


|

```php
// functions.php

function getPosts($mysqli, $offset, $post_per_page, $query) {
    if ($query) {
        $stmt = $mysqli->prepare("SELECT id, title, content, created_at, updated_at FROM posts WHERE title LIKE ? OR content LIKE ? ORDER BY created_at DESC LIMIT ?, ?");
        $search_term = '%' . $query . '%';
        $stmt->bind_param("ssii", $search_term, $search_term, $offset, $post_per_page);
    } else {
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

|

```php
// functions.php

// 게시물 내용 미리보기
function truncateContent($content, $maxLength = MAX_LENGTH) {
    return strlen($content) > $maxLength ? substr($content, 0, $maxLength) . '...' : $content;
}
```

|

```php
require_once 'init.php';

$post_per_page = POST_PER_PAGE; // config.php파일에서 지정한 페이지 수

// 현재 페이지
$page = isset($_GET['page']) ? intval($_GET['page']) : 1; // 페이지 기본값 1
$page = max(1, $page); // 페이지가 1보다 작은 경우 1로 설정
$offset = ($page - 1) * $post_per_page; // 몇 개의 게시물을 스킵할지 결정. ex)2페이지면 1*7 까지 스킵 후 8번째 게시물부터 보여줌

// 총 게시물 수 계산
$total_posts = getTotalPosts($mysqli, NULL);

// 총 페이지 수 계산
$total_pages = ceil($total_posts / $post_per_page);

// 게시물 가져오기
$result = getPosts($mysqli, $offset, $post_per_page, NULL);
$mysqli->close();
```

|

---

|

# 