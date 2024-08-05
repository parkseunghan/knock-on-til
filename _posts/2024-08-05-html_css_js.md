---
title: "[1주차 TIL] KnockOn Bootcamp - HTML, CSS, Javascript"
published: true
---

|

# HTML, CSS, JS의 기본 개념, 용도, 사용방법, 관계 등등

## HTML (HyperText Markup Language)

웹 문서의 *뼈와 살*을 담당

웹 페이지의 구조와 콘텐츠를 정의

태그와 속성을 통해 구조화된 문서 작성 지원

|

## CSS (Cascading Style Sheets)

웹 문서의 *생김새* 지정

HTML 콘텐츠의 시각적 스타일 설정

웹 리소스들의 시각화 방법을 기재한 스타일 시트

글자 색, 모양, 배경 색, 이미지 크기, 위치 등 지정 가능

브라우저는 CSS를 참고하여 웹 문서를 시각화

|

## JS (JavaScript)

웹 문서의 *동작* 정의

HTML 콘텐츠에 동적인 기능

버튼 클릭 시 어떻게 반응할지, 데이터 입력 시 어디로 전송할지 등 구현

사용자 브라우저에서 실행됨 -> 클라이언트가 실행하는 코드 (Client-Side Script)

|

# 웹 페이지 제작에 필요한 기본적인 HTML 태그들

```html
<!DOCTYPE html>
<html lang="ko-KR">
<head>
    <title>Pack's Blog</title>
    <style>
        body { font-family: Arial, sans-serif; }
        h1 { color: navy; }
        p { line-height: 1.6; }
    </style>
</head>
<body>
    <h1>Welcome to Pack's Blog</h1>
    <p>This is a paragraph of text. Here is a <a href="https://www.naver.com">link</a>.</p>
    
    <h2>h2태그. 이미지</h2>
    <img src="image.jpg" alt="이미지 설명" width="300">
    
    <h2>List</h2>
    <ul>
        <li>First item</li>
        <li>Second item</li>
        <li>Third item</li>
    </ul>
    
    <h2>Table</h2>
    <table border="1">
        <thead>
            <tr>
                <th>Header 1</th>
                <th>Header 2</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>Data 1</td>
                <td>Data 2</td>
            </tr>
            <tr>
                <td>Data 3</td>
                <td>Data 4</td>
            </tr>
        </tbody>
    </table>
    
    <h2>Form</h2>
    <form action="/submit" method="post">
        <label for="name">Name:</label>
        <input type="text" id="name" name="name">
        <button type="submit">Submit</button>
    </form>
</body>
</html>
```

## 문서 구조 태그

**`<!DOCTYPE html>`**: 문서 형식을 정의

**`<html>`**: HTML 문서의 루트 요소

**`<head>`**: 메타데이터, 스타일, 링크, 스크립트 등을 포함

**`<title>`**: 브라우저 탭에 표시되는 문서 제목

**`<body>`**: 웹 페이지의 본문 콘텐츠를 포함

|

## 텍스트 관련 태그

**`<h1> ~ <h6>`**: *제목 태그*. <h1>이 가장 크고 중요함, <h6>이 가장 작음

**`<p>`**: *단락*

**`<a>`**: *하이퍼링크*. *href 속성*으로 링크할 URL을 지정

**`<span>`**: *인라인 요소*. 텍스트의 일부를 묶어 *스타일을 적용*할 때 사용

**`<strong>`**: *굵은* 텍스트

**`<em>`**: *이탤릭체* 텍스트

**`<br>`**: *줄 바꿈* 삽입

**`<hr>`**: *수평선* 삽입

|

## 목록 태그

**`<ul>`**: *순서 없는* 목록

**`<ol>`**: *순서 있는* 목록

**`<li>`**: *목록 항목*

|

## 이미지 및 멀티미디어 태그

**`<img>`**: *이미지*. *src 속성*으로 이미지 파일의 URL을 지정

**`<audio>`**: *오디오* 콘텐츠

**`<video>`**: *비디오* 콘텐츠

|

## 표 관련 태그

**`<table>`**: *표*

**`<tr>`**: 표의 *행*

**`<td>`**: 표의 *데이터*

**`<th>`**: 표의 *헤더 셀*

**`<thead>`**: 표의 *헤더* 부분을 그룹화

**`<tbody>`**: 표의 *본문* 부분을 그룹화

**`<tfoot>`**: 표의 *바닥글* 부분을 그룹화

|

## 폼 관련 태그

**`<form>`**: 폼

**`<input>`**: 사용자 입력을 받는 *입력 필드*

**`<textarea>`**: *여러 줄*의 텍스트 *입력 필드*

**`<button>`**: 클릭 가능한 *버튼*

**`<label>`**: 폼 요소의 라벨

**`<select>`**: 드롭다운 목록

**`<option>`**: 드롭다운 목록의 항목

|

# 스타일링을 위한 CSS의 기본적인 문법과 속성들

## 기본 문법

CSS는 *선택자(selector)*와 *선언(declaration)*으로 구성됨

선언은 *속성(property)*과 *값(value)*으로 이루어짐

|

```css
선택자 {
    속성: 값;
}
```

|

```css
body {
    background-color: powderblue;
}
h1 {
    color: blue;
}  
p {
    color: red;
}
```

