# 패스트캠퍼스 HTML & CSS 캠프 - 9번째 수업

## CSS 셀렉터 Level 3
```
문법:
Selector {
  name: value
}

예:
.btn {
  width: 100px;
}
```
1. Type Selector
  * 특정 요소의 이름을 가지고 Selecting
  * div {}
2. Attribute Selector
  * 특정 요소 or 클래스명의 이름에 특정 속성을 가지고있는 경우
```
HTML:
<button class="btn btn-primary">사용 가능한 버튼</button>
<button class="btn btn-primary" disabled>사용 불가능한 버튼</button>

CSS:
.btn {}
.btn-primary {}

.btn[disabled] {}
.btn:disabled {}

// 속성값이 완전히 일치하는 경우
// class 속성의 값이 btn인 경우
button[class=btn] {}

// 속성값이 존재하며, 공백문자로 구분되어 있는 경우,
// 공백문자로 구분되어 있는 목록 중 하나의 값과 일치만 하면 OK
// <button class="btn btn-primary"></button>
// btn, btn-primary
// .btn {}
button[class~=btn] {}

// 대시(-)로 구분된 값 목록에서 btn이란 값을 가지고 있다면 OK
// <button class="btn btn-primary"></button>
// btn-primary
// .btn {}
// <html lang="ko">
// language code = ko, ko-KR
// en, en-US, en-scouse, en-UK
button[class|=btn] {}
html[lang|=ko] {}
html:lang(en) {}

// 속성값이 존재하기만 하면 OK
// <button class="btn">테스트</button>
button[class*=btn] {}

// 속성값이 특정 값으로 시작하는 경우
// <button class="btn-primary">테스트</button>
button[class^=btn] {}

// 속성값이 특정 값으로 끝나는 경우
// <button class="btn-primary">테스트</button>
button[class$=primary] {}
```
3. Structure Class
* 첫번째 자식인데 `div`
  * :first-child
* 마지막 자식인데 `div`
  * :last-child
* nth-child(숫자)
  * 숫자번째 자식인데 `div`
* nth-last-child(숫자) {}
  * 뒤에서부터 숫자번째 자식인데 `div`

* `div` 중에 첫번째 자식
  * :first-of-type
* `div` 중에 마지막 자식
  * :last-of-type
* nth-of-type(숫자)
  * `div` 중에 숫자번째 자식
* nth-last-of-type(숫자) {}
    * `div` 중에 뒤에서부터 숫자번째 자식

* :only-child
  * 유일한 자식요소인 `div`
* :only-of-type
  * `div`인데 유일한 자식요소라면
* :empty
  * 요소 내부가 비어있는 경우
  * 검색결과 없을 때
  * .search-result:empty {}
```
HTML:
<main>
  <h1>제목</h1>
  <div>1</div>
  <div>2</div>
  <div>3</div>
  <div>4</div>
  <div>5</div>
  <footer>6</footer>
</main>

CSS:
main {}
div {}
div:first-child {} // X
div:last-child {} // X
div:first-of-type {} // 1
div:last-of-type {} // 5
div:nth-child(3) {}
div:nth-of-type(odd) {} // 홀수번째 자식인 모든 div
div:nth-of-type(even) {} // 짝수번째 자식인 모든 div
div:nth-of-type(3n - 1) {} // 2, 5, 8, 11, 14, ...
div:nth-of-type(3n + 1) {} // 4, 8, 12, 16, ...

블로그 글

[이미지] ㅁ니ㅓ아ㅣㅓ미나이ㅏ먼이
ㅁ니아ㅓㅁ나ㅣ어ㅣㅁ너ㅣㅏ어ㅣㅏㅁ너암ㄴ
ㅁ나ㅣㅓ이ㅏㅁ너이ㅏㅁ나어ㅏㅣㅁㄴㅇ
ㅁ니ㅏㅓ아ㅣㅁ넝ㅇㅁㄴㅇ  [이미지]
ㅁ나ㅣ어ㅣㅏㅁ너이ㅏ머나ㅣ어ㅣㅏㅁ넝ㅁㄴ
ㅁ니ㅏㅓㅇ마ㅣ너이ㅏ머니ㅏㅓ아ㅣㅁ너이
ㅁ니ㅏㅓ이마너아ㅣ머니ㅏ어머니ㅏ엄ㄴㅇ
[이미지] 머노아모나와ㅓㅁ놔ㅓ오ㅓㅏㅁ노어ㅏ

img:nth-of-type(odd) {float:left}
img:nth-of-type(even) {float:right}

```

4. 링크
* :link - 링크
* :visited - 이미 방문한 링크

5. 유저 액션
* :hover - 마우스 올렸을 때
  * 모바일에서는 안쓰는 게 좋음
* :active - 마우스 클릭했을 때
  * 터치 했을 때
* :focus - 포커스가 갔을 때

6. UI 상태
* :enabled {}
  * 사용 가능한 상태 (Default)
* :disabled {}
  * 사용 불가능한 상태 (disabled)
  * `<input disabled>`
* :checked {}
  * `<input type="checkbox" checked>`
  * `<input type="radio" checked>`

7. psuedo element
* CSS로 가상의 요소를 생성함
* ::before
  * 그 요소를 앞에 붙이고
* ::after
  * 그 요소를 뒤에 붙임
```
HTML:
> 각 li 앞에 아이콘을 넣고싶음

<ul>
<li>Video</li>
<li>Audio</li>
<li>Radio</li>
</ul>

CSS:
li::before {
  content: '';
}
li::after {
  content: '';
}
```
8. Combinator (결합자)
* 자손 콤비네이터
  * E F {}
  * div span {}
