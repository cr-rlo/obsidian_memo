## Const & Let
- const와 let 예약어는 ES6에서 사용하는 변수 선언 방식
- let 예약어는 한번 선언하면 다시 선언 할 수 없음
- const 예약어는 한번 할당한 값을 변경할 수 없음
	- 단 객체 {} 또는 [] 배열로 선언했을 때는 객체의 속성과 배열의 요소를 변경할 수 있음
- 블록 유효 범위
- var 의 유효 범위는 함수의 블록 단위로 제한 됨. 흔히 함수 스코프라고 함
	- for 반복문에서 변수를 선언하면, {}로 변수의 유효 범위가 제한되지 않기 때문에 반복문이 끝나고 나서 변수를 출력했을 때 for 반복문의 마지막 결과 값이 출력됨
- const 와 let 블록 유효 범위
	- 변수의 유효 범위가 {} 블록 안으로 제한 됨

## 화살표 함수
- var a = () => { };
- 단순한 자바스크립트 표현식
	- () => 10+20; // { } 필요없음
- 함수 선언 방식
	- 복잡한 자바스크립트 선언문이 들어갈 경우에는 { }를 사용하여 구현
	- () => { print(); 
			log();
			return 10+20;};
- 전달 인자가 하나인 경우
	- 인자를 하나만 선언하는 경우 인자를 받을 때 사용하는 소괄호 생략 가능
	- const a = num => {
						return num * 10;};
	 const b = num => num * 10;
- this 바인딩의 변화
	- 화살표 함수에서 사용되는 this 바인딩은 기존 함수의 this와 다른 방식
	- 화살표 함수의 this는 함수를 선언할 때의 상위 스코프의 this로 바인딩 될 객체가 정해짐
- setTimeout에서의 this
	- 일반 함수에서 setTimeout에서의 this는 window
	- 그러나 화살표 함수에서는 상위 스코프의 this로 값이 바인딩 
- addEventListener에서의 this
	- addEventListener 두 번째 인자로 화살표 함수를 넣으면 this는 상위 스코프의 this를 가리킴
	- 그래서 ddEventListener 함수에서 this를 사용하는 경우, 화살표 함수가 아닌 일반 함수를 사용
	- 일반 함수로 정의된 addEventListener 함수의 this는 currentTarget을 가리킴
- 화살표 함수는 생성자 함수로 사용 불가 

## 향상된 객체 리터럴
- 기존 자바 스크립트에서 사용하던 객체 정의 방식을 개선한 문법
- 객체를 정의할 때 속성과 값이 같으면 축약이 가능
	- var language = 'javascript';
		var josh = {  // language: language,
		language};
	 console.log(josh); // {language: "javascript"}
- 속성에 함수를 정의할 때 function 예약어 생략
	- const josh = { 
		coding() {
	    console.log('Hello World'); }};
	 josh.coding(); // Hello World

## 스프레드 오퍼레이터
- 스프레드 오퍼레이터는 특정 객체 또는 배열의 값을 다른 객체, 배열로 복제하거나 옮길 때 사용
- 연산자의 모양은 ...
- /// obj 객체를 newObj 객체에 복제
	var obj = {
	  a: 10,
	  b: 20
	};
	var newObj = {...obj};
	console.log(newOjb); // {a: 10, b: 20}

## 템플릿 리터럴
- 자바스크립트에서 문자열을 입력하는 방식
- 기존에는 var str = '' 을 사용했으나 ES6에서는 백틱 사용
- 백틱을 사용하게 되면 여러 줄에 걸쳐 문자열을 정의할 수 도 있고, 자바스크립트의 변수를 문자열 안에 바로 연결할 수 있는 이점이 있음
- var expression = ` I love ${language}! `;

## 구조 분해 문법 Destructuring
- 구조는 변수의 이름을 넣고 오른쪽에 데이터 타입을 선언하는 선언 형식을 의미
- 구조 분해란 변수 선언 형식이 자유로워지는 것
	- var {a, b c} = obj;

## Promise
- 비동기 작업의 처리를 나타내는 객체
- 기존의 콜백 함수 방식의 문제점을 개선한 방식
- 콜백 지옥을 해결할 수 있음
- 에러 처리가 용이함
- 콜백 지옥
	- 비동기적으로 처리해야 할 작업이 둘 이상인 경우 처리해야 할 작업이 많아질수록 코드가 뾰족탑처럼 오른쪽으로 치우치는 Pyramid of Doom 형태
	- 프로미스를 사용하면 해결 가능
- 에러 처리
	- 프라미스를 통한 에러 처리는 `.then`, `.catch` 메소드로 간단히 정리 가능
