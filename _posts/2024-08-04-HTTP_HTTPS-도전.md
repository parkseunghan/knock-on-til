---
title: pre.Web(1주차)-HTTP, HTTPS-도전
published: true
---


# curl을 이용하여 HTTP요청 직접 보내보기

## 기본 옵션

**`-X`** 또는 **`--request <command>`**: HTTP 메서드 설정 (예: GET, POST, PUT, DELETE).

**`-H`** 또는 **`--header <header>`**: 특정 헤더를 추가하거나 변경.

-**`d`** 또는 **`--data <data>`**: POST 요청에 데이터 전송. @를 사용하여 파일에서 데이터를 읽을 수 있음.

**`-F`** 또는 **`--form <name=content>`**: multipart/form-data 형식으로 데이터 전송 (파일 업로드 등).

**`-o`** 또는 **`--output <file>`**: 응답 내용을 파일에 저장.

**`-O`** 또는 **`--remote-name`**: 원격 파일 이름을 사용하여 파일을 저장.

**`-u`** 또는 **`--user <user:password>`**: 서버 인증 (HTTP 기본 인증).

|

## 고급 옵션

**`-I`** 또는 **`--head`**: HTTP 헤더만 가져옴.

**`-L`** 또는 **`--location`**: 서버가 반환한 Location 헤더를 따라감 (리다이렉션 추적).

**`-k`** 또는 **`--insecure`**: SSL 인증서 검증을 비활성화 (보안상 위험함).

**`-s`** 또는 **`--silent`**: 진행률 및 오류 메시지를 숨김.

**`-v`** 또는 **`--verbose`**: 상세한 요청/응답 정보를 출력.

**`--limit-rate <speed>`**: 전송 속도를 제한 (예: 100K).

**`-e`** 또는 **`--referer <URL>`**: Referer 헤더 설정.

**`-A`** 또는 **`--user-agent <string>`**: User-Agent 헤더 설정.

**`-b`** 또는 **`--cookie <data>`**: 쿠키 데이터 전송.

**`-c`** 또는 **`--cookie-jar <file>`**: 쿠키를 파일에 저장.

**`--compressed`**: 압축된 응답을 허용

|

## 예

```sh
curl war.knock-on.org:10001
```

```js
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  1132  100  1132    0     0  18912      0 --:--:-- --:--:-- --:--:-- 19859<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
    <title>Response</title>
    <link href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css" rel="stylesheet">
</head>
<body>
    <div class="container mt-5">
        <div class="row">
            <div class="col-md-8 offset-md-2">
                <div class="card">
                    <div class="card-header bg-primary text-white">
                        <h1 class="h3 mb-0">HTTP Method err!!</h1>
                    </div>
                    <div class="card-body">
                        <h3 class="card-text">0. POST 요청으로 변경하세요!</h3>
                    </div>
                </div>
            </div>
        </div>
    </div>
    <script src="https://code.jquery.com/jquery-3.5.1.slim.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.5.4/dist/umd/popper.min.js"></script>
    <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/js/bootstrap.min.js"></script>
</body>
</html>
```

|

```sh
curl -X POST war.knock-on.org:10001
curl --request POST war.knock-on.org:10001
```

```js
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  1181  100  1181    0     0  41029      0 --:--:-- --:--:-- --:--:-- 45423<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
    <title>Response</title>
    <link href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css" rel="stylesheet">
</head>
<body>
    <div class="container mt-5">
        <div class="row">
            <div class="col-md-8 offset-md-2">
                <div class="card">
                    <div class="card-header bg-primary text-white">
                        <h1 class="h3 mb-0">Request err!!</h1>
                    </div>
                    <div class="card-body">
                        <h3 class="card-text">1. POST 요청의 &#39;request&#39; 파라미터를 &#39;get-flag&#39;로 설정하세요!</h3>
                    </div>
                </div>
            </div>
        </div>
    </div>
    <script src="https://code.jquery.com/jquery-3.5.1.slim.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.5.4/dist/umd/popper.min.js"></script>
    <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/js/bootstrap.min.js"></script>
</body>
</html>
```

|

```sh
curl -X POST war.knock-on.org:10001 -d "request=get-flag"
curl --request POST war.knock-on.org:10001 --data "request=get-flag"
```

```js
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  1164  100  1148  100    16  43612    607 --:--:-- --:--:-- --:--:-- 48500<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
    <title>Response</title>
    <link href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css" rel="stylesheet">
</head>
<body>
    <div class="container mt-5">
        <div class="row">
            <div class="col-md-8 offset-md-2">
                <div class="card">
                    <div class="card-header bg-primary text-white">
                        <h1 class="h3 mb-0">User err!!</h1>
                    </div>
                    <div class="card-body">
                        <h3 class="card-text">2. User-Agent 헤더를 &#39;bot&#39;으로 설정하세요!</h3>
                    </div>
                </div>
            </div>
        </div>
    </div>
    <script src="https://code.jquery.com/jquery-3.5.1.slim.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.5.4/dist/umd/popper.min.js"></script>
    <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/js/bootstrap.min.js"></script>
</body>
</html>
```

|

```sh
curl -X POST -H "User-Agent: bot" war.knock-on.org:10001 -d "request=get-flag"
curl --request POST --header "User-Agent: bot" war.knock-on.org:10001 --data "request=get-flag"
```

```js
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  1204  100  1188  100    16  12181    164 --:--:-- --:--:-- --:--:-- 12673<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
    <title>Response</title>
    <link href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css" rel="stylesheet">
</head>
<body>
    <div class="container mt-5">
        <div class="row">
            <div class="col-md-8 offset-md-2">
                <div class="card">
                    <div class="card-header bg-primary text-white">
                        <h1 class="h3 mb-0">API Key err!!</h1>
                    </div>
                    <div class="card-body">
                        <h3 class="card-text">3. API_KEY가 &#39;SUp3r_STr0000ng_k3y&#39;인 Cookie 헤더를 가지고 있어야만 합니다!</h3>
                    </div>
                </div>
            </div>
        </div>
    </div>
    <script src="https://code.jquery.com/jquery-3.5.1.slim.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.5.4/dist/umd/popper.min.js"></script>
    <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/js/bootstrap.min.js"></script>
</body>
</html>
```

|

```sh
curl -X POST -H "User-Agent: bot" -H "Cookie: API_KEY=SUp3r_STr0000ng_k3y" war.knock-on.org:10001 -d "request=get-flag"
curl --request POST --header "User-Agent: bot" --header "Cookie: API_KEY=SUp3r_STr0000ng_k3y" war.knock-on.org:10001 --data "request=get-flag"
```

```js
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  1144  100  1128  100    16  55836    792 --:--:-- --:--:-- --:--:-- 63555<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
    <title>Response</title>
    <link href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css" rel="stylesheet">
</head>
<body>
    <div class="container mt-5">
        <div class="row">
            <div class="col-md-8 offset-md-2">
                <div class="card">
                    <div class="card-header bg-primary text-white">
                        <h1 class="h3 mb-0">SUCCESS!!!!!</h1>
                    </div>
                    <div class="card-body">
                        <h3 class="card-text">K0{M4n1pul4t1ng_c00k13s_1s_qu1t3_3z!!}</h3>
                    </div>
                </div>
            </div>
        </div>
    </div>
    <script src="https://code.jquery.com/jquery-3.5.1.slim.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.5.4/dist/umd/popper.min.js"></script>
    <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/js/bootstrap.min.js"></script>
</body>
</html>
```

|

---

|

# 웹 브라우저 개발자 도구를 사용하여 웹 사이트의 HTTP 통신을 살펴보기