* 자식 콤비네이터
  * E > F {}
  * div > p {}
* 인접 형제 콤비네이터
  * E + F {}
  * h1 뒤에 바로 붙어있는 P요소
  * h1 + p {}
  * P 요소 뒤에있는 P 요소
  * p + p {}
* 일반 형제 콤비네이터
  * E ~ F {}
  * h1 뒤에 있는 모든 P요소
  * h1 ~ p {}
```
HTML:
<main>
  <div>
    <h1></h1>
    <p></p>
    <img src="" alt="">
    <p></p>
    <img src="" alt="">
    <p></p>
    <p></p>
  </div>
  <p>치킨 맛있엉</p> // blue
</main>

div + div {
  border-left:1px solid #eee;
}

CSS:
main p {
  color: red;
}
main > p {
  color: blue;
}
main ~ p {

}
main + p {

}
```

### 유의할 점 
* 셀렉터 우선순위
* 셀렉터 중 Class 셀렉터, 속성 셀렉터, 의사 클래스의 갯수를 셉니다 (=a)
* 셀렉터 중 Type 셀렉터랑 의사 요소의 갯수를 셉니다 (=b)
* 숫자를 세서 [ab] 순서로 나열했을 때 숫자가 높은 게 우선순위가 높음
* 타겟 요소 내에서만 우선순위가 갈림

```
.wrapper .container .side-nav {}
/* a=3, b=0 = 30 */
.wrapper .container .side-nav ul {
  color: red;
}
/* a=3, b=1 = 31 */
.side-nav ul li {
  color: blue;
}
/* 12 */
.side-nav ul li a {}

ul li {} // a=0, b=2, 2점
li {} // a=0, b=1 , 1점
li.menu {} // a=1, b=1, 11점
```

## CSS 미디어쿼리
### 오해
- 미디어쿼리가 반응형 웹 디자인의 가장 중요한 PART 중 하나이기는 함
- 그렇다고 해서 미디어쿼리를 반응형 웹 디자인에만 쓰는 건 아님

### 진실
- 미디어쿼리는 유저가 접속하는 미디어의 형태에 따라서 다른 CSS를 주고 싶을 때 사용
- 미디어
  - screen
  - print
  - handheld - 옛날 PDA
  - tv - 티비
  - projection - 프로젝터

### 사용법
```
CSS:
@media print {
  // CSS를 씀
}

```

### 미디어 특성
* width (너비)
* height (높이)
* aspect-ratio (해상도)
* orientation (눕혔는 지 세웠는 지)
* color (색상)
* resoultuon (픽셀 밀도)
* device-width
* device-height
* device-aspect-ratio

### 미디어 특성을 이용한 미디어 쿼리
```
CSS:
@media (조건) {
  // 조건이 맞으면
}

@media (width: 640px) {
  // 브라우저 사이즈가 딱 640px
}

// Tablet
@media (min-width: 720px) {
  // 브라우저 사이즈가 720px보다 큰 경우
  body {
    font-size: 16px;
  }
}

// 노트북 (랩탑)
// 엄청 큰 스마트 패드 (아이패드 프로, Surface)
@media (min-width: 1280px) {

}

// 데스크탑 (23인치 ~ 26인치)
@media (min-width: 1920px) {
  
}

// 엄청 큰 데스크탑 (27인치 이상)
@media (min-width: 2540px) {
  
}

@media (min-resoulution: 300dpi) {
  // 모니터의 출력이 300dpi 이상인 곳에서만 얘가 동작
  .header {
    background:url("header@2x.png") 0 0 no-repeat;
  }
}

```
* Mobile First
  * 콘텐츠의 배열이 Mobile => PC로 가는 것이 상대적으로 편함
* 미디어 쿼리는 항상 CSS의 마지막 부분에 작성

## CSS 방법론
* CSS가 쉬운가요?
  * CSS를 배우는 건 쉬운데 관리하고 쓰는 게 어려움

```
button {
  display:inline-block;
  padding: 1em;
  margin: 0.5em;
  font: inherit;
  background: #eee;
}
.btn-alert {
  padding: 3px 6px;
  font-size:14px;
  background: red;
}
```

* 어떻게 하면 큰 단위의 CSS를 잘 관리할 수 있을까?
* SMACSS
  * Scalable Modular Architecture for CSS
  * CSS를 카테고리로 쪼갬 (font관련된거면 font에 올인)
    * Base (기본 / 공통)
      * html {font-size:15px;}
    * Layout (레이아웃)
      * .row {}
      * col을 12단계로 쪼개서...
      * .col {float:left}
      * .col-3 {width:25%}
      * .col-4 {width:33.333333%}
      * .col-6 {width:50%}
      * .col-12 {width:100%}
    * Module (탭, 커스텀 인풋)
      * .tabs {}
      * .tabs nav {}
      * .tabs div {}
    * State (클릭했을 때 ...)
      * .btn:disabled {}
      * .btn:active {}
    * Theme (테마)
      * .tabs--gray {}
  * 어떤 걸 넣더라도 레이아웃이 깨지지 않게 하면 좋다 (==Layout)
  * 어떤 거 (==Module)
* OOCSS
  * bootstrap
  * bassCSS
  * 똑같음...
  * 스켙레톤하고 테마를 분리
    * .btn {} // 스켈레톤
    * .btn-default {} // 기본 테마
    * .btn-warning {} // 중요한 버튼
    * .btn-xs {}
    * .btn-sm {}
    * .btn-md {}
    * .btn-lg {}
    * .btn-xl {}

## 자바스크립트
  * 스펙 산정 잘 하는거
