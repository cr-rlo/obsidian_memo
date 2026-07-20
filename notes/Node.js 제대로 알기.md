- 플랫폼의 구조와 기능들을 이해하기
## Node.js 란?
- 자바스크립트라는 언어를 알아듣는 프로그램
- 어떤 컴퓨터에 Node.js를 설치한다는 건, 해당 컴퓨터가 할 줄 아는 언어들의 목록에 자바스크립트를 추가한다는 의미
- 자바스크립트는 원래 브라우저라는 프로그램 안에서만 사용되던 언어
	- 자바스크립트는 HTML및 CSS 문서들과 함께 서버로부터 클라이언트로 전송된 다음, 클라이언트의 브라우저에서 실행되어 웹페이지의 요소들을 조작하거나 클릭 등에 의한 기능을 부여하는 데 사용되었음
## REPL
- Read - Eval - Print - Loop
	- 꼭 코드 파일을 따로 작성하지 않아도 터미널 등에 특정 언어의 코드를 입력하면 바로 결과가 나오는 환경 
	- 터미널에서 node를 열고 노드에서 바로 코드를 작성하여 결과보기 가능
## Promise와 async/await
- 비동기 코드를 보다 알아보기 쉽게 작성하는 데 사용됨
- 그 자체로 새로운 기능이 있는 것은 아니지만 콜백 함수로 짜던 코드를 보다 쉽게 작성하고 읽을 수 있도록 해줌
## 모듈
- 프로그래밍 코드를 한 곳에 작성하지 않고 기능과 목적별로 나누어 작성한 것
- 한 코드를 여러 곳에서 재사용할 수 있고 코드의 이해, 수정, 관리도 수월
## API
- 네가 이렇게 말하면 내가 이렇게 해줄게
- 두 소프트웨어가 서로 요청을 주고받을 때 각자 어떻게 응답과 요청을 주고받으면 되는지 메뉴판처럼 정해두는 것이 api
## RESTful API
- API의 다양한 형식들 중 오늘날 가장 널리 사용되는 것
- API를 통해 하는 일
	- create
		- POST 사용
		- 새 항목의 정보를 입력하려면, 용량이 클 수도 있는 정보를 담아보내야 하니 소포상자가 필요함
		- 해당 요청이 어느 리소스에 데이터를 추가하는 것인지만 명시하면 됨
	- read
		- 뭔가를 보여달라는 요청 -> 많은 정보가 필요 없음
		- GET 메서드 사용
		- 특정 조건으로 필터링하려면 query parameter 사용
		- 
	- update
		- PUT
			- 특정 항목의 정보를 전체적으로 대체할 때 사용됨
		- PATCH
	- delete
		- DELETE
		- 삭제할 항목의 식별자 넣어주면 됨
- URI는 어떤 자원에 관한 것인지 표현해야 하고 또 가능한 그것만 표현해야 함
- 그 외 어떤 일들을 하는지는 get, post, put, patch등의 메서드로 표현
- 요청을 보면 어떤 작업을 원하는지 바로 알 수 있음
- status codes
	- 성공적인 처리 success
		- 2xx 대 코드
	- client error
		- 4xx 대 코드
	- server error
		- 5xx 대 코드
		- 

## NODE.js의 stream 모듈 그리고 buffer
- stream
	- 대용량의 데이터를 다루기 위한 기술
	- 큰 데이터를 한 번에 옮기지 않고 작은 조각으로 나눠 물 흐르듯이 다루는 기술
	- import { Readable } from 'stream'
	- import { createReadStream } from 'fs'
	-  import { Writable } from 'stream'
	- import { Duplex } from 'stream'
		- 단방향만 가능한 redable과 writable과는 달리, Duplex 스트림은 읽기와 쓰기 모두 가능
	- import { createGzip } from 'zlib'
		- 데이터를 Gzip형태로 압축하여 내보내는 transform 스트림 생성
		- import { createCipheriv, randomBytes } from 'crypto'
			- crypto는 node.js에서 암호화 및 해시 기능을 제공하는 내장 모듈
		- 먼저 암호화의 알고리즘을 문자열로 설정한 다음
		- randomBytes 함수를 통해서 키와 초기화 벡터 생성
		- createCipheriv 함수에 algorithm, key, iv 이들을 인자로 전달해서 데이터를 암호화하는 transform 스트림을 생성
		- 압축 스트림과 암호화 스트림을 만든 후 이들을 읽기 스트림과 쓰기 스트림 사이에 파이핑( .pipe )
		- example 파일이 압축되고 암호화되어 새로운 파일로 저장됨
	- 



- buffer
	- 1. 옮겨지는 데이터 조각들이 일괄 처리를 위해 한곳에 쌓이는 것을 의미
	- 2. node.js에서 바이너리 데이터를 다루기 위한 객체
- Buffer
	- node.js에서 버퍼는 전역으로 제공되는 클래스
	- 따로 import할 필요없이 바로 사용하면 됨
	- Buffer from('')와 같이 문자열이나 배열 등을 매개변수로 받아서 buffer의 인스턴스를 생성 (버퍼형태로 바꾼 값)
	- 문자열의 각 문자가 16진수로 표현되어 버퍼로 담김
	- buffer.toString은 문자열 형태로 로그 출력
	- .alloc은 인자로 주어진 크기만큼의 버퍼 인스턴스 생성

## url, dns, util, os 모듈

- url
	- import { URL } from 'url'
	- URL 문자열을 파싱하고 조작하는 기능을 제공
	- URL 클래스의 인스턴스를 생성하여 기능들 사용
	- 생성자의 인자로는 다룰 URL의 문자열 값이 들어감
	- .protocol, .hostname, .origin, .port, .pathname .searchParams, .hash
		- 사용자가 직접 문자열을 파싱하지 않고도 URL의 인스턴스에 키로 접근하여 각각을 확인할 수 있음
	- .toString( ) 메서드를 사용하면 해당 인스턴스가 가진 값들에 따라 URL문자열을 반환
	- set, delete, append를 통해 매개변수의 값을 변경하고 지우고 추가할 수 있음
	- new URL( ) 인자로 첫 번째는 상대경로, 두 번째는 기본 URL을 넣어 생성하면 기본 URL에서 해당 경로로 들어간 결과로 만들어짐
	- import { fileURLToPath, pathToFileURL } from 'url'
		- 이 두 함수는 각각 파일 url을 경로로, 파일 경로를 파일 url로 바꿔줌
		- 파일 url은 웹 브라우저나 node.js같은 환경에서 로컬 파일 시스템의 자원에 접근할 때 사용하는 url 형식
		- 파일 경로는 운영 체제에서 파일이나 디렉토리의 위치를 나타내는 문자열
- dns
	- 도메인 이름 시스템에 관한 작업을 수행할 때 사용
	- 주로 네트워크 관련 작업이나 서버 관리, 디버깅 같은 상황에서 유용하게 쓰임
- util
	- 다양한 유틸리티 함수를 제공하는 내장 모듈
	- import { promisify } from 'node:util'
		- 인자로 전달된 콜백 기반 함수를 프로미스 기반으로 변환
	- import { inspect } from 'node:util'
		- 객체를 사람이 읽기 쉬운 문자열로 변환해주는 강력한 두고, 특히 디버깅이나 로깅에서 유용
	- import { deprecate } from 'node:util'
		- 어떤 함수가 문제가 있거나 새 함수로 대체되어 앞으로 사용되지 않도록 할 때 개발자에게 경고 메세지로 알리는 데 사용됨
- os
	- 운영체제와 관련된 정보 제공
	- import os from 'node:os';
	- 













	