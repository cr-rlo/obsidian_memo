
## 스크립트
```<script>

document.getElemetById("one").innerHTML = "hi world";

</script>

```
### 스크립트 파일
`<script src="test.js`></script>

### 콘솔로그
consol.log("")
개발자 도구 콘솔로그와 거의 유사
### 코드구조
문은 세미콜론으로 구분
문은 값 연산자 키워드 명령어 표현식 등으로 구성
표현식(값으로 평가, 함수, key, index 등)

### 공백
공백 유무 상관 없음
병합하면 좋음

### 주석
// 로 표시 여러줄, 주석은 / * * /
코드를 보류하는 용도로 사용
코드에 대한 설명을 쓰기도 함
easter egg

### 엄격모드
코드 최상단에 "use strict";

### 변수
var, let, const 등(let x=0)
이름이 규칙
숫자로 시작할 수 없음
띄어쓰기 안됨
대소문자 구분
예약어 사용할 수 없음 (let let=0 불가능)
$,_ 을 제외한 특수문자를 사용할 수 없음
- let: 블록 레벨 스코프, 재선언 시 에러 o, 콘솔에서는 에러 x, 변경가능한 자료형
- const: 블록 레벨 스코프, 재선언시 애러 o, 콘솔에서는 에러 x, 변경 불가능한 자료형(상수)

## 연산
- &&는 곱(전체 조건이 참일 때 참) -> 조건 평가 연산자
- !는 부정
- = =는 동일한 값인지 비교(같을 때 참)
- typeof : 유형을 알려주는 연산자

## 프로퍼티 접근 연산자
1. 마침표 프로퍼티 접근 연산자
2. 대괄호 프로퍼티 접근 연산자
`let x={'one':1, 'two':2`}
x.one 또는 x['one']으로 접근 가능

## 관계 연산자
- 키만 가지고 판단(다른 언어는 아님)
예를 들면 index(key)만 가지고 판단
10 in {10, 20,3 0} -> false로 판정
왜냐하면 괄호 안의 index는 0, 1, 2이기 때문에

## 변수의 형태
- 원시타입: 하나의 값만 가짐(number, string, boolean, null, undefined, symbol)
		-> 변경 불가능한 유일한 값
- 참조타입: object(object, array, map, set), function
		-> 변경 가능

## 숫자
- 형태: 10, 20 ...
- 호출: 변수명 [10, 20 ..]은 안됨, x등 변수명으로 호출
- 10.toString()은 안됨 -> 소수점 때문에 ! 
- (10).toString()와 변수명.toString()은 가능함
- num.toFixed(): 버림
- number('10') -> 숫자 10으로
	parseInt()도 마찬가지, 더 자주 쓰임
	
## 문자열
```- ${변수명}
'hello world'.replace('hello', 'hi')` -> hi world
'hello world hello'.replace(/hello/g, 'hi') -> hi world hi 
```

## 논리값
- !![]  true
- !!{}  true
- !!" false
- !! 아무 문자라도 있으면 true
- [] array
-  x = [10,20,30,40]
	x.length -> 4
	x.forEach( x => console.log(x ** 2))
	 -> 제곱한 값들 도출
- [10,20,30,40].map(x => x+100) 새로운 array 생성
   -> [110,120,130,140]
- [].map(x=>x['age']) 데이터를 뽑아내는 용도
- array(100) -> [비어있음 x 100]
- array(100).fill(0) -> [0,0,0,0,0,.....]
- array(100).fill(0).map((value, index) => value + index) -> [0,1,2,3,....]

## 객체 {}
- 꼭 따옴표로 묶어야 하는 것은 아니지만 묶으면 혼동 x

## 조건문
- 조건문 true 일 때 실행
	if (true) {console.log('hello 1')}
		if(false){console.log('hello 1)} 실행 x
		else if(false){console.log('hello 2')} 실행 x
- let result = true ? 1 : 100;

## 반복문
- for (let i = 0; i < 10; i ++) {console.log(i)}

- let a = [10,20,30,40]; 
	// let a = 'hello';
	// let a = '19821'
	for (let i of a) {console.log(i);}

## 함수와 클래스
- function은 호이스팅이라는 기능. 선언하면 제일 위에 있다고 인식
- let은 호이스팅이 안됨. 선언 전에 사용하면 실행 x

## 콜백함수
- =>

## 클래스
- 클래스: 공장
- 인스턴스: 제품
	- ```
	  ```class Human{ attack(){console.log(공격!)}
					   defense(){console.log(방어!)}}
	daeun = new Human()
`daeun.attack()`

## 상속
```class 고급휴먼 extends Human { 마법(){console.log(파이어볼);}}
다은 = new 고급휴먼()
다은.마법()
다은.attack()
다은.defense()
``` 
- 고급휴먼이 human을 상속(extends)했기 때문에 human의 기능도 사용 가능

## 예외처리
- try{xxxx += 1000}
- catch(e){ console.log(애러)
		 console.log(e)} 혹은 console.error(e)
- finally{console.log(finally!)}

## 전개구문
let arr1 = [1,2,3,4];
let arr2 = [10,20,30,40];
let arr3 = [100,arr1,200,arr2,300]
arr 3 -> [100,Array(4),200,Array(4},300]
let arr3 = [100, ...arr1, 200, ...arr2, 300]
arr3 -> [100, 1, 2, 3, 4, 200, 10, 20, 30, 40, 300]

## Promise
- pending(대기상태) - resolve(해결) - fullfilled(성공)
- pending(대기상태) - reject(거부) - rejected(실패)