---
title: pre.Web(1주차)-Cookie & Session-Challenge
published: true
---

# 네이버 접속 시 사용되는 쿠키들 확인해보기

## 1. 크롬 브라우저에 ID와 PW가 이미 기억되어 있는 상황

1-1. 네이버 접속 시 다음과 같은 쿠키가 생성됨

```
BUC
NAC
NACT
NM_srt_chzzk
NNB
PM_CK_loc
```

|

1-2. 로그인 버튼을 클릭(로그인 화면)

```
BUC
NAC
NACT
NNB
nid_buk
nid_slevel
```

| - NM_srt_chzzk
| - PM_CK_loc
| + nid_buk
| + nid_slevel

|

1-3. 아이디와 비밀번호 입력 후 로그인 버튼을 클릭(네이버 홈)

```
BUC
NAC
NACT
NID_AUT
NID_JKL
NID_SES
NM_srt_chzzk
NNB
PM_CK_loc
nid_buk
nid_inf
nid_slevel
```

| + NM_srt_chzzk
| + PM_CK_loc
| + NID_AUT
| + NID_JKL
| + NID_SES
| + nid_inf

|

1-3-1. 사용자 등록 페이지가 뜬 경우

```
BUC
NAC
NACT
NID_AUT
NID_JKL
NID_SES
NNB
nid_buk
nid_slevel
```

| + NID_AUT
| + NID_JKL
| + NID_SES
| + nid_inf 만 생기고

1-3-2. 등록 버튼을 클릭(네이버 홈)

```
BUC
NAC
NACT
NID_AUT
NID_JKL
NID_SES
NNB
nid_buk
nid_sl
```

| + NM_srt_chzzk
| + PM_CK_loc


## 2. 크롬 게스트 모드로 접속하여 ID와 PW를 처음 입력하는 상황

2-1. 네이버 접속 시 다음과 같은 쿠키가 생성됨

```
BUC
NAC
NACT
NNB
PM_CK_loc
```

|

2-2. 로그인 버튼 클릭 시

```
BUC
NAC
NACT
NNB
nid_slevel
```

| - PM_CK_loc
| + nid_slevel

|

2-3. 로그인 시 (사용자 등록 화면)

```
BUC
NAC
NACT
NID_AUT
NID_JKL
NID_SES
NNB
nid_inf
nid_slevel
```

| + NID_AUT
| + NID_JKL
| + NID_SES
| + nid_inf

|

2-4. 등록 버튼 클릭 시(네이버 홈)

(등록 안함 눌러도 똑같음)

```
BUC
NAC
NACT
NID_AUT
NID_JKL
NID_SES
NM_srt_chzzk
NNB
PM_CK_loc
nid_inf
nid_slevel
```

| + NM_srt_chzzk
| + PM_CK_loc

|

# 위에서 얻은 쿠키를 변조한 후 결과 분석하기

로그인 후, 네이버 검색창을 클릭하면

![naver 검색창](./assets/images/naver(2).png)  
```
_naver_usersession_
```
이 추가됨

**`분석`**

사용자의 검색 기록을 기억함

|

![naver 프로필](./assets/images/naver(1).png)  

메일, 카페, 블로그 등을 클릭하면

```
JSESSIONID
```
가 추가됨

**`분석`**

세션 유지를 통해 로그인 상태를 유지한 채로 메일, 카페, 블로그 등의 페이지로 이동할 수 있게 해줌

|

---

|