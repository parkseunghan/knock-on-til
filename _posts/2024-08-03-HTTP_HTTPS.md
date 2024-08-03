---
title: pre.Web(1주차)-HTTP, HTTPS
published: true
---
|

# HTTP (HyperText Transfer Protocol)

**웹**에서 데이터를 주고 받기 위한 프로토콜

*웹 브라우저 - 웹 서버* 간 데이터를 주고 받을 때 사용됨

요청-응답(request-response) 구조를 기반으로 작동  
> *클라이언트*(예: 웹 브라우저)가 *서버*에 *요청*을 보냄 -> *서버*는 *클라이언트*에 그에 대한 *응답*을 보냄

웹의 기본 프로토콜로서, 웹 페이지의 로드, 데이터 전송 및 다양한 웹 애플리케이션의 작동을 가능하게 하는 역할

|

## 특징

### `무상태 프로토콜 (Stateless Protocol)`

HTTP는 무상태 프로토콜  

각 요청은 *독립적*으로 처리되며, 이전 요청과 *연관성을 갖지 않음*  
-> 서버는 각 요청을 별도로 처리할 수 있음  

|

### `HTTP 메서드`

다양한 작업을 수행하기 위해 여러 메서드 제공  
(GET, POST, PUT, DELETE, PATCH, HEAD, OPTIONS 등)

|

**`GET`**: 서버로부터 데이터 요청 (예: 웹 페이지 로드)  

**`POST`**: 서버로 데이터 보냄 (예: 폼 제출)  

**`PUT`**: 서버에 데이터 업데이트  

**`DELETE`**: 서버에서 데이터 삭제  

**`PATCH`**: 서버에서 데이터를 부분적으로 업데이트  

**`HEAD`**: GET과 동일하지만, 응답 본문(body) 반환 X  

**`OPTIONS`**: 서버가 지원하는 메서드 확인  

|

### `HTTP 상태 코드`

서버는 클라이언트의 요청에 대한 응답으로 *상태 코드* 반환  

상태 코드: 요청의 성공 여부 및 기타 정보를 나타냄

|

**`200 OK`**: 요청이 성공적으로 처리됨

**`404 Not Found`**: 요청한 자원을 찾을 수 없음

**`500 Internal Server Error`**: 서버 내부 오류 발생

**`302 Found`**: 요청한 자원이 다른 URL로 이동됨

|

### 헤더

HTTP 요청/응답에는 *헤더(header)*가 포함되어 있어, 메타데이터(데이터에 대한 데이터)를 전송할 수 있음

헤더: 콘텐츠 유형, 길이, 인코딩 방식, 인증 정보 등의 다양한 정보 포함

|

### HTTPS (HyperText Transfer Protocol Secure)

HTTP의 보안 버전, 데이터를 암호화하여 전송

HTTPS는 SSL/TLS 프로토콜을 사용해 데이터의 무결성과 기밀성을 보장함

|

## 동작 과정

### 1. 클라이언트가 서버에 HTTP 요청을 보냄

웹 브라우저 주소 창에 URL 입력 

또는 링크 클릭

|

### 2. 서버가 요청을 처리하고 응답을 보냄

서버는 요청을 받아들임

해당 요청에 맞는 데이터를 준비하여 HTTP 응답을 클라이언트에 보냄

응답에는 상태 코드, 요청한 데이터(예: HTML 페이지)가 포함됨

|

### 3. 클라이언트가 응답을 받아 처리

클라이언트는 서버로부터 받은 응답을 처리하여, 사용자에게 필요한 정보를 표시함

|

--- 

|

# HTTP, HTTPS

HTTP와 HTTPS는 웹에서 데이터를 전송하기 위한 주요 프로토콜로, 주요 차이점은 보안성

|

## HTTP (HyperText Transfer Protocol)

HTTP는 데이터를 암호화하지 않고 전송하는 프로토콜

|

**`보안`**: HTTP는 암호화되지 않아 데이터가 전송되는 동안 *도청*이나 *중간자 공격(man-in-the-middle attack)*에 취약함

|

**`포트 번호`**: 80 포트 사용

|

**`사용 예`**: 보안이 중요하지 않은 일반적인 웹사이트에서 사용(뉴스 사이트, 블로그 등)

|

## HTTPS (HyperText Transfer Protocol Secure)

HTTP의 보안 버전

