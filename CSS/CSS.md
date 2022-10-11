# CSS
- [CSS](#css)
  - [CSS란?](#css란)
  - [스타일과 스타일 시트](#스타일과-스타일-시트)
  - [CSS 기본 선택자](#css-기본-선택자)
  - [스타일 적용 순위](#스타일-적용-순위)
  - [스타일 상속](#스타일-상속)
  - [주요 스타일](#주요-스타일)
    - [글꼴 관련 스타일](#글꼴-관련-스타일)
    - [텍스트 관련 스타일](#텍스트-관련-스타일)
    - [목록 스타일](#목록-스타일)
    - [배경 스타일](#배경-스타일)
  - [박스 모델](#박스-모델)
    - [박스 모델의 주요 속성](#박스-모델의-주요-속성)
    - [테두리 스타일 지정](#테두리-스타일-지정)
    - [여백 설정](#여백-설정)
    - [웹 문서 레이아웃 만들기](#웹-문서-레이아웃-만들기)
    - [웹 요소의 위치 지정](#웹-요소의-위치-지정)
  - [CSS 고급 선택자](#css-고급-선택자)
    - [연결 선택자](#연결-선택자)
    - [속성 선택자](#속성-선택자)
    - [가상 클래스 선택자](#가상-클래스-선택자)
    - [가상 요소 선택자](#가상-요소-선택자)
  - [애니메이션](#애니메이션)
    - [변형(transform)](#변형transform)
    - [트랜지션(transition)](#트랜지션transition)
    - [애니메이션](#애니메이션-1)
  - [반응형 웹과 미디어 쿼리](#반응형-웹과-미디어-쿼리)
    - [뷰포트(Viewport)](#뷰포트viewport)
    - [미디어 쿼리(Media Queries)](#미디어-쿼리media-queries)
  - [그리드 레이아웃(Grid Layout)](#그리드-레이아웃grid-layout)
    - [플렉스 박스 레이아웃(Flex Box Layout)](#플렉스-박스-레이아웃flex-box-layout)
    - [CSS 그리드 레이아웃](#css-그리드-레이아웃)

## CSS란?

CSS는 Cascading Style Sheet 의 약자. Cascading은 우선순위가 계단식(위에서 아래)으로 적용된다는 의미로 사용.

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
* 인라인 스타일: 해당 태그에 style 속성을 정의하는 것
* 내부 스타일: HTML의 style 태그에 스타일을 작성하는 것
* 외부 스타일: 스타일을 별도 파일로 저장해 놓고 사용

```html
<!DOCTYPE html>
<html lang="ko">
<head>
  <!-- 외부 스타일: 스타일을 별도 파일로 저장해 놓고 사용 -->
  <link rel="stylesheet" href="CSS_FILE_PATH">
  <style>
    /* 내부 스타일: HTML의 style 태그에 스타일을 작성 */
    p {
      text-align: center;
    }
  </style>
</head>
<body>
  <!-- 브라우저 기본 스타일: 인라인, 내부, 외부 스타일이 정의되어 있지 않은 경우 사용 -->
  <h1>CSS World!</p>
  <!-- 인라인 스타일: 해당 태그에 style 속성을 정의 -->
  <p style="text-align: center;"></p>
</body>
</html>
```

## CSS 기본 선택자

* `*`: 전체 선택자. 스타일을 모든 문서 요소에 적용.
* 타입 선택자: 특정 태그를 사용한 모든 요소에 스타일을 적용
* `.`: 클래스 선택자. 같은 태그라도 여러 요소에 스타일을 적용(예: 특정 컨텐츠를 반복하는 경우 클래스를 사용하여 같은 CSS를 적용)
* `#`: ID 선택자. 하나의(고유한) 요소에만 스타일을 적용(예: header, content, footer, side-bar에 ID를 부여하여 고유하게 사용)
* `,`: 는 여러 태그에 동일한 스타일 규칙을 지정할 때 사용.

```css
/* 전체 선택자(*) */
* { margin: 0;}

/* 타입 선택자: 특정 태그에 스타일을 적용 */
p { text-align: center; }

/* 클래스 선택자(.) */
.p-center { text-align: center; }

/* ID 선택자(#) */
#container { text-align: center; }

/* 다중 선택자(,) */
p, div { text-align: center; }
```

## 스타일 적용 순위
* 중요도: 사용자가 지정한 스타일 → 웹 문서를 제작한 제작자의 스타일 → 웹 브라우저가 기본으로 정해 놓은 스타일
* 적용범위순: !important → 인라인 스타일 → id 스타일 → class 스타일 → 타입 스타일
* 작성순: 나중에 작성한 스타일이 먼저 작성한 스타일을 덮어씀

## 스타일 상속

자식 요소의 스타일을 별도로 지정하지 않았다면 부모 요소의 스타일의 속성들이 자식 요소에 그대로 전달되는 것.

예를 들어, body 태그는 웹 문서에 사용한 모든 태그의 부모 요소임. body 태그의 스타일은 웹 문서 전체에 적용됨.

## 주요 스타일

### 글꼴 관련 스타일

* `font-family`: 글꼴 속성
* `font-size`: 글자 크기 속성
* `font-style`: 이텔릭체 표시 속성
* `font-weight` : 글자 굵기 속성
  
```css
font-family: "맑은 글꼴", 굴림;

/*
  * 글자 크기 값에 사용 가능한 키워드는 xx-small, x-small, small, medkum, large, x-ragre, xx-large
  * 글자 크기 값에 사용 가능한 단위
    - 1em: 부모 요소 글꼴 대문자 M의 너비
    - 1rem: 문서 시작 부분(root)에서 지정한 크기
    - 1ex: 해당 글꼴의 소문자 x의 높이
    - 1px: 모니터의 1픽셀
    - 1pt: 일반 문서에서 주로 사용하는 단위
*/
font-size: 상대크기 | 절대크기 | 크기 | 퍼센트;

/* normal: 기본값 / italic 또는 oblique: 이탤릭체  */
font-style: normal | italic | oblique;


/*
  * 예약어 lighter, normal, bold, bolder 또는 숫자값 100~900 사이 사용.
  * 숫자값 400은 normal, 700은 bold임
*/
font-weight: lighter | normal | bold | bolder | 100~900;
```

### 텍스트 관련 스타일

* `color`: 텍스트 컬러 속성
* `text-align`: 문단 정렬 속성
* `line-height`: 줄간격 속성
* `text-decoration`: 텍스트 줄 긋기 속성
* `text-shadow`: 텍스트 그림자 효과 속성
* `text-transform`: 텍스트를 대문자 또는 전각문자로 변환하는 속성
* `letter-spacing` 글자 간격 조절 속성
* `word-spacing`: 단어 사이 간격 조절 속성

```css
/*
  * 사용 가능한 값
    - 색상 이름: black, white, yellow 등
    - 16진수: #RRGGBB 형태로 빨간색, 초록색, 파란색의 양을 표시
    - RGBA: 빨간색, 초록색, 파란색 값을 0~255 사이값으로 입력. 불투명도는 0~1 사이값으로 입력
    - HSL 또는 HSLA: 색상, 채도, 명도, 불투명도를 입력
*/
color: <COLOR_NAME> | <#RRGGBB> | <rgb(R, G, B)> | <rgba(R, G, B, A)> | <hsl(H, S, L)> | <hsla(H, S, L, A)>;

/*
  - justify: 양쪽에 맞추어 문단 정렬.
  - match-parent: 부모 요소를 따라 문단 정렬.
*/
text-align: start | end | left | right | center | justify | match-parent;

/* 아래 속성은 모두 줄 간격이 24px */
line-height: 24px;
line-hgight: 2.0; 
line-height: 200%;

/* 각각 기본값, 밑줄, 윗줄, 취소선 */
text-decoration: none | underline | overline | line-through;

text-shadow: none | <WIDTH> <HEIGHT> <BLUR_RADIUS> <COLOR>;

/* 각각 첫 글자를 대문자로 변환, 모든 글자를 대문자로 변환, 모든 글자를 소문자로 변환, 가능한 한 모든 문자를 전각 문자로 변환 */
text-transform: capitalize | uppercase | lowercase | full-width;

letter-spacing: <px> | <em> | <%>;
word-spacing: <px> | <em> | <%>;
```



### 목록 스타일

* `list-style-type`: 목록 앞에 불릿 기호 또는 번호를 넣는 속성
* `lst-style-image`: 목록 앞에 이미지를 넣는 속성
* `list-style-position`: 목록 앞에 불릿이나 번호를 넣는 속성
* `list-style`: 위 속성들을 한 번에 사용하는 속성
* `caption-side`: 표 제목 위치 속성
* `border`: 표 테두리 속성
* `border-spacing`: 셀과 셀 사이 여백 속성
* `border-collapse`: 표와 셀 테두리를 합치는 속성

```css
list-style-type: none | disc | circle | square | decimal | decimal-leading-zero | lower-roman | uppper-roman | lower-alpha | lower-latin | upper-alpha | upper-latin;
list-style-image: none | <url('IMAGE_URL')>;
list-style-position: inside | outside;
list-style: <LIST_STYLE_TYPE> <LIST_STYLE_POSITION>;
caption-side: top | bottom;

/* 1픽셀 직선 블랙인 테두리 */
border: 1px solid black;

border-spacing: 가로여백 | 세로여백;
border-collapse: separate | collapse;
```

### 배경 스타일

* `background-color`: 배경색 지정 속성
* `background-clip`: 배경색 적용 범위 속성
* `background-image`: 배경 이미지 속성
* `background-repeat` 배경 이미지 반복 속성
* `background-position` 배경 이미지 위치 속성
* `background-origin` 배경 이미지 적용 범위 속성
* `background-attachment` 웹 문서 스크롤 시 배경 이미지 고정 속성
* `background-size` 배경 이미지 크기 조절 속성
* `background` 배경 이미지 주요 속성을 한 번에 설정
  
```css
/* body 태그의 스타일은 모든 태그에 상속되지만, background-color 속성만 상속되지 않음. */
background-color: ;

/*
  - border-box: (기본값) 박스 모델의 가장 외곽인 테두리까지 적용
  - padding-box: 박스 모델의 패딩 범위까지 테두리 적용
  - content-box: 박스 모델의 콘텐츠 영역까지 테두리 적용
*/
background-clip: border-box | padding-box | content-box;

/* 이미지 파일 경로는 상대경로 또는 절대경로(URL) 입력 */
background-image: url('이미지_경로');

/* 각각 가로세로 반복(기본값), 가로로 반복, 세로로 반복, 반복하지 않음 */
background-repeat: repeat | repeat-x | repeat-y | no-repeat;

/* 속성에 사용할 수 있는 값: left, center, right, <백분율>, <길이값> */
background-position: <HOROZONTAL_POSITION> <VERTICAL_POSITION>;

/*
  - border-box: (기본값) 박스 모델의 가장 외곽인 테두리까지 적용
  - padding-box: 박스 모델의 패딩 범위까지 테두리 적용
  - content-box: 박스 모델의 콘텐츠 영역까지 테두리 적용
*/
background-origin: border-box | padding-box | content-box;

background-attachment: fixed | scroll;

background: <BACKGROUND_IMAGE> <BACKGROUND-REPEAT> <BACKGROUND-POSITION> <BACKGROUND-ATTACHMENT>;

/*
  - contain: 배경 이미지가 요소 안에 다 들어오도록 확대 축소
  - cover: 배경 이미지가 요소를 모두 덮도록 확대 축소
*/
background-size: auto | contain | cover | <size> | <percentage>;
```

그라디언트는 나중에…


## 박스 모델

* 박스 모델은 콘텐츠, 패딩(콘텐츠와 박스 영역 사이), 마진(박스 바깥 영역) 으로 구성. [http://www.tcpschool.com/css/css_boxmodel_boxmodel](http://www.tcpschool.com/css/css_boxmodel_boxmodel) 참고.
* 블록 레벨 요소는 한 줄을 차지하는 태그(h, div, p 등).
* 인라인 레벨 요소는 한 줄을 차지하지 않고 요소 크기만큼 차지하는 태그(span, img, strong 등).

### 박스 모델의 주요 속성

* `width` 및 `height`: 콘텐츠 영역 크기를 지정하는 속성
* `box-sizing`: 박스 모델의 너비와 모델을 어떻게 결정할 것인지를 정하는 속성
* `box-shadow`: 박스 모델에 그림자 효과를 주는 속성

```css
width: <px> | <em> | <%> | auto;
height: <px> | <em> | <%> | auto;

/*
  content-box: (기본값) 콘텐츠 영역만 너비와 높이를 설정
  border-box: 테두리까지 포함하여 너비와 높이를 설정
*/
box-sizing: content-box | border-box;

/* inset: 안쪽 그림자 */
box-shadow: 수평거리 수직거리 흐림정도 번짐정도 색상 inset;
```

### 테두리 스타일 지정

테두리 속성 값은 1 ~ 4개를 정할 수 있음. 이 때 값을 몇개 적용하느냐에 따라 적용 대상이 달라짐.
* 1개: `top`, `right`, `bottom`, `left` 모두 같은 값 적용
* 2개: 첫번째 속성 값은 `top, bottom`, 두번째 속성 값은 `left, right` 값 적용
* 3개: 순서대로 `top → right → bottom` 값 설정. left 값은 bottom 값을 따라감.
* 4개: 순서대로 `top → right → bottom → left` 값 설정

주요 테두리 속성들
* `border-style`: 테두리를 그리는 속성
* `border-width` 테두리 두께 속성
* `border-color`: 테두리 컬러 속성
* `border-radius`: 둥근 테두리 속성

```css
border-style: none | hidden | solid | dotted | dashed | double | groove | inset | outset | ridge;
border-width: <size> | thin | medium | thick;
border-color: 

/* 
  - 속성 값을 1~4개로 정하여 꼭지점마다 둥글기를 다르게 설정할 수 있음 
  - 이미지를 원 형태로 만드려면 이미지의 너비와 높이를 1:1 비율로 만든 후 border-radius 값을 50%로 설정
*/
border-radius: <size> | <percetnage>
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
* `float`: 요소를 어느 쪽에 떠있게 할것 인지 정하는 속성
* `clear`: float 속성을 사용하면 그 다음 요소에도 같은 속성이 전달됨. 더 이상 float 속성이 필요없음을 명시할 때 clear 속성 사용.

```css
/*
  - block: 인라인 레벨 요소를 블록 레벨 요소로 만듦
  - inline: 블록 레벨 요소를 인라인 레벨 요소로 만듦
  - inline-block: 인라인 레벨 요소와 블록 레벨 요소 속성을 모두 가짐
  - none: 화면에 표시하지 않음
*/
display: block | inline | inline-block | none;

float: left | right | none;

/* 어떤 float 속성을 해제할 것인지 설정 */
clear: left | right | both;
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


## CSS 고급 선택자

웹 문서 내용이 많아지면 id와 class가 늘어나므로 각각에 스타일을 적용하기가 쉽지 않음. 연결 선택자와 속성 선택자를 사용하면 특정 요소들을 쉽게 선택하여 스타일을 적용할 수 있음.

### 연결 선택자

* `요쇼 요소` 선택자: 부모 요소에 포함된 모든 하위 요소를 선택[하위(자손) 선택자]
* `요소 > 요소` 선택자: 자식 요소만 선택(자식 선택자)
* `요소 + 요소` 선택자: 서로 인접한 요소만 선택(인접 형제 선택자)
* `요소 ~ 요소` 선택자: 모든 형제 요소를 선택(형재 선택자)

```css
/* '요소 요소' 선택자: 부모 요소(section)에 포함된 모든 하위 요소(p)에 스타일 적용 */
section p { }

/* '요소 > 요소' 선택자: 부모 요소(section) 바로 아래에 존재하는 요소(p)에만 스타일 적용 */
section > p { }

/* '요소 + 요소' 선택자: h1과 인접한 p에만 스타일 적용 */
h1 + p { }
/*
<h1>Title</h1>
<p>Content 1</p>
<p>Content 2</p> <!-- 이 태그엔 스타일이 적용되지 않음 -->
*/

/* '요소 ~ 요소' 선택자: h1과 나란히 위치한 p에 스타일 적용 */
h1 ~ p { }
/*
<h1>Title</h1>
<p>Content 1</p>
<p>Content 2</p> <!-- 이 태그까지 스타일이 적용됨 -->
*/
```


### 속성 선택자

속성 선택자는 속성값에 따라 원하는 요소를 선택하며, 대괄호 `[]` 사이에 원하는 속성을 입력하면 됨.

* `[속성 = 속성값]` 선택자: 주어진 속성과 속성 값이 일치하는 요소 선택
* `[속성 ~= 속성값]` 선택자: 해당 속성값이 정확하게 포함된 요소 선택
* `[속성 |= 속성값]` 선택자: 해당 속성값이 포함된 요소 선택
  - `[속성 ~= 속성값]` 선택자와의 차이점은, 전자는 속성값에 하이픈이나 공백이 들어가 있어도 선택하고, 후자는 속성값이 정확하게 포함되어 있어야 선택함.
* `[속성 ^= 속성값]` 선택자: 해당 속성값으로 시작하는 요소 선택
* `[속성 $= 속성값]` 선택자: 해당 속성값으로 끝나는 요소 선택
* `[속성 *= 속성값]` 선택자: 해당 속성 값이 어느 위치에서든지 포함되어 있는 요소 선택

```css
/* a 태그 중 href 속성이 있는 요소를 선택 */
a[href] { }

/* <a href="_blank"> 인 요소 선택 */
a[href = _blank] { }

/* 
	class 값 중 button이 있는 요소 선택 
  - class="button" 및 class="flat button" 은 선택함
  - class="flat-buttons" 는 선택하지 않음
*/
[class ~= button] { }

/*
  class 값 중 button이 포함된 요소 선택
  - class="button" 및 class="flat-buttons" 도 선택함
*/
[class |= button] { }

/* class 값이 btn으로 시작하는 요소 선택 */
[class ^= btn] { }

/* <a href="asdf.pdf"> 와 같은 요소 선택 */
a[href $= pdf] { }

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
- `:only-child`: 부모 안에 자식 요소가 하나 뿐일 때 자식 요소를 선택
- `A:only-child`: 부모 안에 A 요소가 하나 뿐일 때 선택
- `:first-child`: 부모 안에 있는 요소 중 첫 번째 요소 선택
- `:last-child`: 부모 안에 있는 요소 중 마지막 요소 선택
- `A:first-of-type`: 부모 안에 있는 A 요소 중 첫 번째 선택
- `A:last-of-type`: 부모 안에 있는 A 요소 중 마지막 선택
- `:nth-child(n)`: 부모 안에 있는 요소 중 n번째 요소 선택
- `:nth-last-child(n)`: 부모 안에 있는 요소 중 끝에서 n번째 요소 선택
- `A:nth-of-type(n)`: 부모 안에 있는 A 요소 중 n번째 요소 선택
- `A:nth-last-of-type(n)`: 부모 안에 있는 A 요소 중 끝에서 n번째 요소 선택
- 괄호 안에 변수를 n으로 하는 수식을 넣을 수 있음. 이 때 n 값은 0부터 시작하며, 홀수 번째는 odd, 짝수 번째는 even을 사용.

### 가상 요소 선택자

- `::first-line` 요소: 첫 번째 줄에 스타일 적용
- `::first-letter` 요소: 첫 번째 글자에 스타일 적용
- `::before` 요소: 요소 내용 앞에 내용 또는 스타일 추가
- `::after` 요소: 요소 내용 뒤에 내용 또는 스타일 추가

---

## 애니메이션

### 변형(transform)
* CSS에서 변형을 적용하려면 transform 속성을 사용
* transform 속성에 사용하는 주요 함수: translate, scale, rotate, skew, perspective 등

### 트랜지션(transition)
* 트랜지션은 스타일 속성이 바뀌는 것
* `transition-property`: 어떤 속성에 트랜지션을 적용할 것인지 명시
* `transition-duration`: 트랜지션 진행시간 설정. transition-property 대상이 여러 개라면 진행시간을 쉼표로 구분하여 여러 값 입력.
* `transition-timing-function`: 트랜지션 효과의 시작, 중간, 끝에서 속도를 지정해 속도 곡선을 만듦
* `transition-delay`: 트랜지션 효과를 언제부터 시작할 것인지 설정. 단위는 s또는 ms.
* `transition`: 위에서 설명한 트랜지션 속성 4가지를 한 번에 명시. 속성 값을 작성하는 순서는 상관 없음.

```css
/*
  - all: all을 사용하거나 transtion-property를 생략할 경우 모든 속성이 트랜지션 대상이 됨
  - none: 트랜지션 효과를 적용하는 동안 아무 속성도 바뀌지 않음
  - 속성이름: 트랜지션 효과를 적용할 속성 명시
*/
transition-property: all | none | <PROPERTY_NAME>;

transition-property: width, height;
transition-duration: 2s, 1s;

/*
  - ease: 천천히 시작하고 빨라지다가 마지막에 천천히 끝냄(기본값)
  - linear: 시작과 끝까지 모두 같은 속도로 끝냄
  - ease-in: 느리게 시작
  - ease-out: 느리게 끝냄
  - ease-in-out: 느리게 시작하고 느리게 끝냄
  - cubic-bezier(n, n, n, n): 베지에 함수를 정의하여 사용(0~1 사이값 사용)
*/
transition-timing-function: ease | linear | ease-in | ease-out | ease-in-out | cubic-bezier(n, n, n, n);

transition: <TRANSITION-PROPERTY> | <TRANSITION-DURATION> | <TRANSITION-TIMING-FUNCTION> | <TRANSITION-DELAY>
```

### 애니메이션

* `@keyframe`: 애니메이션에서 스타일이 바뀌는 지점
* `animation-name`: 애니메이션을 여러 개 정의할 때 구분하기 위한 이름. 어떤 키프레임을 사용할 것인지 명시.
* `animation-duration`: 애니메이션 재생 시간. 단위는 s 또는 ms. 기본 값은 0.
* `animation-direction`: 애니메이션 진행 방향
* `animation-iteration-count`: 애니메이션 반복 횟수. infinite로 설정하면 무한 반복.
* `animation-timing-function`: 애니메이션의 시작, 중간, 끝에서 속도를 지정해 속도 곡선을 만듦
* `animation`: 위에서 설명한 애니메이션 속성들을 한 번에 명시할 때 사용

```css
@keyframes <NAME> {
  from { /* 시작할 스타일 */ }
  to { /* 끝낼 스타일 */ }
}

animation-name: none | <NAME>;
animation-duration: <s> | <ms>;

/*
  - normal: from에서 to로 진행
  - reverse: to에서 from으로 진행
  - alternative: 홀수 번째는 normal로, 짝수 번째는 reverse로 진행
  - alternative-reverse: 홀수 번째는 reverse로, 짝수 번째는 normal로 진행
*/
animation-direction: normal | reverse | alternative | alternative-reverse;

animation-iteration-count: <count> | infinite;

/*
  - ease: 천천히 시작하고 빨라지다가 마지막에 천천히 끝냄(기본값)
  - linear: 시작과 끝까지 모두 같은 속도로 끝냄
  - ease-in: 느리게 시작
  - ease-out: 느리게 끝냄
  - ease-in-out: 느리게 시작하고 느리게 끝냄
  - cubic-bezier(n, n, n, n): 베지에 함수를 정의하여 사용(0~1 사이값 사용)
*/
animation-timing-function: ease | linear | ease-in | ease-out | ease-in-out | cubit-bezier(n, n, n, n);

animation: <ANIMATION-NAME> | <ANIMATION-DURATION> | <ANIMATION-TIMING-FUNCTION> | <ANIMATION-DELAY> | <ANIMATION-ITERATION-COUNT> | <ANIMATION-DIRECTION>
```


## 반응형 웹과 미디어 쿼리

반응형 웹 디자인(Responsive Web Design)은 기존 웹 사이트 내용을 그대로 유지하면서 다양한 화면 크기에 맞추어 표시해주도록 함.

### 뷰포트(Viewport)

뷰포트는 사용 중인 기기의 화면에 맞추어 웹 문서를 확대 또는 축소하여 콘텐츠를 표시하는 영역.

뷰포트를 사용하려면 meta 태그에 뷰포트를 사용할 것을 선언해줘야 함.

```html
<head>
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
</head>
```

뷰포트를 사용하면 px와 같은 단위 대신 뷰포트 전용 단위를 사용할 수 있음
* `vw`: 1vw는 뷰포트 너비의 1%
* `vh`: 1vh는 뷰포트 높이의 1%
* `vmin`: 1vmin은 뷰포트 너비와 높이 중 작은 값의 1%
* `vmax`: 1vmax는 뷰포트 너비와 높이 중 큰 값의 1%

### 미디어 쿼리(Media Queries)

미디어 쿼리는 서로 다른 기기의 해상도에 따라 스타일을 다르게 보여주는 것.

미디어 쿼리는 `@media` 속성을 사용하여 특정 기기에서 어떤 스타일을 보여줄 것인지 정의함
* only: 미디어 쿼리를 지원하지 않는 웹 브라우저에서는 해당 미디어 유형을 무시함
* not: 해당 미디어 유형을 제외함
* and: 조건들을 연결함(해당 조건에 맞는 기기라면 미디어 쿼리를 적용)

```css
/* 기본형 */
@media [only | not] 미디어_유형 [and] 조건1 [and] 조건2 /* ... */

/* 예시 */
@media screen and (min-width: 768px) and (max-width: 1439px)
```

미디어 유형 종류는 `all, print, screen, tv, aural, braille, handheld, projection, tty, embossed` 등이 있음.

```css
/* 화면용 스타일 작성 */
@media screen { }

/* TV용 스타일 작성 */
@media tv { }
```

미디어 조건에 사용할 수 있는 속성들
* 웹 문서의 너비, 높이: width, height, min-width, min-height, max-width, max-height
* 단말기의 너비, 높이: device-width, device-height, min-device-width, min-device-height, max-device-width, max-device-height
* 화면 회전 속성: orientation: portrait(세로 방향), orientation: landscape(가로 방향)

```css
/* 스크린 최소 너비가 400px이고 가로 방향일 경우에 대한 스타일 작성 */
@media screen and (min-device-width: 400px) and (orientation: landscape) { }
```

미디어 쿼리의 중단점(Break Point)은 화면 크기에 따라서 다른 CSS를 적용할 분기점을 가리킴.
* 시중에 나온 모든 기기들의 CSS를 반영할 수 없으므로 모바일, 태블릿 및 데스크톱 정도로 구분하는 것이 좋음
* 위 세 가지 경우 중 모바일의 제약사항이 크므로 모바일을 먼저 고려하여 미디어 쿼리를 작성하기도 함(Mobile First 기법)

미디어 쿼리는 외부에서 작성한 CSS 파일을 연결하거나, 웹 문서에 직접 정의함.

```html
<!-- link 태그로 미디어 쿼리가 정의된 CSS 파일을 가져오거나 -->
<link rel="stylesheel" media="미디어_쿼리_조건" href="CSS_파일_경로">

<!-- style 태그 내에서 미디어 쿼리가 정의된 CSS 파일을 가져옴 -->
<style>
  @import url(CSS_파일_경로) 미디어_쿼리_조건;
</style>
```

```html
<!-- style 태그 내에서 미디어 쿼리를 직접 작성 -->
<style media="미디어_쿼리_조건">
  { /* 스타일 작성 */ }
</style>
```

## 그리드 레이아웃(Grid Layout)
* 그리드 레이아웃은 웹 사이트를 여러 개의 컬럼으로 나눠 배치하는 방법
* 플렉서블 박스 레이아웃(플렉스 박스 레이아웃) 또는 그리드 레이아웃을 주로 사용

### 플렉스 박스 레이아웃(Flex Box Layout)
* 플렉스 박스 레이아웃은 수평, 수직 방향 중에서 한 쪽을 주축으로 정한 후 박스를 배치하는 방법
* 플렉스 컨테이너로 작동할 항목(부모)을 선언한 후, 그 안에 항목(자식)을 배치

플렉스 컨테이너로 선언된 요소에서 사용하는 주요 속성들
* `display`: 해당 요소가 플렉스 컨테이너로 작동하도록 설정
* `flex-direction`: 주축과 방향 설정
* `flex-wrap`: 플렉스 컨테이너 너비보다 많은 항목이 있을 때 줄바꿈 여부
* `flex-flow`: flex-direction 및 flex-wrap 속성을 한번에 지정
* `justify-content`: 주축에서 플렉스 항목들을 어떻게 정렬할 것인지 지정
* `align-items`: 교차축에서 플랙스 항목들을 어떻게 정렬할 것인지 지정
* `align-self`: 특정 플렉스 항목을 교차축 기준으로 어떻게 배치할 것인지 설정(플렉스 컨테이너가 아닌, 플렉스 항목에서 사용하는 속성)
* `align-content`: 줄바꿈이 발생했을 때 줄간격을 어떻게 설정할 것인지 지정

플랙스 컨테이너에 포함된 요소에서 사용하는 주요 속성
* `align-self`: 특정 플렉스 항목을 교차축 기준으로 어떻게 배치할 것인지 설정

```css
/*
  - flex: 컨테이너 안의 플렉스 항목을 블록 레벨 요소로 배치
  - inline-flex: 컨테이너 안의 플렉스 항목을 블록 인라인 요소로 배치
*/
display: flex | inline-flex;

/*
  - row: 주축을 가로로 지정하고, 왼쪽에서 오른쪽으로 배치(기본값)
  - row-reverse: 주축을 가로로 지정하고, 오른쪽에서 왼쪽으로 배치
  - column: 주축을 세로로 지정하고, 왼쪽에서 오른쪽으로 배치
  - column-reverse: 주축을 세로로 지정하고, 오른쪽에서 왼쪽으로 배치
*/
flex-direction: row | row-reverse | column | column-reverse;

/*
  - nowrap: 한 줄에 표시(기본값)
  - wrap: 여러 줄에 표시
  - wrap-reverse: 여러 줄에 표시하되, 시작점과 끝점이 바뀜
*/
flex-wrap: nowrap | wrap | wrap-reverse;

/*
  - flex-start: 주축의 시작점에 맞춰 배치
  - flex-end: 주축의 끝점에 맞춰 배치
  - center: 주축의 중앙에 맞춰 배치
  - space-between: 첫 항목과 마지막 항목을 양 끝에 배치한 후, 나머지 항목들을 같은 간격으로 배치
  - space-around: 모든 항목을 주축에 같은 간격으로 배치
*/
justify-content: flex-start | flex-end | center | space-between | space-around;

/*
  - flex-start: 주축의 시작점에 맞춰 배치
  - flex-end: 주축의 끝점에 맞춰 배치
  - center: 주축의 중앙에 맞춰 배치
  - baseline: 교차축의 문자 기준선에 맞춰 배치
  - stretch: 교차축에 가득 차게 배치
*/
align-items: flex-start | flex-end | center | baseline | stretch;

/*
  - flex-start: 주축의 시작점에 맞춰 배치
  - flex-end: 주축의 끝점에 맞춰 배치
  - center: 주축의 중앙에 맞춰 배치
  - baseline: 교차축의 문자 기준선에 맞춰 배치
  - stretch: 교차축에 가득 차게 배치
*/
align-content: flex-start | flex-end | center | baseline | stretch;

/*
  - flex-start: 주축의 시작점에 맞춰 배치
  - flex-end: 주축의 끝점에 맞춰 배치
  - center: 주축의 중앙에 맞춰 배치
  - baseline: 교차축의 문자 기준선에 맞춰 배치
  - stretch: 교차축에 가득 차게 배치
*/
align-self: flex-start | flex-end | center | baseline | stretch;
```

### CSS 그리드 레이아웃

CSS 그리드 레이아웃은 Column과 Row로 웹 화면을 구성

그리드 컨테이너로 선언된 요소에서 사용하는 주요 속성들
* `display`: 해당 요소가 그리드 컨테이너로 작동하도록 설정
* `grid-template-columns`: 그리드 컨테이너의 Column 개수 설정
* `grid-template-rows`: 그리드 컨테이너의 Row 개수 설정
* `column-gap`: Column 간 간격 설정
* `row-gap`: Row 간 간격 설정
* `gap`: Column 및 Row 간 간격을 한 번에 설정

```css
/*
  - grid: 컨테이너 안의 항목을 그리드 블록 레벨 요소로 배치
  - inline-grid: 컨테이너 안의 항목을 그래드 인라인 레벨 요소로 배치
*/
display: grid | inline-grid;

/* 크기가 200px인 Column 3개 설정 */
grid-template-columns: 200px 200px 200px;

/* 그리드 레이아웃에서는 절대크기인 px와 다른, 상대크기를 지정할 수 있는 fr 단위 사용 가능 */
/* 1:2:1 비율의 컬럼 설정 */
grid-template-columns: 1fr 2fr 1fr;

/* 1fr 3개의 컬럼 설정 */
grid-template-columns: repeat(3, 1fr);

/* Column 개수를 자동으로 조절하여 배치하고, 컨테이너에 남는 공간이 없도록 꽉 채움 */
grid-template-columns: repeat(auto-fit, 1fr);

/* Column 개수를 자동으로 조절하여 배치함. 컨테이너에 남는 공간이 생길 수 있음. */
grid-template-columns: repeat(auto-fill, 1fr);

/* 크기가 100px인 Row 설정 */
grid-template-rows: 100px;

/* Row 크기를 최소 200px로 설정하고, 내용이 많아질 경우 크기를 더 늘리도록 함 */
grid-template-rows: minmax(200px, auto);

/* grid-column-gap, grid-row-gap 및 grid-gap은 Deprecated 되었으므로 아래 속성으로 대체 사용 */
column-gap: 20px;
row-gap: 10px;
gap: 20px 10px;
```

그리드 컨테이너에 포함된 요소에서 사용하는 주요 속성
* `grid-column-start`: 배치할 Column의 시작 번호
* `grid-column-end`: 배치할 Column의 끝 번호
* `grid-column`: 배치할 Column의 시작-끝 번호를 한 번에 설정
* `grid-row-start`: 배치할 Row의 시작 번호
* `grid-row-end`: 배치할 Row의 끝 번호
* `grid-row`: 배치할 Row의 시작-끝 번호를 한 번에 설정

```css
/* 그리드 컨테이너 내 요소를 Column 1~3번 크기만큼 배치 */
grid-column-start: 1;
grid-column-end: 3;
grid-column: 1/3;

/* 그리드 컨테이너 내 요소를 Row 1~2번 크기만큼 배치 */
grid-row-start: 1;
grid-row-end: 2;
grid-row: 1/2;
```

그리드 템플릿 영역을 만들어 배치할 수도 있음.

```css
/* 그리드 컨테이너 설정 */
#container {
    width: auto;
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-template-rows: repeat(3, 100px);

    /* 아래와 같이 그리드 템플릿을 배치 */
    grid-template-areas: 
      "box1 box1 box1"
      "box2 box3 box4"
      "box2 .    box4"; /* 빈 공간으로 두려면 . 사용 */
}

/* class명에 box가 포함된 요소 레이아웃 */
.box{
    padding: 15px;
    color: #fff;
    font-weight: bold;
    text-align: center;
  }   

/* box1 ~ 4: 그리드 템플릿 영역 */
.box1 {
    background-color: burlywood;
    grid-area: box1;
}

.box2 {
    background-color: yellowgreen;
    grid-area: box2;
}

.box3 {
    background-color: royalblue;
    grid-area: box3;
}

.box4 {
    background-color: goldenrod;
    grid-area: box4;
}
```

```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="style.css">
    <title>Document</title>
</head>
<body>
    <div id="container">
        <!-- box1 ~ 4: 그리드 템플릿 -->
        <div class="box box1">box1</div>
        <div class="box box2">box2</div>
        <div class="box box3">box3</div>
        <div class="box box4">box4</div>
    </div>
</body>
</html>
```