> body 선택자의 배경 색상은 powderblue
> hi 선택자의 글자 색은 blue
> p 선택자의 글자 색은 red

|

## 선택자 (Selectors)

스타일을 적용할 HTML 요소를 지정

태그 선택자, 클래스 선택자, 아이디 선택자, 그룹 선택자, 자손 선택자, 자식 선택자, 형제 선택자, 일반 형제 선택자, 속성 선택자가 있음

|

**`태그 선택자 (Tag Selector)`**: *특정 태그*의 모든 요소를 선택

```css
body {
    background-color: powderblue;
}
p {
    color: red;
}
```

> body 태그와 p태그에 적용

|

```html
<body>바디 태그임</body>
<p>P 태그임</p>
```

> HTML에서 태그 선택자 적용 예
> 태그 자체에 적용됨

|

**`클래스 선택자 (Class Selector)`**: 특정 클래스에 속한 요소 선택. 클래스 *이름 앞에 점(.)*을 붙임

```css
.container {
    font-size: 20px;
    color: red;
}
```

> .container 클래스에 속한 모든 요소에 적용

|

```html
<p class=".container">이 P 태그는 ".container" 클래스임</p>
<div class=".container">이 div 태그도 ".container" 클래스</div>
```

> HTML에서 클래스 선택자 적용 예
> 해당 클래스를 지정한 태그에만 적용됨

|

**`아이디 선택자 (ID Selector)`**: 특정 아이디를 가진 요소에 스타일을 적용. 아이디 *이름 앞에 샵(#)*을 붙임. 아이디는 문서 내에서 유일함

```css
#header {
    background-color: yellow;
    padding: 10px;
}
```

> #header 아이디를 가진 모든 요소에 적용

|

```html
<h1 id="header">id가 header임</h1>
```

> HTML에서 아이디 선택자 적용 예
> 해당 아이디를 지정한 태그에만 적용됨

|

**`그룹 선택자 (Group Selector)`**: 여러 HTML 요소에 동일한 스타일 적용. *쉼표(,)*로 구분

```css
h1, h2, h3 {
    color: green;
}
```

> h1, h2, h3 태그에 적용

|

```html
<h1>h1 태그임</h1>
<h2>h2 태그임</h2>
<h3>h3 태그임</h3>
```

> HTML에서 그룹 선택자 적용 예
> 그룹으로 지정된 태그에 모두 적용됨

|

**`자손 선택자 (Descendant Selector)`**: 특정 요소의 모든 자손 요소에 스타일 적용. *공백*으로 구분

```css
div p {
    color: purple;
}
```

> div에 속한 p에 적용

|

```html
<div>
    <p>div의 자손 p. 적용됨</p>
    <span>div의 자손 span</span>
</div>
<p>div 밖에 있는 p. 적용 안됨</p>
```

> HTML에서 자손 선택자 적용 예
> 자손으로 지정된 태그에 모두 적용됨

|

**`자식 선택자 (Child Selector)`**: 특정 요소의 바로 아래 자식 요소에 스타일 적용. *(>) 기호*로 구분

```css
ul > li {
    list-style-type: square;
}
```

> ul 바로 아래에 있는 li에 적용

|

```html
<ul>
    <li>First item</li>
    <li>Second item
        <ul>
            <li>Sub item</li>
        </ul>
    </li>
</ul>
```

> HTML에서 자식 선택자 적용 예
> 바로 아래 자식 태그에 적용됨

|

**`형제 선택자 (Adjacent Sibling Selector)`**: 특정 요소의 바로 다음에 오는 형제 요소에 스타일 적용. *(+) 기호*로 구분

```css
h1 + p {
    margin-top: 0;
}
```

> h1바로 다음에 오는 p에만 적용

|

```html
<h1>Heading</h1>
<p>h1 바로 다음에 오는 p. 적용됨</p>
<p>두 번째 p. 적용 안됨</p>
```

> HTML에서 형제 선택자 적용 예
> 바로 다음에 오는 p태그에만 적용됨

|

**`일반 형제 선택자 (General Sibling Selector)`**: 특정 요소 뒤에 나오는 모든 형제 요소에 스타일 적용. *(~) 기호*로 구분

```css
h1 ~ p {
    color: teal;
}
```

> h1 다음에 오는 모든 p에 적용

|

```html
<h1>Heading</h1>
<p>첫 번째 p. 적용됨</p>
<p>두 번째 p. 적용됨</p>
```

> HTML에서 일반 형제 선택자 적용 예
> h1 다음에 오는 모든 p태그에 적용됨

|

**`속성 선택자 (Attribute Selector)`**: 특정 속성을 가진 HTML 요소에 스타일 적용

```css
a[href] {
    color: orange;
}
a[target="_blank"] {
    text-decoration: underline;
}
```

> 해당 태그에 있는 속성에 스타일을 적용함

|

```html
<a href="https://www.naver.com">a태그에 있는 href 속성에 적용됨</a>
<a target="_blank" href="https://www.naver.com">a태그에 있는 target="_blank" 속성과 href 속성에 적용됨</a>
<a>Link without href</a>
```

> HTML에서 속성 선택자 적용 예
> a태그 안에 있는 해당 속성에 적용됨

|

# 웹 페이지의 동적 기능을 위한 JS의 기본적인 문법과 함수들

