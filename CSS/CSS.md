# CSS
- [CSS](#css)
  - [CSS란?](#css란)
  - [스타일과 스타일 시트](#스타일과-스타일-시트)
  - [CSS 기본 선택자](#css-기본-선택자)
  - [스타일 적용 순위](#스타일-적용-순위)
  - [스타일 상속](#스타일-상속)
  - [글꼴 관련 스타일](#글꼴-관련-스타일)
  - [텍스트 관련 스타일](#텍스트-관련-스타일)
  - [목록 스타일](#목록-스타일)
  - [표 스타일](#표-스타일)
  - [박스 모델](#박스-모델)
    - [박스 모델의 주요 속성](#박스-모델의-주요-속성)
    - [테두리 스타일 지정](#테두리-스타일-지정)
    - [여백 설정](#여백-설정)
    - [웹 문서 레이아웃 만들기](#웹-문서-레이아웃-만들기)
    - [웹 요소의 위치 지정](#웹-요소의-위치-지정)
  - [배경 스타일](#배경-스타일)
  - [CSS 고급 선택자](#css-고급-선택자)
    - [연결 선택자](#연결-선택자)
    - [속성 선택자](#속성-선택자)
    - [가상 클래스 선택자](#가상-클래스-선택자)
    - [가상 요소](#가상-요소)
  - [애니메이션](#애니메이션)

## CSS란?

CSS는 Cascading Style Sheet. Cascading은 우선순위가 계단식(위에서 아래)으로 적용된다는 의미로 사용.

스타일을 사용하는 이유?
* 사이트 내용을 수정해도 디자인에 영향을 미치지 않기 위함
* 다양한 기기에 맞는 문서를 보여주기 위함(예: 반응형 웹)

여기서 설명하는 태그는 태그 그 자체, 요소는 태그로 감싸진 부분을 가리킴.

## 스타일과 스타일 시트

스타일 형식은 다음과 같음.

```css
/* 선택자는 스타일을 어느 태그에 적용할 것인지 알려주는 것 */
선택자 {
  속성: 속성값;
}

/* p 태그의 스타일 정의 */
p {
  text-align: center;
  color: blue;
}
```

스타일 시트는 스타일 규칙을 한 군데에 묶어놓은 것
* 브라우저 기본 스타일: CSS를 사용하지 않은 웹 문서에서 사용하는 스타일
* 인라인 스타일: 해당 태그에 style 속성을 사용하는 것

```html
<p style="text-align: center;"></p>
```

* 내부 스타일: HTML의 style 태그에 스타일을 작성하는 것

```html
<!DOCTYPE html>
<html lang="ko">
<head>
  <style>
    p {
      text-align: center;
    }
  </style>
</head>
</html>
```

* 외부 스타일: 스타일을 별도 파일로 저장해 놓고 사용

```html
<link rel="stylesheet" href="CSS_파일_경로">
```

## CSS 기본 선택자

* `*`: 전체 선택자. 스타일을 모든 문서 요소에 적용.

```css
/* 모든 문서 요소에 마진을 0으로 설정 */
* {
  margin: 0;
}
```

* 타입 선택자: 특정 태그를 사용한 모든 요소에 스타일을 적용

```css
/* p 태그를 사용한 모든 요소에 스타일을 적용 */
p {
  text-align: center;
}
```

* `.`: 클래스 선택자. 같은 태그라도 여러 요소에 스타일을 적용(예 header, content, footer, side-bar에 ID를 부여하여 고유하게 사용)

```css

/* class="p-center"인 태그에 스타일 적용 */
.p-center {
  text-align: center;
}
```

```html
<p class="p-center">center</p>
```

* `#`: ID 선택자. 하나의(고유한) 요소에만 스타일을 적용(예: 특정 컨텐츠를 반복하는 경우 클래스를 사용하여 같은 CSS를 적용)

```html

<style>
  <!-- id="centainer"인 태그에 스타일 적용 -->
  #container {
    width: 300px;
    border: 1px solid;
  }
</style>

<div id="container">
  <h1>CSS</h1>
  <p>Cascadeing Style Sheets</p>
</div>

```

* `,`: 는 여러 태그에 동일한 스타일 규칙을 지정할 때 사용.

```css
/* p, div 태그에 스타일 적용 */
p, div {
  text-align: center;
}
```

## 스타일 적용 순위
* 중요도: 사용자가 지정한 스타일 → 웹 문서를 제작한 제작자의 스타일 → 웹 브라우저가 기본으로 정해 놓은 스타일
* 적용범위순: !important → 인라인 스타일 → id 스타일 → class 스타일 → 타입 스타일
* 작성순: 나중에 작성한 스타일이 먼저 작성한 스타일을 덮어씀

## 스타일 상속

자식 요소의 스타일을 별도로 지정하지 않았다면 부모 요소의 스타일의 속성들이 자식 요소에 그대로 전달되는 것.

예를 들어, body 태그는 웹 문서에 사용한 모든 태그의 부모 요소임. body 태그의 스타일은 웹 문서 전체에 적용됨.

## 글꼴 관련 스타일

* `font-family`: 글꼴 속성

```css
font-family: "맑은 글꼴", 굴림
```

* `font-size`: 글자 크기 속성
  - 글자 크기 값에 사용 가능한 키워드는 xx-small, x-small, small, medkum, large, x-ragre, xx-large
  - 글자 크기 값에 사용 가능한 단위
    - 1em: 부모 요소 글꼴 대문자 M의 너비
    - 1rem: 문서 시작 부분(root)에서 지정한 크기
    - 1ex: 해당 글꼴의 소문자 x의 높이
    - 1px: 모니터의 1픽셀
    - 1pt: 일반 문서에서 주로 사용하는 단위

```css
선택자 { font-size: 상대크기 | 절대크기 | 크기 | 퍼센트 }
```

* `font-style`: 이텔릭체 표시 속성

```css
/* normal: 기본값 / italic 또는 oblique: 이탤릭체  */
font-style: normal | italic | oblique
```

* `font-weight` : 글자 굵기 속성
  * 예약어 lighter, normal, bold, bolder 또는 숫자값 100~900 사이 사용.
  * 숫자값 400은 normal, 700은 bold임

```css
font-weight: lighter | normal | bold | bolder | 100~900
```

## 텍스트 관련 스타일

* `color`: 텍스트 컬러 속성
  - 사용 가능한 값
    - 색상 이름: black, white, yellow 등
    - 16진수: #RRGGBB 형태로 빨간색, 초록색, 파란색의 양을 표시
    - RGBA: 빨간색, 초록색, 파란색 값을 0~255 사이값으로 입력. 불투명도는 0~1 사이값으로 입력
    - HSL 또는 HSLA: 색상, 채도, 명도, 불투명도를 입력

```css
color: 컬러_이름 | #RRGGBB | rgb(R, G, B) | rgba(R, G, B, A) | hsl(H, S, L) | hsla(H, S, L, A)
```

* `text-align`: 문단 정렬 속성
  - justify: 양쪽에 맞추어 문단 정렬.
  - match-parent: 부모 요소를 따라 문단 정렬.

```css

text-align: start | end | left | right | center | justify | match-parent
```

* `line-height`: 줄간격 속성

```css
/* 아래 속성은 모두 줄 간격이 24px */
line-height: 24px;
line-hgight: 2.0; 
line-height: 200%

/* 텍스트를 세로 정렬하려면 line-height 속성 값과 height 속성 값을 서로 똑같이 설정 */
.height-center {
  height: 100px;
  line-height: 100px;
}
```

* `text-decoration`: 텍스트 줄 긋기 속성

```css
/* 각각 기본값, 밑줄, 윗줄, 취소선 */
text-decoration: none | underline | overline | line-through;
```

* `text-shadow`: 텍스트 그림자 효과 속성

```css
text-shadow: none | WIDTH HEIGHT BLUR_RADIUS COLOR
```

* `text-transform`: 텍스트를 대문자 또는 전각문자로 변환하는 속성

```css
/* 각각 첫 글자를 대문자로 변환, 모든 글자를 대문자로 변환, 모든 글자를 소문자로 변환, 가능한 한 모든 문자를 전각 문자로 변환 */
text-transform: capitalize | uppercase | lowercase | full-width
```

* `letter-spacing` 글자 간격 조절 속성
* `word-spacing`: 단어 사이 간격 조절 속성

```css
letter-spacing: px | em | %
word-spacing: px | em | %
```


## 목록 스타일

* `list-style-type`: 목록 앞에 불릿 기호 또는 번호를 넣는 속성

```css
list-style-type: none | disc | circle | square | decimal | decimal-leading-zero | lower-roman | uppper-roman | lower-alpha | lower-latin | upper-alpha | upper-latin
```

* `lst-style-image`: 목록 앞에 이미지를 넣는 속성

```css
list-style-image: none | url('이미지_URL')
```

* `list-style-position`: 목록 앞에 불릿이나 번호를 넣는 속성

```css
list-style-position: inside | outside
```

* `list-style`: 위 속성들을 한 번에 사용하는 속성

```css
list-style: LIST_STYLE_TYPE LIST_STYLE_POSITION
```

## 표 스타일

* `caption-side`: 표 제목 위치 속성

```css
caption-side: top | bottom
```

* `border`: 표 테두리 속성

```css
/* 1픽셀 직선 블랙인 테두리 */
border: 1px solid black;
```

* `border-spacing`: 셀과 셀 사이 여백 속성

```css
border-spacing: 가로여백 | 세로여백
```

* `border-collapse`: 표와 셀 테두리를 합치는 속성

```css
border-collapse: separate(기본값) | collapse
```


## 박스 모델

* 박스 모델은 콘텐츠, 패딩(콘텐츠와 박스 영역 사이), 마진(박스 바깥 영역) 으로 구성. [http://www.tcpschool.com/css/css_boxmodel_boxmodel](http://www.tcpschool.com/css/css_boxmodel_boxmodel) 참고.
* 블록 레벨 요소는 한 줄을 차지하는 태그(h, div, p 등).
* 인라인 레벨 요소는 한 줄을 차지하지 않고 요소 크기만큼 차지하는 태그(span, img, strong 등).

### 박스 모델의 주요 속성

* `width` 및 `height`: 콘텐츠 영역 크기를 지정하는 속성

```css
width: PX | EM | % | auto;
height: PX | EM | % | auto;
```

* `box-sizing`: 박스 모델의 너비와 모델을 어떻게 결정할 것인지를 정하는 속성

```css
/*
  content-box: (기본값) 콘텐츠 영역만 너비와 높이를 설정
  border-box: 테두리까지 포함하여 너비와 높이를 설정
*/
box-sizing: content-box | border-box
```

* `box-shadow`: 박스 모델에 그림자 효과를 주는 속성

```css
/* inset: 안쪽 그림자 */
box-shadow: 수평거리 수직거리 흐림정도 번짐정도 색상 inset
```

### 테두리 스타일 지정

테두리 속성 값은 1 ~ 4개를 정할 수 있음. 이 때 값을 몇개 적용하느냐에 따라 적용 대상이 달라짐.
* 1개: `top`, `right`, `bottom`, `left` 모두 같은 값 적용
* 2개: 첫번째 속성 값은 `top, bottom`, 두번째 속성 값은 `left, right` 값 적용
* 3개: 순서대로 `top → right → bottom` 값 설정. left 값은 bottom 값을 따라감.
* 4개: 순서대로 `top → right → bottom → left` 값 설정

* `border-style`: 테두리를 그리는 속성

```css
border-style: none | hidden | solid | dotted | dashed | double | groove | inset | outset | ridge
```

* `border-width` 테두리 두께 속성

```css
border-width: 크기 | thin | medium | thick
```

* `border-color`: 테두리 컬러 속성

```css
border-color: 
```

* `border-radius`: 둥근 테두리 속성
  - 이미지를 원 형태로 만드려면 이미지의 너비와 높이를 1:1 비율로 만든 후 border-radius 값을 50%로 설정

```css
/* 속성 값을 1~4개로 정하여 꼭지점마다 둥글기를 다르게 설정할 수 있음 */
border-radius: 크기 | 백분율
```

### 여백 설정

웹 문서를 화면 중앙에 배치하려면  margin-left와 margin-right 속성 값을 auto로 설정.

```css
#container {
  margin: 20px auto;
}
```

마진 중첩은 아래, 위 마진이 서로 만날 때 큰 마진값으로 합쳐지는 것.

### 웹 문서 레이아웃 만들기

* `display`: 블록레벨 요소와 인라인레벨 요소를 서로 바꿔 사용하기 위한 속성
  - block: 인라인 레벨 요소를 블록 레벨 요소로 만듦
  - inline: 블록 레벨 요소를 인라인 레벨 요소로 만듦
  - inline-block: 인라인 레벨 요소와 블록 레벨 요소 속성을 모두 가짐
  - none: 화면에 표시하지 않음
```css
display: block | inline | inline-block | none
```

* `float`: 요소를 어느 쪽에 떠있게 할것 인지 정하는 속성

```css
float: left | right | none
```

* `clear`: float 속성을 사용하면 그 다음 요소에도 같은 속성이 전달됨. 더 이상 float 속성이 필요없음을 명시할 때 clear 속성 사용.

```css
/* 어떤 float 속성을 해제할 것인지 설정 */
clear: left | right | both
```

### 웹 요소의 위치 지정

웹 요소의 위치를 지정하려면 position 속성으로 기준 위치를 정한 뒤 `top`, `right`, `bottom`, `left` 속성 사용.

```css
#box1 {
  /*
    position 속성 값
    - static: (기본값) 문서 흐름에 맞춰 배치
    - relative: 위치값을 지정할 수 있도록 함. 이 외엔 static과 동일.
    - absolute: relative 값을 사용한 상위 요소를 기준으로 배치
    - fixed: 브라우저 창을 기준으로 배치
  */
  position: absolute;
  top: 10px;
  right: 20px;
  bottom: 10px;
  left: 20px;
}
```


## 배경 스타일

* `background-color`: 배경색 지정 속성
  - body 태그의 스타일은 모든 태그에 상속되지만, background-color 속성만 상속되지 않음.

```css
background-color: 
```

* `background-clip`: 배경색 적용 범위 속성
  - border-box: (기본값) 박스 모델의 가장 외곽인 테두리까지 적용
  - padding-box: 박스 모델의 패딩 범위까지 테두리 적용
  - content-box: 박스 모델의 콘텐츠 영역까지 테두리 적용

```css
background-clip: border-box | padding-box | content-box
```

* `background-image`: 배경 이미지 속성

```css
/* 이미지 파일 경로는 상대경로 또는 절대경로(URL)을 입력 */
background-image: url('이미지_경로')
```

* `background-repeat` 배경 이미지 반복 속성

```css
/* 각각 가로세로 반복(기본값), 가로로 반복, 세로로 반복, 반복하지 않음 */
background-repeat: repeat | repeat-x | repeat-y | no-repeat
```

* `background-position` 배경 이미지 위치 속성

```css
/* 속성에 사용할 수 있는 값: left, center, right, <백분율>, <길이값> */
background-position: <HOROZONTAL_POSITION> <VERTICAL_POSITION>
```

* `background-origin` 배경 이미지 적용 범위 속성
  - border-box: (기본값) 박스 모델의 가장 외곽인 테두리까지 적용
  - padding-box: 박스 모델의 패딩 범위까지 테두리 적용
  - content-box: 박스 모델의 콘텐츠 영역까지 테두리 적용
```css
background-origin: border-box | padding-box | content-box
```

* `background-attachment` 웹 문서 스크롤 시 배경 이미지 고정 속성

```css
background-attachment: fixed | scroll
```

* `background` 배경 이미지 제어 속성

```css
background: <BACKGROUND_IMAGE> <BACKGROUND-REPEAT> <BACKGROUND-POSITION> <BACKGROUND-ATTACHMENT>
```

* `background-size` 배경 이미지 크기 조절 속성
  - contain: 배경 이미지가 요소 안에 다 들어오도록 확대 축소
  - cover: 배경 이미지가 요소를 모두 덮도록 확대 축소
```css
background-size: auto | contain | cover | <크기> | <백분율>
```

그라디언트는 나중에…


## CSS 고급 선택자

웹 문서 내용이 많아지면 id와 class가 늘어나므로 각각에 스타일을 적용하기가 쉽지 않음. 연결 선택자와 속성 선택자를 사용하면 특정 요소들을 쉽게 선택하여 스타일을 적용할 수 있음.

### 연결 선택자

* `요쇼 요소` 선택자: 부모 요소에 포함된 모든 하위 요소를 선택[하위(자손) 선택자]

```css
/* 부모 요소(section)에 포함된 모든 하위 요소(p)에 스타일 적용 */
section p { }
```

* `요소 > 요소` 선택자: 자식 요소만 선택(자식 선택자)

```css
/* 부모 요소(section) 바로 아래에 존재하는 요소(p)에만 스타일 적용 */
section > p { }
```

* `요소 + 요소` 선택자: 서로 인접한 요소만 선택(인접 형제 선택자)

```css
/* h1과 인접한 p에만 스타일 적용 */
h1 + p { }
```

```html
<h1>Title</h1>
<p>Content 1</p>
<p>Content 2</p> <!-- 이 태그엔 스타일이 적용되지 않음 -->
```

* `요소 ~ 요소` 선택자: 모든 형제 요소를 선택(형재 선택자)

```css
/* h1과 나란히 위치한 p에 스타일 적용 */
h1 ~ p { }
```

```html
<h1>Title</h1>
<p>Content 1</p>
<p>Content 2</p> <!-- 이 태그까지 스타일이 적용됨 -->
```

### 속성 선택자

속성 선택자는 속성값에 따라 원하는 요소를 선택하며, 대괄호 `[]` 사이에 원하는 속성을 입력하면 됨.

```css
/* a 태그 중 href 속성이 있는 요소를 선택 */
a[href] { }
```

* `[속성 = 속성값]` 선택자: 주어진 속성과 속성 값이 일치하는 요소 선택

```css
/* <a href="_blank"> 인 요소 선택 */
a[href = _blank] { }
```

* `[속성 ~= 속성값]` 선택자: 해당 속성값이 정확하게 포함된 요소 선택

```css
/* 
	class 값 중 button이 있는 요소 선택 
  - class="button" 및 class="flat button" 은 선택함
  - class="flat-buttons" 는 선택하지 않음
*/
[class ~= button] { }
```

* `[속성 |= 속성값]` 선택자: 해당 속성값이 포함된 요소 선택
  - `[속성 ~= 속성값]` 선택자와의 차이점은, 전자는 속성값에 하이픈이나 공백이 들어가 있어도 선택하고, 후자는 속성값이 정확하게 포함되어 있어야 선택함.

```css
/*
  class 값 중 button이 포함된 요소 선택
  - class="button" 및 class="flat-buttons" 도 선택함
*/
[class |= button] { }
```

* `[속성 ^= 속성값]` 선택자: 해당 속성값으로 시작하는 요소 선택

```css
/* class 값이 btn으로 시작하는 요소 선택 */
[class ^= btn] { }
```

* `[속성 $= 속성값]` 선택자: 해당 속성값으로 끝나는 요소 선택

```css
/* <a href="asdf.pdf"> 와 같은 요소 선택 */
a[href $= pdf] { }
```

* `[속성 *= 속성값]` 선택자: 해당 속성 값이 어느 위치에서든지 포함되어 있는 요소 선택

```css
/* <a href="https://naver.com"> 과 같은 요소 선택 */
a[href *= naver] { }
```

### 가상 클래스 선택자

가상 클래스 선택자는 클래스 이름 앞에 콜론(`:`) 1개를 붙여 사용
* `:link`: 방문하지 않은 링크에 스타일 적용
* `:visited`: 방문한 링크에 스타일 적용
* `:hover`: 마우스 포인터를 올려 놓을 때 스타일 적용
* `:active`: 활성화된 요소에 스타일 적용
* `:focus`: 초점이 맞추어진 요소에 스타일 적용
* 가상 클래스 선택자의 우선순위는 `:link → :visited → :hover → :active`임

요소 상태에 따른 가상 클래스
* `:target`: 앵커의 목적지가 되는 요소의 스타일 적용
* `:enabled`: 사용 가능한 요소에 스타일 적용
* `:disabled`: 사용 불가한 요소에 스타일 적용
* `:checked`: checked 속성이 있는 요소에 스타일 적용
* `:not`: 특정 속성값을 제외한 요소를 스타일 적용

특정 위치의 자식 요소를 선택하려면 아래 선택자를 사용
- `:only-child` :
- 괄호 안에 변수를 n으로 하는 수식을 넣을 수 있음. 이 때 n 값은 0부터 시작함.

### 가상 요소

- `::first-line` 요소: 첫 번째 줄에 스타일 적용
- `::first-letter` 요소: 첫 번째 글자에 스타일 적용
- `::before` 요소: 요소 내용 앞에 스타일 추가
- `::after` 요소: 요소 내용 뒤에 스타일 추가

## 애니메이션