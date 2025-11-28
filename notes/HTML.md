맨 윗줄 DOCTYPE
열기태그 닫기태그
head 문서 정보
body 내용
h1 대표 제목
h1+p tab 
h1* 3 tab
h$* 6 tab
 - 실제 상황에서는 밑에서 a뒤 괄호는 없다고 생각
<a)</a> 어디론가 이동
<a) href=주소 target="_blank"> cilck</a> 새로운 창으로 열기
<a) href="./index.html"> click</a> 폴더에있는 파일로
<a) href="#move"> click</a> 화면에 있는 태그로
<a) href="./test.png" download> click</a> 파일을 다운 할 수 있게

<strong>hello</strong>
강조, 음성강조
<b>elit</b>
강조
<em>quisquam</em>
기울기, 음성강조
<i> autem </i>, excepturi
기울기

<!-- 주석표시 -->

### 페이스북 만들기
<head>

<title>Page Title</Title></title>
```html
<style>

body{

margin:0;

padding:0;

}

h1{background: #4267B2;

color: white;

padding: 10px;

margin: 0;

}

article{width: 500px;

border: 1px solid blue;

margin-top: 30px;

margin-left: 50%;

transform: translateX(-50%

);}

</style>

</head>

<body>

<header>

<h1>FaceBook</h1>

</header>

<section>

<article>

<img width="100%" src="src/a.jpg" alt="">

<p>Lorem ipsum dolor .</p>

</article>

<article>

<img width="100%" src="src/a.jpg" alt="">

<p>Lorem ipsum.</p>

</article>

<article>

<img width="100%" src="src/a.jpg" alt="">

<p>Lorem ipsum dolor.</p>

</article>

</section>

</body>

```

### 여러가지 기능

```html
</html>
<form action="" method ="get">
<label for="id">아이디</label>
<input type="text" name="아이디" id="id"/><br>

<input type="password" name="" id="" /><br>

<input type="date" name="" id=""><br>

<input type="time" name="" id=""><br>

<input type="range" name="" id=""><br>

<input type="color" name="" id=""><br>

<input type="radio" name="" id=""><br>

<input type="checkbox" name="" id=""><br>

```

### 아이콘 넣기
```html
<head>

<title>Page Title</title>

<link href="https://fonts.googleapis.com/css2?family=Material+Symbols+Outlined"

rel="stylesheet">

<style>

</style>

</head>

<body>

<h1>hello world</h1>

<span class="material-symbols-outlined">

favorite

</span>

<h1>hello world</h1>

</body>
```
### 애니매이션
```html
<style>

@keyframes 애니{

50%{

transform: translate(200px,0);}

100%{transform: translate(200px,200px);}

}

div{

background: red;

width: 100px;

height: 100px;

animation: 애니 2s;

transition: all 1s;

}

div:hover{

background: dodgerblue;

width: 200px;

height: 200px;

}

</style>
```
### 어려운 애니매이션
```
<style>

.btn{

border: 4px solid palevioletred;

border-radius: 4px;

padding: 30px 60px;

background: none;

color: palevioletred;

font-size: 32px;

position: relative;

overflow: hidden;

cursor: pointer;

transition: all 0.3s;

}

.btn:hover{

color: white;

border: 4px solid firebrick;

}

.btn::before{

content:"!";

position: absolute;

bottom: 0;

left:0;

width: 100%;

height: 100%;

background: palevioletred;

z-index: -1;

border-radius: 100px 100px 0px 0px;

height: 0px;

transition: all 0.3s

}

.btn:hover:before{

height: 120px;

background: firebrick;

}

</style>

</head>

<body>

<button class="btn">click me</button>

</body>
```