데이터 전송 시 *SSL(Secure Sockets Layer)*/*TLS(Transport Layer Security)* 프로토콜을 사용해 데이터를 암호화하여 *기밀성*과 *무결성*을 보장

|

**`보안`**

데이터를 암호화하여 전송하므로 도청, 중간자 공격 등에 대해 보호 제공

데이터의 기밀성을 보장

서버와 클라이언트 간 데이터 무결성 검증

|

**`포트 번호`**: 443 포트 사용

|

**`인증서`**

SSL/TLS 인증서를 사용해 서버의 신원 검증

인증서는 공인된 인증 기관(CA, Certificate Authority)에서 발급됨

|

**`사용 예`**

보안이 중요한 웹사이트에서 사용하여 사용자 데이터 보호(온라인 쇼핑몰, 은행 웹사이트, 이메일 서비스 등)

|

## 차이점 비교

|            | HTTP                     |  HTTPS                        |
|:-----------|:-------------------------|:------------------------------|
| 보안       | 암호화 X                  | SSL/TLS 사용, 데이터 암호화    |
| 포트 번호  | 80                        | 443                          |
| 인증       | 인증서 x                  | SSL/TLS 인증서 사용, 서버 인증 |
| 데이터 보호 | 데이터 전송 중, 도청 및 변조에 취약 | 데이터 전송 중, 도청 및 변조 방지 |
| URL       | http://                            | https://             |

|

---

|

# HTTP 헤더, 바디의 구조

HTTP 요청/응답 메시지는 크게 세 부분으로 구성됨  

시작줄(start line)

*헤더(header)*

*바디(body)*

|

## HTTP `요청(request)` 메시지 구조

### 1. 시작줄 (Start Line)

요청 메서드, 요청 대상(URI), HTTP 버전 포함

```js
GET /index.html HTTP/1.1
```

|

### 2. 헤더 (Headers)

요청에 대한 메타데이터 포함

각 헤더는 "name:value" 로 이루어져 있음

```js
Host: war.knock-on.org:10001
User-Agent: bot
Content-Type: application/x-www-form-urlencoded
Content-Length: 20
Cookie: A=a
```

|

### 3. 공백 줄 (Blank Line)

헤더와 바디를 구분하는 빈 줄

|

### 4. 바디(Body)

선택적으로 포함됨

주로 POST, PUT 등의 메서드에서 서버로 전송할 데이터를 포함

```js
request=get-flag
name=Pack&age=999
```

### 예

```js
POST / HTTP/1.1
Host: war.knock-on.org:10001
User-Agent: bot
Content-Type: application/x-www-form-urlencoded
Content-Length: 20
Cookie: API_KEY=h3ll0_Pack

request=get-flag
```

|

## HTTP `응답(response)` 메시지 구조

### 1. 상태줄 (Status Line)

HTTP 버전, 상태 코드, 상태 메시지 포함

```js
HTTP/1.1 200 OK
```

|

### 2. 헤더

응답에 대한 메타데이터 포함

```js
Content-Type: text/html; charset=UTF-8
Content-Length: 138
```

|

### 3. 공백 줄

헤더와 바디를 구분하는 빈 줄

|

### 4. 바디

요청에 대한 실제 응답 데이터 포함

```js
<html>
    <head>
        <title>Example</title>
    </head>
    <body>
        <h1>Hello, World!</h1>
    </body>
</html>
```

|

### 예

```js
HTTP/1.1 200 OK
Content-Type: text/html; charset=UTF-8
Content-Length: 138

<html>
    <head>
        <title>HTTP Response</title>
    </head>
    <body>
        <h1>Hello, World!</h1>
    </body>
</html>
```

|

## 헤더 종류

### **`일반 헤더 (General Headers)`**

요청 및 응답 모두에 적용

> Cache-Control, Connection, Date, Pragma, Trailer, Transfer-Encoding, Upgrade, Via, Warning

|

### **`요청 헤더 (Request Headers)`**

클라이언트가 서버로 보내는 요청에 대한 정보를 포함

> Accept, Accept-Charset, Accept-Encoding, Accept-Language, Authorization, Expect, From, Host, If-Match, If-Modified-Since, If-None-Match, If-Range, If-Unmodified-Since, Max-Forwards, Proxy-Authorization, Range, Referer, TE, User-Agent

|

### **`응답 헤더 (Response Headers)`**

서버가 클라이언트로 보내는 응답에 대한 정보를 포함

> Accept-Ranges, Age, ETag, Location, Proxy-Authenticate, Retry-After, Server, Vary, WWW-Authenticate

|

### **`엔터티 헤더 (Entity Headers)`**

요청 또는 응답의 본문에 대한 정보를 포함

> Allow, Content-Encoding, Content-Language, Content-Length, Content-Location, Content-MD5, Content-Range, Content-Type, Expires, Last-Modified

|

## 바디 내용

**`요청 바디`**: 주로 POST, PUT 등의 메서드에서 사용되며, 폼 데이터, JSON, XML 등의 형식으로 데이터를 포함할 수 있음

|

**`응답 바디`**: 서버가 클라이언트에게 보내는 실제 데이터로, HTML, JSON, XML, 이미지 등 다양한 형식이 될 수 있음

|

---

|

# HTTP method
# HTTP 상태코드
# SSL인증서