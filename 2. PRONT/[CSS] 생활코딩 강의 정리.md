# 강의 정리

강의 주소: [WEB2 - 생활코딩](https://opentutorials.org/course/3086)

## CSS
- 웹페이지를 아름답게 만드는 방법
- style 태그 내에 코드를 입력하면 이게 css코드가 된다
```HTML
<!DOCTYPE html>
<html>
<head>
    <title>TITLE</title>
    <meta charset="utf-8">
    <style>
        ...
    </style>
</head>
<body>
    ...
</body>
</html>
```

### CSS 코드 작성
- a 태그에 대한 코드를 작성하고 싶다?
- 아래와 같은 형태로 씀
```html
    <style>
        a {
            color: red; // 색상을 바꿈
            text-decoration: none; // 밑줄 토글
        }
    </style>
```

- 이런식으로 선택자 내부의 프로퍼티들의 값을 변경해서 태그의 정보들을 변경 할 수 있다.
```html
    <style>
        Selector {
            Property : Value;
        }
    </style>
```