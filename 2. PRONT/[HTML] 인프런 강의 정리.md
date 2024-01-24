# 강의 정리
### 목록
### 1. [HTML](#1-html-1)
### 2. [CSS](#2-css-1)
### 3. [JavaScript](#3-javascript-1)
---
###
# 1. HTML 
    HTML = Hyper Text Markup Language
    웹의 뼈대를 구성하기 위해 사용하는 마크업 언어
    태그(Tag)를 사용해서 구조를 만든다.

### Tag
- 태그는 여는것으로 시작해 닫는것으로 끝난다. : < html > ~ < /html >
- 가장 기본적인 태그
    ```html
    <html>
        <head>
        </head>
        <body>
        </body>
    </html>
    ```

### SPA?
- Single Page Application
- 웹을 만들다 보면 html 파일이 엄청나게 많이 생길텐데 이를 해결하기 위해 등장
    - React 와 관련
- Page 가 한개다? == html 파일이 한개
- 평소에는 body 태그 내부가 비어있다가 페이지에 접속할 때 페이지의 해당 콘텐츠를 가져와 동적으로 body 태그 내부를 채운다.




# 2. CSS 
    CSS = Cascading Style Sheets
    웹의 레이아웃과 글꼴, 색 등의 디자인을 입히는 역할을 하는 언어
    HTML 로 구조를 만들었다면 CSS로 디자인을 입힌다.



# 3. JavaScript 
     정식 명칭: ECMAScript
     웹이 살아움직이도록 생명 부여
     스크립트 언어의 한 종류
### 스크립트 언어?
- 다른 프로그래밍 언어와 가장 큰 차이는 프로그램이 실행되는 런타임에 코드가 해석된다.   
컴파일 언어(C, C# 등)는 컴파일을 통해 코드가 해석되고 실행 가능한 형태로 변환된다.
- RN = 앱용, 일렉트론 = 데탑용

### 기초
#### 1. 자료형
- 일반적인 언어는 변수 선언시 타입을 정하나 JS는 변수의 데이터가 대입되는 시점에 해당 변수의 타입이 결정된다. = Dynamic Typing(동적 타이핑)
- 변수 선언시 "var" 로 선언
    - "let" 선언도 존재
- String 타입 선언시 "" 과 '' 으로 선언한 내용은 다른 것이기에 주의
- Bool 타입은 true 와 false
- undefined 타입은 변수를 선언하고 값을 넣어주지 않았을 경우에 해당하나 값이 대입되는 순간 해당 자료형이 결정 됨 !== null 
    - null 은 값이 정의 된게 null 이라는 뜻임
- 배열에서 타입이 여러개 섞여 있는 배열도 구현이 가능함
    ```JavaScript
    let arr = [0, "one", undefined, 4, null, false];
    ```
- 객체는 Dictionary 와 유사한 타입이다.
    - 키와 값의 쌍으로 구성이 되며 키는 문자열, 값은 그 어떤 타입이든 상관없다
    ```JavaScript
    let obj = {a: 1, b: "Hello"};

    console.log(obj["a"]) // 1
    console.log(obj.a)    // 1
    ```




# 4. React