- const promise = new Promise((resolve, reject) => {// executor}
- 프로미스 객체는 두 가지 프로퍼티(properties)를 가짐
	1. 상태(state): pending으로 초기화되며 resolve가 호출될 시 fulfilled로, reject가 호출될 시 rejected로 바뀜. 이 두가지 상태를 통칭하여 settled 상태
	2. 결과(result): undefined로 초기화되며 resolve(value) 메서드가 호출될 시 value로, rejected(error) 메서드가 호출될 시 error로 바뀜
- 프로미스 객체의 실행 함수는 단 하나의 resolve 또는 reject만 처리할 수 있음
- 프로미스의 reject는 resolve와 마찬가지로 인자에 어떠한 타입이 와도 상관없지만, Error객체와 함께 처리하는 것이 권장
- 프로미스 객체의 state와 result는 외부에서 접근할 수 없음
 1. then
	- .then 메서드는 첫 번째 인자로 resolved 상태를 처리하는 함수를 받고, 두 번째 인자로는 rejected 상태를 처리하는 함수를 받음
	promise.then(
	    function(result) {
        // resolved! },
	    function(error) {
        // rejected!});
 2. catch: 프로미스 객체의 에러를 처리할 때(rejected 된 경우) 사용됨
	 - .catch메서드는 .then 메서드의 첫 번째 인자에 null을 전달한 것과 마찬가지로 작동
3. finally
	- .finally 메서드는 프로미스가 settled 상태일 때 호출됨
	- promise 객체 정의 후, 작업 처리의 성공 및 실패 여부와 상관없이, .finally 메서드를 사용하기만 하면 무조건 호출되는 메서드임
	- .finally는 인자를 받지 않음

## Async & Await
- 비동기적 사고 방식에서 벗어나 동기적(절차적)으로 코드를 작성할 수 있게 도와줌
- async 함수는 함수의 앞에 async를 붙여주고 함수의 내부 로직 중 비동기 처리 로직 앞에 await을 붙여주면 됨
-  Promise 객체를 반환하는 API 호출 함수 앞에 await을 붙임

## Import & Export
- 자바스크립트의 코드를 모듈화 할 수 있는 기능
- 다른 파일에 있는 자바스크립트의 기능을 특정 파일에서 사용할 수 있는 것
- 자바스크립트는 기본적으로 변수의 유효 범위가 전역으로 잡히기 때문에 프로그래밍 패턴이나 별도의 모듈화 라이브러리를 사용해왔음
- 현재는 자바스크립트 언어 자체에서 모듈화 지원
- export 변수, 변수
	- 다른 파일에서 가져다 쓸 변수나 함수 앞에 export라는 키워드를 붙임
	- export된 파일은 import로 불러와 사용할 수 있음
- import { 불러올 변수 또는 함수 이름 } from '파일 경로';
	- export된 변수나 함수를 {}에 선언한 뒤 해당 파일이 있는 경로를 적어줌
- export var pi = 3.14;
- import { pi } from './math.js';
  console.log(pi); // 3.14
	- 위 코드는 math.js라는 파일에서 pi를 export하고 app.js 파일에서 import하여 콘솔에 출력하는 코드

## 널 병합 연산자 nullish coalescing operator
- 널 병합 연산자는 연산자의 왼쪽 피연산자가 null 또는 undefined일 때 오른쪽 피연산자를 반환하고, 그렇지 않으면 왼쪽 피연산자를 반환하는 논리 연산자
- 널 병합 연산자: ??
- function printTitle(text) {
	 let title = text ?? 'Cracking Vue.js';
	 console.log(title); }
  printTitle(); // Cracking Vue.js;

## 기본값 매개변수 default parameter
- 함수의 매개변수에 값이 전달되지 않았을 때 기본 값으로 설정하는 문법
- 함수를 정의할 때 매개변수의 우측에 =를 추가하고 함수에 값이 전달되지 않았을 때 설정할 기본 값을 defaultValue 위치에 저장
- function foo(param1 = 1, param2 = {}, param3 = 'korean') {
  console.log(param1, param2, param3);};
	foo(30, { name: 'amy' }, 'american'); // 30, { name: 'amy' }, 'american'
	foo(); // 1, {}, 'korean'
- ES6의 기본값 매개변수는 파라미터가 정의되지 않고 `undefined` 값인 경우에만 기본 값을 할당
- printFruit(0, false, null); 의 상황에서 0, false, null을 값으로 인식하여 기본값으로 대체되지 않음

## 옵셔널 체이닝 optional chaning
- 객체의 속성 값이 유효한지 검증할 수 있음
- 옵셔널 체이닝(`?.`) 앞의 평가 대상이 `undefined`나 `null`이면 에러가 발생하지 않고 `undefined` 를 반환
- const postcode = userInfo.address?.postcode;
	- underInfo 에 address 속성이 있는지 확인하고 postcode에 접근
- 옵셔널 체이닝은 메소드의 존재 여부를 확인하고 호출할 때도 사용할 수 있음
	- userInfo.getInfo?.();
- 널 병합 연산자 ?? 와 같이 사용하기
	- 옵셔널 체이닝과 널 병합 연산자를 사용하여 특정 속성의 갑의 유무를 판별하고 기본 값을 정의할 수 있음
	- const city = userInfo.address?.city ?? 'New York';
	- 위 코드에서 city의 값은 널 병합 연산자 ?? 의 왼쪽 항인 옵셔널 체이닝으로 검증한 객체의 속성 값이 null 또는 undefined 이면 널 병합 연산자 ??의 오른쪽 항인 New York이 기본 값으로 적용됨