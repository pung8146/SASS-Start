# sass(scss)

## 설치법

1. node 를 설치
2. 터미널에서 npm install -g sass (-g 는 전역 설치 어디서든 sass를 쓸 수 있습니다)
3. sass 바꿀파일이있는폴더/바꿀파일이름.scss:변경파일이있을폴더/변경된파일.css
4. sass --watch 바꿀파일이있는폴더/바꿀파일이름.scss:변경파일이있을폴더/변경된파일.css
   4.1 --watch를 붙이면 파일이 변경될때마다 자동으로 css도 변경해줍니다.
5. sass --style compressed style/main.scss:style/main.css
   5.1 --style compressed (압축의 의미) => 빌드압축하면 공백이런걸 다 지워줘서 용량적으로 효율이좋습니다.

## 주석

Sass(SCSS)는 CSS의 주석을 그대로 사용할 수 있습니다.
이는 주석의 시작과 끝 사이에 원하는 만큼 텍스트를 포함할 수 있는 형태인데, 이 외에도 Sass는 한줄의 텍스트만 포함할 수 있는 형태의 주석도 사용할 수 있습니다.

### 기본형태 /\* \*/

```
/*
여러줄 주석을 사용합니다
*/
```

### 한 줄 주석 //

```
// 매번 새롭게 '//' 를 사용해주어야합니다.
```

## 한 줄 주석의 이유

> '//'를 이용해 만든 한 줄 짜리 주석은 컴파일을 거쳐 만들어진 최종 파일에 반영되지 않는다. 반면 `/**/`를 이용해 만든 여러줄 짜리 주석은 반영된다. ** 기존 주석은 css 파일에 남아있습니다 **

## 중첩 규칙

> CSS 에서는 스타일을 정의하기 위해 선택자를 서로 다른 선언문에서 반복해서 써야하는 경우가 있다.

### 기존 css 방식

```css
div {
  width: 100px;
}
div p {
  color: white;
}
div p span {
  color: blue;
}
```

### Sass

```css
div {
  width: 100px;
  p {
    color: red;
    span {
      color: gold;
    }
  }
}
```

# 단축 속성

> 단축 속성은 여러가지 CSS 속성의 값을 함께 지정할 수 있는 속성으로,같은 주제를 가진 여러 공통 속성을 묶기 위해 정의하는 속성이다. Sass에서는 중첩을 이용해 단축 속성의 하위 속성을 그룹화 할 수 있다.** 접두어가 같은 태그들 **

```css
p {
  font: {
    family: sans-serif;
    size: 1em;
    style: normal;
    weight: 900;
  }
}
```

# & 기호로 상위 선택자 참조하기

ex: $hover, $active

# 변수 사용가능

```css
$main-color: red;

div {
  color: $main-color;
}
```

# 믹스인

> 믹스인을 만들때는 @mixin 지시자를 사용한다. 지시자 뒤에는 만들고자 하는 믹스인의 이름을 써준다 변수와 마찬가지

```css
1. 정의를 해줍니다 @mixin my-font {
  family: sans-serif;
  size: 32px;
  style: normal;
}

2. 사용 할 곳에 불러옵니다 h1 {
  @include my-font;
}
```

## 믹스인 인자

> 믹스인 정의 시 괄호와 함께 변수를 추가하면 인자가 정의되며,개수제한은 없습니다. 믹스인 호출 시에 인자를 전달하고 싶다면, 믹스인 이름 옆에 괄호와 함께 속성값을 추가하면 됩니다.

```css
// 1. 괄호와 함께 속성 값을 추가합니다.
@mixin my-font($font-color) {
  family: sans-serif;
  size: 32px;
  style: normal;
  color: $font-color;
}

// 2. 사용 할 곳에 불러옵니다
h1 {
  @include my-font(red;);
}

p {
  @include my-font(blue);
}
```

## 믹스인 인자 기본값

> 인자를 전달할 수도, 전달하지 않을 믹스인을 만들 수 있습니다.기본값은 인자로 정의된 변수 옆에 ':'를 쓰고 속성값을 써서 정의합니다.

```css
// 1. 기본값은 인자로 정의된 변수 옆에 ':'를 쓰고 속성값을 써서 정의합니다.
@mixin my-font($font-color, $bg-color: yellow) {
  family: sans-serif;
  size: 32px;
  style: normal;
  color: $font-color;
}
```
