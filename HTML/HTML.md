- [HTML](#html)
  - [HTML 구조](#html-구조)
    - [시맨틱 태그](#시맨틱-태그)
  - [텍스트 입력하기](#텍스트-입력하기)
  - [목록 만들기](#목록-만들기)
  - [표 만들기](#표-만들기)
  - [이미지 삽입](#이미지-삽입)
  - [오디오, 비디오 삽입](#오디오-비디오-삽입)
  - [하이퍼링크 삽입](#하이퍼링크-삽입)
  - [입력 양식 작성](#입력-양식-작성)
    - [폼 삽입](#폼-삽입)
    - [폼 구역 나누기](#폼-구역-나누기)
    - [폼 요소에 레이블 붙이기](#폼-요소에-레이블-붙이기)
    - [input 태그](#input-태그)
    - [input 태그의 주요 속성](#input-태그의-주요-속성)
    - [폼에서 사용하는 여러 가지 태그](#폼에서-사용하는-여러-가지-태그)
# HTML

## HTML 구조

HTML은 보통 `<!DOCTYPE html>` 로 시작하여 `<html>`, `<head>`, `<body>` 세 영역으로 구성

Visual Studio Code에서 문서 모드를 HTML로 선택한 후, ! 입력하고 Tab 키를 누르면 아래와 같이 자동 입력됨

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    
</body>
</html>
```

`<!DOCTYPE html>`은 현재 문서가 HTML5 문서임을 명시

`<head>`: 웹 브라우저가 알아야 할 정보를 명시

- `<meta>`: 웹 문서 정보를 명시. 가장 중요한 역할은 어떤 인코딩을 사용할 것인지 명시하는 것.
- `<title>`: 웹 문서의 제목

`<body>`:웹 브라우저에 표시할 내용을 입력

### 시맨틱 태그

시맨틱 태그를 사용하는 이유
* HTML만 보고 제목, 내용 등을 쉽게 알 수 있음
* 문서 구조가 정확하게 나눠지므로  다양한 화면에서 웹 문서를 표현하기 쉬움
* 웹 사이트를 검색할 때 필요한 내용을 정확히 찾을 수 있음(예: 본문 내용을 검색해야 하는 경우 메뉴, 푸터 영역이 아닌 본문 내용만 검색)

주요 시맨틱 태그
* `<header>`: 주로 맨 위쪽이나 왼쪽에 있으며, 검색 창이나 사이트 메뉴를 삽입
* `<nav>`: 다른 위치로 연결하는 링크를 생성. 웹 문서의 위치에 영향을 받지 않으므로 헤더, 푸터, 또는 사이드 바 안에 포함시켜 사용하거나 독립해서 사용할 수 있음.
* `<main>`: 핵심 내용 삽입
* `<article>`: 웹 페이지 내용에 사용
* `<section>`: 웹 페이지 내용을 각각의 파트로 구분하기 위해 사용
* `<aside>`: 사이드바를 생성. 필수 요소는 아님
* `<footer>`: 맨 아래쪽에 푸터 영역을 생성. 사이트 정보, 저작권 정보, 연락처 등을 넣음
* `<div>`: id나 class 속성을 사용하여 문서 구조를 만들거나 스타일을 적용할 때 사용

## 텍스트 입력하기

* `<p>` 태그(paragraph)는 텍스트 앞뒤로 빈 줄이 생기면서 텍스트 단락 생성.
* `<br>`: 줄 바꿈.
* `<blockquote>`: 인용문 표시. 다른 텍스트보다 약간 들여 씀.
* `<strong>`: 중요한 내용을 강조. 단순히 글자를 굵게 표시할 때는 `<b>` 태그 사용.
* `<em>` 태그(emphasis)는 특정 부분을 강조하고 싶은 내용을 기울여 출력. 단순히 글자를 기울여 출력할 때는 `<i>` 태그(italic) 사용.

## 목록 만들기

* 순서 있는 목록(Ordered List)은 `<ol>` 태그와 `<li>` 태그(list) 사용
* 순서 있는 목록(Unorded List)은 `<ul>` 태그와 `<li>` 태그(list) 사용
* 설명 목록(Description List)은 이름과 값 형태로 구성된 목록

```html
<!-- 순서 있는 목록(Ordered List) -->
<!-- type 속성 종류: 1(숫자), a(영소문자), A(영대문자), i(로마 소문자), I(로마 대문자 -->
<ol type="a" start="3"> 
  <li>List 1</li>
  <li>List 2</li>
</ol>

<!-- 순서 없는 목록(Unordered List) -->
<ul> 
  <li>List 1</li>
  <li>List 2</li>
</li>

<!-- 설명 목록(Description List) -->
<dl>
  <dt>Name</dt>
  <dd>Value</dd>
</dl>
```

## 표 만들기

* 표는 `<table>` 태그로 생성.
* 표 제목은 `<caption>` 태그 사용.
* 표의 구조는 `<thead>`, `<tbody>`, `<tfoot>` 태그를 사용하며, 각각 제목, 본문, 요약 부분을 가리킴.
  - 표 열의 속성을 정의하려면 `<colgroup>` 및 `<col>` 태그를 사용하며, 표 전체 열 개수만큼 `<col>` 태그를 사용해야 함.
* 표의 행(table row)은 `<tr>` 태그로, 표의 열(table data)은 `<td>` 태그로 생성.
  - 행을 합치려면 `rowspan` 속성을, 열을 합치려면 `colspan` 속성을 사용

```html
<table border="1">
  <caption>상품 구성</caption>
  <colgroup>
    <col style="background-color: #eee;">
    <col>
    <col style="width: 150px;">
  </colgroup>
  <thead>
    <tr>
      <th>1열</th>
      <th>2열</th>
      <th>3열</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td rowspan="2">1행1열</td>
      <td>1행2열</td>
      <td>1행3열</td>
    </tr>
    <tr>
      <!-- rowspan에 의해 행 병합되었으므로 쓰지 않음 -->
      <td>2행2열</td>
      <td>2행3열</td>
    </tr>
    <tr>
      <td>3행1열</td>
      <td colspan="2">3행 2열ㅇㅇ</td>
      <!-- colspan에 의해 열 병항되었으므로 쓰지 않음 -->
    </tr>
    <tfoot>
      <tr>
        <td>tfoot</td>
        <td>tfoot</td>
        <td>tfoot</td>
      </tr>
    </tfoot>
  </tbody>
</table>
```

## 이미지 삽입

`<img>` 태그로 이미지 삽입.

```html
<!-- 
  - src: 이미지 경로
  - alt: 이미지를 표시할 수 없는 경우 대신 보여줄 텍스트
  - width 및 height: 이미지 가로 및 세로 길이. 단위는 픽셀(px) 또는 퍼센트(%)
-->
<img src="이미지_경로" alt="대체용_텍스트" width="가로길이" height="세로길이">
```

## 오디오, 비디오 삽입

* `<object>` 태그는 다양한 멀티미디어 파일을 삽입할 때 사용.
* `<embed>` 태그도 멀티미디어 파일을 삽입할 때 사용. 주로 `<object>`, `<audio>`, `<video>` 태그를 지원하지 않는 웹 브라우저를 고려할 때 사용.
* `<audio>` 태그는 오디오 파일 삽입에 사용. 대부분의 웹 브라우저에서 mp3 형식 지원.
* `<video>` 태그는 비디오 파일 삽입에 사용. 대부분의 웹 브라우저에서 mp4 형식 지원.

```html
<object data="데이터경로" width="가로길이" height="세로길이"></object>
<embed src="파일경로" width="가로길이" height="세로길이">

<!-- 
`<audio>` 및 `<video>` 태그에서 사용 가능한 속성
  * controls: 컨트롤 바 표시
  * autoplay: 자동 재생(대부분의 웹 브라우저에서 금지하는 속성)
  * loop: 반복 재생
  * preload: 어떻게 로딩할 지 설정. 사용할 수 있는 값은 auto, metadata, none.
  * poster=”파일경로": `<video>` 태그에서 사용하는 속성으로, 재생 전에 보여줄 포스터 이미지 지정
-->
<audio src="오디오파일_경로"></audio>
<video src="비디오파일_경로"></video>
```


## 하이퍼링크 삽입

* `<a>` 태그로 하이퍼링크 삽입.
* `<a>` 태그의 target 속성에 _blank를 지정하면 링크가 새 탭에서 열림.

```html
<a href="링크주소">텍스트 또는 이미지</a>
```


## 입력 양식 작성

### 폼 삽입

`<form>`과 `</form>` 태그 사이에 폼 요소를 넣어 폼 생성.

`<form>` 태그의 속성
* method: 폼 내용을 서버로 넘기는 방법 설정
  - get: 폼 내용을 주소 표시줄에 드러낸 채로 넘김. 데이터 크기 제한 있음.
  - post:  폼 내용을 주소 표시줄에 드러내지 않고 전송. 데이터 크기 제한 없음.
* name: 폼 이름
* action: 폼을 처리할 스크립트 이름 지정
* target: action 속성에서 지정한 스크립트를 다른 위치에서 열도록 지정
* autocomplete: 자동 완성 기능 설정. 기본 값은 on.

```html
<form method="post">
	<!-- 폼 요소 삽입 -->
</form>
```

### 폼 구역 나누기

폼 안에 여러 구역을 나눌 때 `<fieldset>` 태그 사용.

fieldset 태그로 묶은 그룹에 제목을 붙일 때 `<legend>` 태그 사용.

```html
<fieldset>
  <legend>Field Name</legend>
</fieldset>
```

### 폼 요소에 레이블 붙이기

폼 요소를 `<label>` 태그로 감싸거나

```html
<label>ID:<input type="text"></label>
```

폼 요소와 `<label>` 태그를 분리하여 사용하되, label 태그의 for 속성과 폼 요소의 id 속성을 동일하게 설정

```html
<label for="user_id">ID:</label>
<input type="text" id="user_id">
```

### input 태그

`<input>`: 사용자가 입력한 값을 받을 때 사용하며, 사용 가능한 type 속성 값은 다음과 같음.

| 종류           | 설명                                                    |
| -------------- | ------------------------------------------------------- |
| checkbox       | 2개 이상 선택 가능한 체크박스                           |
| date           | 날짜(년, 월, 일)                                        |
| datetime       | 날짜 및 시간(년, 월, 일, 시, 분, 초)                    |
| datetime-local | 사용자 지역 기준의 날짜 및 시간(년, 월, 일, 시, 분, 초) |
| email          | 이메일 주소                                             |
| file           | 파일                                                        |
| image          | submit 버튼 대신 사용할 이미지 추가                     |
| month          | 날짜(년, 월)                                            |
| number         | 숫자를 입력받는 스핀 박스                               |
| password       | 비밀번호                                                |
| radio          | 1개만 선택 가능한 라디오 버튼                           |
| range          | 숫자를 입력받는 슬라이드 막대                           |
| reset          | 초기화 버튼                                             |
| search         | 검색 필드                                               |
| submit         | 전송 버튼                                               |
| tel            | 전화번호                                                |
| text           | 한 줄 짜리 텍스트                                       |
| time           | 시간(시, 분, 초)                                        |
| url            | URL 주소                                                |
| week           | 날짜(년, 주)                                            |

checkbox 타입은 여러 개의 항목을, radio 타입은 한 개의 항목만 선택할 때 사용

```html
<!-- 
checkbox와 radio 타입에서 사용하는 속성
* value: 서버에 넘겨줄 값
* checked: 기본 체크 여부
-->
<label><input type="checkbox" value="1kg" checked>1kg</label>
<label><input type="checkbox" value="2kg">2kg</label>

<!-- 여러 개의 라디오 버튼 중 하나만 선택되도록 하려면 name 속성 값을 똑같이 설정해야 함 -->
<label><input type="radio" value="1kg" name="weight" checked>1kg</label>
<label><input type="radio" value="2kg" name="weight">2kg</label>
```

number 및 range 타입은 숫자를 입력받을 때 사용

```html
<!--
number 및 range 타입에서 사용하는 속성
* min: 최소값(기본: 0)
* max: 최대값(기본: 100)
* step: 숫자 간격(기본: 1)
* value: 초기값
-->
<input type="number" min="0" max="100" step="1" value="50">
<input type="range" min="0" max="100" step="1" value="10">
```

date, month, week 타입은 날짜를 입력받을 때 사용

time 타입은 시간을 입력받을 때,  datetime과 datetime-local 타입은 시간과 날짜를 입력받을 때 사용

```html
<!--
date 및 time 관련 타입에서 사용하는 속성
* min, max: 날짜나 시간 범위 설정
* step: 날짜 및 시 간격
* value: 초기값
-->
<input type="date" min="2022-01-01" max="2022-12-31" value="2022-07-17">
<input type="month">
<input type="week">

<input type="time" min="09:00" max="18:00" value="12:00">
<input type="datetime">
<input type="datetime-local">
```

submit 타입은 폼 정보를 서버로 전송, reset 타입은 폼에 입력한 정보를 초기화.

```html
<input type="submit" value="Submit">
<input type="reset" value="Reset">
```

image 타입은 이미지 버튼 생성.

```html
<input type="image" src="IMG_PATH" alt="ALT_TEXT">
```

button 타입은 주로 자바스크립트를 실행할 때 사용.

```html
<input type="button" value="notice" onclick="window.alert('NOTICE')">
```

file 타입은 폼에 파일을 첨부.

```html
<input type="file">
```

hidden 타입은 폼에는 보이지 않지만 폼과 함께 서버로 전송됨. 사용자에게 보여 줄 필요는 없지만 관리자가 알아야 할 정보를 명시할 때 사용.

```html
<input type="hidden" name="NAME" value="VALUE">
```

### input 태그의 주요 속성

autofocus 속성을 사용하면 페이지를 불러오자마자 해당 필드에 마우스 포인터 표시.

placeholder 속성은 힌트를 표시.

required 속성은 반드시 입력해야 함을 명시.

```html
<input type="text" placeholder="HINT" autofocus required">
```

### 폼에서 사용하는 여러 가지 태그

`<textarea>`: 여러 줄을 입력받음.

```html
<!-- cols 값은 영문자 수를 기준으로 함 -->
<textarea cols="50" rows="10">Textarea</textarea>
```

`<select>`: 드롭다운 목록을, `<option>`: 목록에 항목을 추가.

```html
<!-- 
select 태그에서 사용하는 속성
* size: 표시할 드롭다운 항목 개수
* multiple: 둘 이상의 항목을 선택할 때 사용

option 태그에서 사용하는 속성
* value: 서버로 넘겨줄 값
* selected: 기본적으로 선택해서 보여 줄 항목
-->
<select size="2" multiple>
  <option value="value1">Value 1</option>
  <option value="value2">Value 2</option>
  <option value="value3" selected>Value 3</option>
</select>
```

`<datalist>`: 데이터 목록을, `<option>`: 목록에 항목을 추가. `<input>` 태그와 함께 사용해야 함.

```html
<!-- input 태그의 list 속성 값과 datalist의 id 속성 값이 서로 같아야 함. -->
<input type="text" list="DATA_ID">
<datalist id="DATA_ID">
  <option value="value1">Value 1</option>
  <option value="value2">Value 2</option>
</datalist>
```

`<button>`: 폼을 전송하거나 리셋하는 버튼 생성.

```html
<button type="submit">전송</button>
<button type="reset">리셋</button>
<button type="button">버튼</button>
```