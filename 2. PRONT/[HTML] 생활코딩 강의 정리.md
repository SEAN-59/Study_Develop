# 강의 정리

강의 주소: [WEB1 - 생활코딩](https://opentutorials.org/course/3084)

## TAG
### 00. 태그 특징
- 태그는 중첩해서 사용할 수도 있다.
    - 순서 상관 없이 중첩해서도 사용이 가능하다. 
        ```
            <a>...<b>...</a>...</b>
            <a>...<b>...</b>...</a>
        ```

- 태그 이름만으로는 정보가 부족하다
    - 새로운 문법의 필요성을 느낌 = 속성(attribute)

- 태그 간의 관계: 부모(parent) / 자식(child)
    - 아래와 같은 구조로 부모와 자식을 구분 할 수 있다.
    - 다음과 같은 구조로 되어있다고 해도 부모 태그가 꼭 자식 태그의 부모인것도 아니고 반대인 경우도 아니다
        - 필요에 따라서 달라질 수 있는 관계이다.
    ```
        <parent>
            <child>...</child>
        </parent>
    ```

### 1. String 강조 표시
```html
    <strong>...</strong>
```

### 2. 밑줄 표시
```html
    <u>...</u>
```

### 3. 한글이 깨진다면?
- 웹브라우저에게 UTF-8로 페이지를 열라고 지정해주는 코드
```html
    <meta charset="utf-8">
```

### 4. 제목 태그
- 작은 숫자부터 큰 숫자로 점점 크기가 작아지는 것을 볼 수 있다.
```html
    <h1>...</h1>
    <h2>...</h2>
    <h3>...</h3>
    <h4>...</h4>
    <h5>...</h5>
    <h6>...</h6>
```

### 5. 인기 있는 태그
- head > body > html > title > meta > div > a > script > link > img > p > span > li > ul > br > style > h1 > h2 > input > form > strong > h3 > table > tr > td

### 6. 줄바꿈 태그
- br 태그와 p 태그의 결과는 거의 같다.
- 단락을 표현할 떄는 p 태그가 더 좋은 선택으로 단락에 단락 태그를 사용하는 것이 웹을 정보로서 가치 있게 해준다.
- br 태그는 줄바꿈을 의미할 뿐이다.
- p 태그의 단점으로는 단락과 단락의 간격이 고정되어 있기에 시각적 자유도가 떨어진다.
    - br 태그는 쓰는만큼 줄바꿈이 되기 때문에 원하는 만큼 간격을 줄 수 있는 장점이 있다.
    - CSS 를 이용하면 p 태그의 한계를 극복 가능하다.
```html
    <br>
    <p>...</p>
```

- 위쪽에 45px의 여백을 주는 p 태그의 조건을 변경 할 수 있다.
```CSS
    <p style="margin-top:45px;">
```

### 7. 이미지 태그
- 소스 파일 안의 같은 폴더내에 위치하는 이미지 파일이라면 이미지 이름만 적어주는거로도 불러올 수 있다.
- src : source 의 줄임말
- width : 가로 값 (숫자나 %를 사용해 크기 조정 가능)

```html
    <img src="이미지 주소">
    <img src = "
https://s3-ap-northeast-2.amazonaws.com/opentutorials-user-file/module/3135/7648.png">
    <img src = "이미지" width = "100%">
```

### 8. 목차 태그
- 목록을 사용하기 위해서는 li 태그
- 목록과 다른 목록을 구분하기 위한 경계를 위해서는 ul 태그를 사용
- li 태그는 ul 태그를 필요로 하고 ul 태그는 li 태그가 없다면 가치가 없다.
    - ul 태그는 순서가 없는 리스트 정의에 사용
    - ol 태그는 순서가 있는 리스트 정의에 사용
```html
    <li>...</li>
    <li>...</li>

    <ul>
        <li>...</li>
        <li>...</li>
    </ul>
    <ul>
        <li>...</li>
        <li>...</li>
    </ul>

    <ol>
        <li>...</li>
        <li>...</li>
    </ol>
    <ol>
        <li>...</li>
        <li>...</li>
    </ol>
```

### 9. 제목 태그
- 웹페이지를 나타내는 제목
- 검색엔진이 웹페이지를 분석할 때 가장 중요하게 생각하는 태그
    - 안쓰면 정말 큰 손해
```html
    <title>제목</title>
```

### 10. 웹 페이지 구성 태그
- 본문과 본문을 설명하는 정보를 각기 다른 태그로 분리해서 정리
- 본문을 나타내는 공간은 body 태그로, 본문을 설명하는 공간은 head 태그를 사용
- 이 둘을 감싸는 하나의 태그 = html 태그
- 이 웹페이지가 HTML 로 만들어져있다는것을 표현하기 위해서 !doctype html 을 문서의 시작에 추가
```html
<!doctype html>
<html>
<head>
    ...
</head>
<body>
    ...
</body>
</html>
```


### 11. 링크 태그
- 링크 하는 태그는 특정 구역에 정박한다는 느낌으로 닻(anchor)을 내린다는 뜻으로 a태그를 사용
    - href 는 HypertextREFerence 의 약자로 링크를 넣어두면 된다.
    - target 은 링크를 클릭 했을 때 어떤 동작을 할 지 결정
    - title 은 이 링크가 어떤 내용을 담고 있는지 툴팁으로 보여줌
```html
    <a href = "링크", target = "_blank", title = "html5">하이퍼링크가 걸릴 무언가</a>
```

- 다음으로 할 일 
1. HTML태그 학습 : [링크]("https://tcpschool.com/html-tags/intro")
2. CSS 학습: [링크]("https://opentutorials.org/course/3086")
3. JS 학습: [링크]("https://opentutorials.org/course/3085")




--- 

# 그냥 개인 공부로 한다.
## 기본
- HTML : 그냥 웹을 보여주기 위한 언어일 뿐
- 구성
    ```html
    <Tag Attribute>Content</Tag>
    ```
    1. tag 는 opening 과 closing 으로 구성이 되어있으나 몇몇 태그는 closing 태그가 없는 경우가 있다.
    2. tag 는 attribute(속성)를 가질 수 있는데 이는 다음과 같이 구성된다.
        ```html
        Property="Value"
        ```
    3. tag 들은 중첩해서 사용이 가능하며 다른 태그안에 위치할 수 도 있다.
        ```html
        <TagA>Content<TagB>Content</TagB>Content</TagA>
        <TagA>Content<TagB>Content</TagA>Content</TagB>
        ```
        - 위처럼 작성을 할 수 는 있지만 적절히 열고 닫아야 깔끔하게 안쪽과 바깥쪽 위치에 있을 수 있다.
    4. 어떤 tag 들은 Content를 갖지 않을 수 있다 이를 빈 요소라고 한다
        ```html
        <img src="img주소" alt="대체TEXT">
        ```
    5. meta 로 작성하는 메타 데이터는 많은 종류가 존재한다.
        - [메타데이터 확인하기]("https://developer.mozilla.org/ko/docs/Learn/HTML/Introduction_to_HTML/The_head_metadata_in_HTML")

    6. CSS 와 JS 를 적용하기 위해서는 head 부분에 코드를 입력해주어야 한다.
        ```html
        <link rel = "stylesheet" href = "my-css-file.css">
        <!--
            link는 문서의 head부분에 위치하며 2가지의 Property를 취한다.
            문서의 스타일 시트를 나타냄(rel)과 동시에 스타일 시트 파일의 경로(href)를 포함한다.
        -->

        <script src = "my-js-file.js"></script>
        <!--
            script는 head 에 들어갈 필요는 없으나 </body> 태그 바로 앞, 문서 본문의 맨 끝에 넣는것이 좋다.
            JS 적용 전에 모든 HTML의 내용을 브라우저에서 읽었는지 확인하는것이 좋으며 엑세스 과정에서 JS가 아직 존재하지 않는 요소라 판단시 에러 발생 할 수 있음
            태그가 비어있다 보일 수 있지만 무조건 closingTag 를 사용해 닫아주어야 한다.

        -->
        ```
    7. html 태그에 lang 속성을 추가해 해당 문서의 언어를 설정해 검색 엔진에 효과적으로 색인화 될 수 있게 한다.


    5. 기본 구성
        ```html
        <!DOCTYPE html>
        <html>
            <head>
                <meta charset = "utf-8">
                <link rel = "stylesheet" href = "my-css-file.css">
                <title>Page Title</title>
            </head>
            <body>
                ...
                <script src = "my-js-file.js"></script>
            </body>
        </html>
        ```

## TAG
### 1. 제목 : h1 ~ h6 태그 
- 작은 숫자부터 큰 숫자로 점점 크기가 작아지는 것을 볼 수 있다.
```html
<h1>...</h1>
<h2>...</h2>
<h3>...</h3>
<h4>...</h4>
<h5>...</h5>
<h6>...</h6>
```
- 몇가지 관례가 존재
    1. 페이지 당 하나의 h1 을 사용 : 최상위 표제이며 다른 표제들이 이것의 밑에 위치
    2. 각 표제들은 계층적으로 올바른 순서로 사요
    3. 6개를 사용할 수 있지만 꼭 필요한게 아니라면 3개 이상 사용하지 말 것

### 2. 문단 : p 태그
- 문자의 문단을 포함하기 위함이며 일반적인 문자 내용을 나타낼 때 많이 사용
- 기본적으로 각 단락은 p 태그에 둘러싸여 있어야 한다.
```html
<p>This is content.</p>
```

### 3. 목록 : ul, ol, li 태그
- 목록을 나타내는 것은 항상 최소 두개의 요소로 구성된다.
    - 순서 없는 목록: ul 태그 (Unordered List)
    - 순서 있는 목록: ol 태그 (Ordered List)
- 목록 내의 각 항목은 li 태그 안에 놓여야 한다.
- 리스트 내부에 리스트를 입력하는 방법 또한 가능하다.
```html
<ul>
    <li>First List</li>
    <li>Second List</li>
    <li>Third List</li>
</ul>
```

### 4. 링크 : a 태그
- 웹을 웹으로 만들어주는 가장 중요한 요소
- 특정 컨텐츠를 a 태그로 감싸고 내부에 Property를 줘서 지정한다.
    - href = Hypertext REFerence 의 약자
    - title = 페이지에 포함된 정보 또는 웹에서 주의 해야 할 사항 등 링크에 대한 추가 정보를 포함
        - 커서 올려두고 있을때 따로 조그맣게 지정한 값이 나타남
    - 참고로 단순한 Text가 아니라 block 단위로도 감쌀 수 있다.
        - 이미지를 링크로 바꾸고 싶으면 a 태그 내에 넣어주면 된다.
- 주소의 시작은 https:// 같은 프로토콜 부분을 써주는것을 잊지 말아야 한다.
- URL 과 path
    - 같은 디렉토리 내에 위치한다면 URL은 단순한 이름만 입력하면 된다.
    - 하위 디렉토리 내에 위치한다면 URL은 해당 디렉토리와 함께 입력을 해줘야 한다.
    - 부모 디렉토리 내에 위치한다면 URL은 상위 디렉토리로 이동을 하는 .. 을 사용하여 입력을 해줘야 한다.
        - 두개의 점을 사용해서 상위로 이동이 가능하니 : ../../../A.html 이런것도 가능함
```html
<a href="이동하고자 하는 웹 주소">MOVE WEB</a>

<a href="이동하고자 하는 웹 주소" title="CHCKTITLE">MOVE WEB</a>

<a href="이동하고자 하는 웹 주소">
    <h3>HEAD</h3>
    <p>TEXT CONTENT</p>
</a>

<!--
    파일 구조 : ./
                TEST/
                    index.html
                    same.html
                    NEXT/
                        child.html
                TEST2/
                    parent.html
-->
<a href="same.html">같은 위치</a>
<a href="NEXT/child.html">하위 위치</a>
<a href="../TEST2/parent.html">상위 위치</a>
```

### 5. span 태그
- 컨텐츠에 추가적인 의미를 더하진 않지만 CSS 나 JS 를 적용해 무언가를 하고 싶을 때 사용
```html
<span style = "font-size: 32px; margin: 21px 0;">HEAD</span>
```

### 6. 중요 : em 태그
- 글에 중요 표기를 위해 이탤릭체로 표현한다.
- 단순 스타일을 위한 이탤릭체를 위해서는 span 태그에 CSS를 더하거나 i 태그를 사용 가능하다.
```html
<p>IT is <em>very</em> important content.</p>
```

### 7. 강조 : strong 태그
- 굵은 텍스트로 스타일 지정한다.
- 단순 스타일을 위한 이탤릭체를 위해서는 span 태그에 CSS를 더하거나 b 태그를 사용 가능하다.
```html
<p>IT is <strong>very</strong> important content.</p>
```

### 8. Italic, bold, underline: i, b, u 태그
- CSS가 완전히 지원되지 않는 경우에도 해당 스타일을 표현 할 수 있게 고안되었다.
1. i 태그 : 기울임꼴 -> 외래어, 분류학 명칭, 전문 용어, 생각 등 의 의미를 전달하기 위해 사용
2. b 태그 : 굵은 글씨 -> 주요 단어, 제품 이름, 주요 문장 등 의 의미를 전달하기 위해 사용
3. u 태그 : 밑줄 -> 적절한 이름, 잘못된 철자 등 의 의미를 전달하기 위해 사용
    - 밑줄 같은 경우는 하이퍼링크를 떠올릴 수 있기에 웹에서는 링크에만 밑줄을 긋는 것이 좋다.
    - 의미론적으로 u태그를 사용해야 한다면 CSS를 사용해 기본 밑줄을 웹에서 적합하게 변경할 수 있는지 고려

### 9. id 속성
- 사용하고자 하는 태그에 id 속성을 넣어줘야 한다.
- 일반적으로 특정 헤드라인데 연결하는 것이 타당하다.
- id 는 다른 곳에서도 연결해서 사용이 가능하다.
  <<<<<<24.01.11 여기까지 진행함: https://developer.mozilla.org/ko/docs/Learn/HTML/Introduction_to_HTML/Creating_hyperlinks>>>>>>
```html
<h2 id="Address">Addr</h2>
```