---
title: "[3주차 TIL] KnockOn Bootcamp - 게시판 만들기(1) - MySQL 데이터베이스"
published: true
---

# MySQL 데이터베이스 구축

## 데이터베이스 생성

```sql
CREATE DATABASE board;

use board;
```

|

## 테이블 생성

```sql
-- posts
CREATE TABLE `posts` (
  `id` int NOT NULL AUTO_INCREMENT,
  `title` varchar(255) NOT NULL,
  `content` text NOT NULL,
  `created_at` timestamp NULL DEFAULT CURRENT_TIMESTAMP,
  `file_path` varchar(255) DEFAULT NULL,
  `updated_at` timestamp NULL DEFAULT NULL ON UPDATE CURRENT_TIMESTAMP,
  `user_id` int NOT NULL,
  PRIMARY KEY (`id`)
)
```

> id: 게시물 식별 id
title: 게시물 제목
content: 게시물 내용

> created_at: 작성일

> updated_at: 수정일

|

```sql
--users
CREATE TABLE `users` (
  `id` int NOT NULL AUTO_INCREMENT,
  `username` varchar(50) NOT NULL,
  `nickname` varchar(50) NOT NULL,
  `password` varchar(255) NOT NULL,
  `created_at` timestamp NULL DEFAULT CURRENT_TIMESTAMP,
  `updated_at` timestamp NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
  PRIMARY KEY (`id`),
  UNIQUE KEY `username` (`username`)
)
```

|

## 유저 생성

```sql
-- testuser 생성
CREATE USER 'testuser'@'locathost' IDENTIFIED BY 'testuser';

-- 권한 부여 (택1)
-- 모든 권한 부여
GRANT ALL PRIVILEGES ON board.* TO 'testuser'@'localhost';

-- 특정 권한만 부여
GRANT SELECT, INSERT, UPDATE, DELETE ON board.* TO 'testuser'@'localhost';

-- 권한 적용
FLUSH PRIVILEGES;
```

|