## 바닐라 자바스크립트
- 아무것도 섞지 않은 순수한 자바스크립트 그 자체
- jQuery, React, Vue 같은 외부 도구(프레임워크, 라이브러리)를 전혀 쓰지 않고, 브라우저가 기본으로 제공하는 기능만 사용해서 코드를 짜는 것
- 프레임워크
	- 전체적인 흐름을 제어하는 틀, 개발자는 그 규칙 안에서 코드를 작성해야 함
- 라이브러리
	- 개발자가 필요할 때 꺼내쓰는 도구, 주도권이 개발자에게 있음
- jQuery VS React
	- jQuery: 라이브러리. 브라우저 간 문법차이 해결, DOM 요소를 직접 선택해서 수정하는 직접 명령 방식
	- React: 프레임워크, 라이브러리. 복잡한 UI를 효율적으로 관리하는 것, 화면 전체를 다시 그리지 않고 바뀐 부분만 계산해서 변경, UI를 독립된 부품 단위로 쪼개어 개발. 데이터 상태에 따라 화면이 자동으로 동기화
- JSon
	- 데이터를 주고받기 위한 텍스트 기반 표준 양식
	- 언어에 종속되지 않음
	- "key" : "value" 쌍으로 구성
	- JSON.stringify(obj): 객체 → 문자열 (전송용)
    - JSON.parse(string): 문자열 → 객체 (사용용)
- 바닐라 자바스크립트의 장점
	- 외부 도구를 불러올 필요가 없어서 속도가 압도적으로 빠름
	- 어떤 환경에서든 즉시 돌아가는, 환경의 제약이 없음
## HTML 문서의 시작과 Head의 모든 요소
- < !DOCTYPE html >
	- html5 표준 선언
	- 호환 모드 방지
	- css/레이아웃 깨짐 예방
	- 항상 문서 최상단
- < head >
	- 문서 전체가 제대로 표시되기 위한 준비 단계
	- 문자 인코딩을 지정해 화면 깨짐 방지
	- 뷰포트를 이용해 모바일 대응, 확대/ 잘림 방지
	- 제목으로 문서 정체성 부여
	- 최적화된 글꼴과 스타일시트를 불러와 보기좋은 화면
	- 단순 꾸밈이 아닌 브라우저 지침서
- < meta name = "viewport" content = "" / >
	- 모바일 환경에서 화면 크기와 배율을 맞추는 데 꼭 필요
- < title > </ title >
	- 브라우저 탭 제목
	- 북마크와 히스토리에도 저장
	- 문서의 정체성 표시 + 단순 장식이 아님
- < link rel = "" href />
## Body 레이아웃과 사이드바 뼈대
- < body > </ body >
	- 실제 화면에 보이는 모든 요소의 시작점
- < div class = "app" > 
	- 앱 전체 컨테이너
	- 이 div는 앱 전체를 감싸는 최상위 레이아웃 박스로 사용됨
	- css에서 .app 요소를 그리드 레이아웃으로 설정해 두었기 때문에 안쪽에 사이드바와 네비게이션 바, 본문이 그리드의 각 칸에 알맞게 배치됨
- < aside id= "sidebar" class= "sidebar" >
	- aside는 문서 보조 영역을 표현할 때 쓰는 의미론적 태그
	- 메인 컨텐츠는 아니지만 탐색, 관리 필수 영역
	- id= "sidebar"는 자바스크립트가 이 영역을 빠르게 찾을 수 있도록 해줌
	- class= "sidebar"는 css에서 스타일을 적용하게 함
	- 두 속성을 함께 쓰는 이유는 id는 한 문서에 하나뿐인 특정 요소를 지칭하기 위한 고유 식별자이고, class는 여러 요소에 공통적으로 적용할 수 있는 디자인 규칙을 위한 이름
- < div class= "inner" >
	- 사이드 바 내부 래퍼
	- 콘텐츠를 스크롤 가능한 영여긍로 묶음
	- css에서 padding + overflow 규칙 적용
	- 사이드 바 내용이 많아지면 스크롤바 생성
- < button id="collapseBtn" class="collapse=btn" title="collapse" > << < /button >
	- 사이드 바 토글 버튼(접기/펼치기)
	- id는 자바스크립트 이벤트 연결용
	- class는 버튼 스타일 적용
	- title은 마우스 오버 시 툴팁으로 표시되는 설명 (버튼 용도 설명으로 접근성 강화)
	- 내용 << 는 왼쪽으로 접힘을 직관적으로 표시
- < div class= "user-box" >
	- < div class = "avatar" > < /div>
	- < div class = "user-meta" > 
		- < strong> Guest < / strong > < small > guest@example.com < /small> < /div>
		- 사용자 정보를 표시하는 박스
		- 아바타 + 이름 + 이메일을 한 덩어리로 그룹화
	- 사이드 바 상단에서 계정 정보표시
- < div class="nav-items" >
	- 사이드바 상단 기능 버튼 모음
	- 여러 버튼을 세로로 그룹화
	- item 각각이 하나의 동작 단위 버튼
	- < div class= "item" id= "actionSearch">
		- < span > search < /span>
		- 검색버튼
		- 돋보기 아이콘 + search 텍스트
		- < span class ="right >
			- < span class ="kbd"> 아이콘 < /span>
			- < span class ="kbd"> K < /span>
			- 오른쪽에는 command K 단축키를 알려주는 작은 박스
			- 이 작은 박스를 css 로 스타일링 해 키보드 단축키처럼 보이게 함
	- < div class= "item" id= "actionSettings">
		- 설정 버튼 
		- < span > Settings < /span>
	- < div class= "item" id= "actionSettings">
		- 새 페이지 버튼
		- < span > New pages < /span>
	- 각 버튼에 id를 부여해 JS 클릭 이벤트 연결 가능
- < div class= "Group-title"> All pages < /div>
	- 문서 목록을 표시하는 구간
	- All pages라는 그룹 타이틀
- < div id= "docListRoot" class="doc-list">  < /div>
	- 비어있는 div 태그
	- Js로 문서 트리 렌더링 자리
	- 사용자가 만든 페이지들 계층 구조로 표시되는 핵심 영역
- < div  class="nav-items">
	- < div  class="item" id= "actionAddPages >
		- < span > Add a page < /span>
			- 새로운 루트 페이지를 추가할 수 있게 해줌
- < div  class="nav-items">
	- < div  class="item" id= "trashTrigger" >
		- < span > Trash < /span >
		- 휴지통 열기 버튼
		- 삭제 문서 진입점
		- 문서 삭제 시 즉시 제거 X -> 휴지통으로 이동
		- 사용자가 원하면 복원 가능
		- 사이드 바에 안전장치 역할로 배치
- < div id ="resizeHandle" class= "resize-handle" title="Drag to resize / Double click to reset" > < /div >
	- 사이드 바 폭 조절 핸들
	- JS에서 드래그 이벤트 감지 -> 사이드 바 크기 변경
	- title 속성은 마우스를 올리면 드래그 조절, 더블클릭 초기화 설명 보여주어 안내
	- CSS 얇은 세로줄. 약 4px -> 사이드 바 본문 경계선
- < button id ="sidebarPeekBtn" class="peek-btn" title="Open sidebar" > = < /button>
	- 사이드 바 다시 열기 버튼
	- 햄버거 아이콘 사용
	- 사이드바 접힘 상태에서만 표시
	- 모바일 좁은 화면에서는 사이드바가 자동으로 접히기 때문에 이 버튼이 사이드바에 유일한 진입점
	- 토글 버튼 덕분에 모바일 대응성 + 사용성 향상
## 사이드 바 옆에 붙어있는 네비게이션 바와 메인 에디터
- 상단에 위치해 있는 네비게이션 바는 현재 페이지 경로를 알려주고 오른쪽에는 즐겨찾기나 세 하위 페이지 같은 중요한 버튼들을 모아둔 공간
- 메인 컨텐츠는 우리가 작성할 문서가 실제로 보여지는 에디터 영역
- < header class = "navbar" > 
	- 상단 네비게이션 바
	- header태그는 문서 머리글, 네비게이션이라는 것을 알려주는 의미론적 태그
	- navbar클래스로 css에서 배경색, 높이, 정렬 스타일 구현
	- 항상 화면 상단 고정
- < main >
	- 문서 주요 콘텐츠 영역
	- 의미론적 태그 -> 본문의 핵심 의미 표시
	- 사이드바/ 헤더와 구분되는 메인 컨텐츠 담당
	- 안에 div class "doc-canvas"로 본문 컨테이너
		- 가운데 정렬 + 최대 폭 제한 -> 가독성 확보, 내부에 문서헤더, 본문 내용 순서로 배치
		- 안에 div class "doc-header"로 문서의 헤더 
		- 아이콘을 바꿀 수 있는 버튼
		- 타이틀 랩 클래스
			- 문서 제목, 메타 정보 영역
## HTML 구조의 아래쪽 오버레이 요소들- 휴지통 팝오버, 모달, 토스트보조 UI 정리
- 이 부분은 평소에는 화면에 보이지 않지만 특정 버튼을 누르거나 동작이 발생했을 때 화면 위에 떠서 사용자와 상호작용하는 중요한 요소들
- 

# CSS
## CSS 디자인 토큰과 다크 테마 변수
- :root
	- 문서 최상위 요소 html
	- 여기에 css 변수 정의하면 문서 어디서든 재사용 가능
	- 테마/ 색상 변경 시 한 줄만 수정해도 앱 전체 반영
- --변수
	- 값을 그냥 문자열로 저장
	- 실제로 사용할 때 .box{ color : var(--color); }
	- color 속성 덕분에 색상으로 인식
	- --bg = 색
		- 앱 전체에 일관된 색상 적용
	- --pane, --panel2, --panel3
		- 패널 배경 단계 구분
		- 사이드 바, 네비게이션 바, 팝 오버 등이 다른 색을 가지게해서 명도 차이로 층 차감
	- --text
		- 일반 텍스트 색상
	- --muted
		- 덜 중요하 설명 텍스트 색상
		- 주요색, 보조색 분리 -> 정보 계층 시각적 표현
	- --primary
		- 강조 색 -> 버튼, 선택 항목에 사용
	- --border
		- 패널 구분선 색상
	- --danger
		- 삭제, 경고 색상
	- --success
		- 완료 성공 색상
		- 직관적 색상 체계 -> 사용자 경험 강화
	- --shadow
		- 공통 그림자 규칙
			- 0 10px 30px (x=0, y=10px Blur=30px)
		- 반투명 검정 -> 입체감/ 부유감
	- --radius
		- 공통 border-radius
		- 버튼 박스 패널 모두 적용
		- 일관된 둥근 스타일 유지
	- --sidebar-w
		- 사이드바 기본 너비
	- --navbar-h
		- 네비게이션 바 높이
- 레이어 
	- --z-sidebar:1000;
		- 사이드 바 레이어
	- --z-dropdown:10150;
		- 드롭다운 레이어
	- --z-toast:10190;
		- 가장 위에 떠야하는 토스트 알림
	- 요소 별 레이어 우선 순위 변수화
	- 겹치는 UI충돌시 중앙에서 쉽게 조정가능
## Reset 스타일과 Body 기본설정
- *
	- 모든 요소에 적용한다는 의미
	- * { box-sizing:border-box; }
- content-box
	- 기본적으로 css의 박스모델은 content-box
	- content-box는 padding/border가 width밖으로 더해짐
	- 따라서 width를 100px로 정하면 실제 크기가 100px보다 커짐
	- 이를 막기위해서 최근에는 border-box가 선호됨
	- border-box는 padding/border가 width안에 포함
- html,body{ height:100%; }
- body{ margin:0 }
	- 기본적으로 8px의 여백을 가짐
	- 이를 초기화해서 레이아웃 틀어짐 방지, 정확한 레이아웃 기반 확보
- transition: background-color 0.25s ease, color 0.25s ease;
	- 테마 전환 시 색상 부드럽게 페이드
	- 라이트 다크 전환 시 번쩍임 방지
	- 0.25초 자연스러운 변화 -> 사용자 경험 향상
## APP 컨테이너와 Grid 레이아웃 구조
- .app
	- 최상위 컨테이너 < div class = "app" >
	- display: gird; -? 2차원 레이아웃
	- flexbox = 1차원 정렬/ 한 방향 정렬
	- gird = 2차원 레이아웃, 행+열 모두 적합
	- 구조: 2열(사이드바/메인) x 2행(네비게이션/본문)
	- grid사용 -> 자연스럽고 직관적 레이아웃
	- grid-template-columns: var(--sidebar-w) 1fr;
			- 너비 --sidebar-w
			- 2열 구조
			- 첫 열은 사이드바, 둘째 열은 남은 공간 전부( 1fr )
	- grid-template-rows : var(--navbar-h) 1fr;
		- 2행 구조
		- 첫 행은 네비게이션 바, 둘째 행은 본문 영역
- .sidebar
	- grid의 첫 번째 열 전체 차지
	- grid-column: 1;
		- 첫 번째 열에 배치
		- 첫 번째 열 고정
	- grid-row: 1 / span 2;
		- grid-row: 시작행 / span 차지할 칸수
		- 칸수의 크기는 grid-template-rows : var(--navbar-h) 1fr; 여기서 정한 크기를 따름
		- 1행부터 2행까지 세로로 확장
		- 첫 번째 행에서 시작해서 2칸 차지
		- 결과 -> 네비게이션 바 아래까지 이어져 화면 왼쪽 전체 차지
## peek 버튼과 상단 navbar 스타일링
- peek버튼은 모바일이나 작은 화면에서 사이드바를 다시 열 수 있는 손잡이 역할
- navbar는 현재 페이지 경로, 즐겨찾기, 검색, 설정 같은 주요 인터랙션을 모아놓은 영역
- .peek-btn
	- position: fixed;
		- 스크롤해도 항상 같은 자리 유지
	- 기본 상태: display:none; -> 숨김
- .sidebar .is-collapsed ~ .peek-btn { display: grid ;}
	- ~는 일반 형제 선택자
		- 같은 부모 안에서 뒤에 오는 형제 요소 선택
		- 즉, .is-collapsed 뒤에 오는 .peek-btn 선택
		- ~은 두에 오는 모든 형제를 선택하고 +는 바로 다음 형제만 선택
	- 사이드 바가 접히면 peek-btn 표시
	- sidebar안에서 .is-collapsed 클래스가 있을 때 뒤에 오는 .peek-btn에 display: grid 적용
- .navbar
	- grid-column: 2;
		- grid 2열 
	- grid-row: 1;
		- 1행 차지
	- position: sticky;
	- top: 0;
		- 스크롤해도 항상 상단에 고정
- .breadcrumbs
	- 현재 페이지 경로 텍스트
	-  letter-spacing: 0.2px 으로 글자 간격 벌려 가독성 높임
## main과 doc canvas - 본문을 담는 그릇
- 화면 오른쪽의 본문 영역을 실제로 감싸는 메인 컨테이너
- 그 안에서 문서를 보기 좋게 중앙에 배치하는 Doc canvas
- main
	- grid-column:2;
		- grid 2열 2행 차지(본문 영역)
		- 1열 사이드바 1행 네비게이션의 나머지 칸이 본문 영역
	- over-flow: auto;
		- 사이드바 네비게이션 바 항상 고정 유지
		- 본문만 독립 스크롤
		- 사용자는 항상 같은 탐색 위치 유지
		- grid로 큰 틀 분리 -> main 하나만 스크롤 컨테이너여도 레이아웃 전체가 자연스럽게 협력
- .doc-canvas
	- 본문 내용을 가운데로 정렬하는 역할
	- max-width: 940px; -> 넓은 화면에서도 글줄 제한
	- margin: auto; -> 좌우 중앙 배치
	- 줄이 너무 길면 가독성 저하, 피로 누적
	- 적절한 폭 제한으로 읽기 편한 문서 레이아웃
## user box와 action items
- 유저 박스는와 액션 아이템은 사이드바의 첫 인상을 좌우하는 중요한 요소들 
- .user-box
	- display : flex;
		- 아바타 + 사용자 정보 가로 배치
	- align-items: center;
		- 수직 중앙 정렬
	- gap: 10px 
		- 아바타와 텍스트 간의 간격 확보
	- .avatar
		- 사용자의 프로필 이미지를 대체하는 박스
		- box-shadow로 살짝 떠 있는 느낌 -> 사용자 포인트 강조
- .user.meta
	- display: flex;
	- flex-direction: column;
		- 이름+이메일 세로 정렬
- .nav-items
	- 사이드 바 액션 버튼 컨테이너
	- 아이템들을 묶어주는 역할
## document Tree 스타일과 계층 구조
- 계층적인 문서 구조
- .doc-list
	- 루트 문서들을 감싸는 박스
	- 내부에 .tree-row요소가 차례대로 쌓임
- .tree-row
	- 문서 하나를 나타내는 줄
	- display: flex; align-items: center; 
		- 아이콘 제목 버튼 가로 정렬
- .tree-row.dragover-top/bottom/inside 각각 정의
	- 드래그 위치 시각적 피드백 제공
	- 안정적 문서 이동 경험
- .children
	- 트리 구조 핵심 컨테이너
	- 시각적 효과: 트리가 계층적으로 자라남
	- 사용자 인식: 상위-하위 관계 직관적 파악 가능
## Dropdown 메뉴와 popover 스타일링
- .dropdown-btn
	- 트리 행 오른쪽 끝 ... 버튼
	- hover시 배경+글자 색 변화 -> 지금 활성화 기능 피드백 제공
- .dropdown-menu
	- body에 직접 붙는 떠 있는 메뉴 박스(포털)
	- position: fixed; -> 화면 기준 좌표 고정
- .popover
	- 고정 위치로 나타나는 패널
	- 드롭다운보다 넓은 폭
	- 배경 + 테두리 + border-radius+그림자
	- 드롭다운과 디자인 통일
	- 차이점은 더 넓은 공간 + 다양한 콘텐츠 수용 가능
## 화면 전체를 덮는 overlay UI 스타일링
- .overlay
	- 화면 전체 덮개 컨테이너
	- positon: fixed; inset: 0; -> 전체 화면 고정 덮개
		- inset은 top, right, bottom, left를 한번에 설정하는 단축 속성
		- inset: 0;은 상하좌우 전부 0;
	- display: none;
		- 열릴 때 display: gird; place-items:; center
			- 모달 창 정 중앙 배치
## settings 모달과 환경 제어 UI 디자인
- .settings-header
	- 설정 모달 최상단 헤더
	- display: flex; justify-content: space-between;
		- display: flex는 기본값 즉 가로로 나란히배치
		- justify-content: space-between;는 양끝에 붙이고 나머지 공간 균등하게 나눔
		- 좌우 배치 , 세로 중앙 정렬
		- 왼쪽에는 제목, 오른쪽에는 닫기 버튼
- .settings-modal .settings-grid
	- 모달 안의 그리드 배치
	- display: grid;
		- 설정 항목 2열 레이아웃
	- grid-template-columns: 1fr auto;
		- 왼쪽 영역 설명 영역, 오른쪽 컨트롤 요소 영역
		- 1번열 남은 공간 전부차지
		- 2번열 안에 있는 내용물 크기만큼 차지
	- align-items:center;
		- 열 안의 아이템들을 세로가운데 정렬
- .settings-modal .settings-row
	- 설정 항목 한 줄 
	- display: contents;
		- 불필요한 래퍼 박스 없애기 => 자식 요소 태그들만 남음
		- 자식들이 직접 flex, grid의 영향을 받게 됨
		- 내부 요소 (label, 버튼 등) grid cell에 직접 배치
		- display: contents; 가 없으면 래퍼가 grid cell을 차지해서 내부요소가 안에 갖히게 됨 
		- display: contents;가 있으면 래퍼가 사라지면서 내부요소가 직접 grid에 배치됨
- .switch
	- 테마 전환 UI 컴포넌트
	- display: inline- flex;
		- 체크박스+레이블 한 줄 배치
		- flex vs inline-flex;
			- flex는 블록처럼 한 줄 전체 차지
			- inline-flex;는 내용물 크기만큼만 차지
## confirm 모달, Toast 알림
- confirm 모달 
	- 사용자가 정말로 진행할지 묻는 역할
	- 삭제 같은 행동을 하기 전에 한 번 더 묻는 안전장치 역할
- Toast 알림
	- 짧게 정보를 알려주는 알람
	- 작은 피드백을 빠르게 보여주는 역할
- .modal-overlay
	- 화면 전체를 덮는 배경
	- position: fixed; inset:0;
		- 뷰포트 완전 가림
	- background: rgba(0,0,0,0.5);
		- 반투명 검정, 모달 집중 유도
	- display:none;
		- 기본값은 보이지 않게
		- 자바스크립트로 열릴 때 display: flex;
	- align-items: center; justify-content: center;
		- 모달 정중앙 배치
- .modal
	- 실제 확인 창(콘텐츠 박스)
	- width: min(420px, 90vw)
			- 크기 max-width: 420px, 좁은 화면 90%까지 축소
- toasts
	- 화면 우측 하단 알림 컨테이너
	- position: fixed;
		- 브라우저 창 오른쪽 아래 항상 고정
	- display: flex; flex-direction: column;
		- 알림 여러 개 일 때 세로 차곡차곡 쌓임
## 에디터 헤더 툴바 본문 스타일
- 문서 편집기 영역
- 에디터 영역
	- 문서 아이콘과 제목을 담는 컨테이너
	- 글꼴 스타일과 블록 포맷을 바꿀 수 있는 툴바
	- 실제 글을 작성하는 본문 편집 영역
	- 메타 정보를 표시하는 작은 텍스트
- .doc-header
	- 아이콘+제목 헤더
	- 아이콘과 제목이 나란히 배치되는 컨테이너
	- display:flex;
		- 가로 배치
	- align-items: center;
		- 아이콘 + 입력창 수직 중앙 정렬
		- 문서 헤더가 깔끔하고 직관적인 레이아웃
- .title-wrap
	- 제목 + 메타 정보 컨테이너
	- flex: 1;
		- 남은 공간을 전부 차지하라 는 의미
		-  가로 공간을 유연하게 차지
	- min-width: 0;
		- 기본적으로 flex 아이템은 내용물보다 작아질 수 없음
		- 하지만 이 속성을 통해 내용물 보다 작아질 수 있음
		- 따라서 텍스트가 길어도 영역 안에서 줄어듦 
		- 텍스트가 길어도 삐져나오지 않음
		- 너무 넓게 밀리는 것 방지
		- 제목 영역이 적절히 확장/ 축소되며 안정적 레이아웃 유지
- .title-input
	- 문서 제목 입력창
	- all: unset;
		- 브라우저 기본 스타일 제거
		- 폰트 사이즈와 굵기 설정으로 큼직하고 굵은 제목다운 느낌
	- border-bottom: dashed transparent;
		- dashed: 테두리를 점선 형태로 설정
		- transparent: 테두리의 색상을 투명하게 설정
		- 평소에는 안보임
		- focus 시 강조선 나타나 집중 효과
- .title-input:focus
	- border-bottom-color: var( );
	-  focus 시 강조선 나타나 집중 효과
- .meta
	- 문서 부가 정보 영역(예: 마지막 수정일)
	- 필요한 정보를 전달하면서도 본문 흐름 방해 X
- .toolbar
	- 포맷팅 도구 상자(굵게, 기울임, 제목, 리스트 등 설정)
	- positon: sticky; top: 8px;
		- 스크롤해도 화면 상단 근처에 고정
	- display: flex; flex-wrap: wrap;
		- 가로배치
		- flex-wrap: wrap;은 레이아웃에서 아이템들이 한 줄에 다 들어가지 않을 떄, 다음 줄로 자연스럽게 줄 바꿈
		- 기본적으로 display: flex;의 아이템들은 가로 너비가 부족하더라도 한 줄에 억지로 구겨넣으려는 성질이 있음(nowrap)
- .tbtn
	- 툴바 안에 있는 개별 버튼들
- .tbtn:hover
	- hover시 배경 글자색 변화 -> 클릭 가능 피드백 제공
- .editor
	- 실제 글 작성 영역
	- min-height: 600px
		- 빈 페이지여도 충분한 작업 공간 확보
		- padding으로 여백 확보, 가독성 확보
	- transition: border-color 0.15s ease, box-shadow 0.15s ease;
		- border-color: 트랜지션 대상 속성
		- 0.15s: 지속 시간
		- ease: 가속도 곡선 -> 느리게 시작해서 빨라졌다가 다시 느려짐
			- 가장 자연스러운 가속도 설정
			- 처음과 끝이 부드럽게 연결됨
- .editor :where()
	- :where( )은 .editor안에 있는 특정 요소를 모두 선택한다는 뜻
	- 특징으로 괄호 안에 무엇을 넣든 CSS우선 순위가 가장 뒤로 밀려난다는 점
	- 비슷한 속성으로 :is( )가 있는데 이는 우선순위를 계산할 때 괄호 안에 나열된 것들 중에서 가장 높은 점수를 가진(우선순위를 가진) 요소를 기준으로 전체 우선 순위가 결정된다는 뜻
- . editor pre
	- editor 안 pre 태그 선택
	- pre 태그는 HTML 기본 태그인 < pre >
		- 이 태그 안 택스트는 작성된 공백과 줄바꿈이 그대로 유지되며, 보통 고정 폭 글꼴로 표시됨
	- 코드 블록
## 미디어 쿼리로 완성하는 반응형 디자인
- 노션 사이드바 프로젝트는 pc, 태블릿, 모바일 환경에서 모두 자연스럽게 동작해야 하므로 다양한 화면 너비를 기준으로 스타일을 조정
- 이를 위해 사용되는 것이 미디어 쿼리
	- CSS에서 @media 조건을 작성하면 특정 화면 크기일 때만 스타일이 적용되도록 만들 수 있음
	- 큰 화면 전용 레이아웃
	- 작은 화면 전용 레이아웃
- @media (min-width: 1280px){ 
	- 큰 화면을 위한 스타일
	- :root {  } }
		
		- --sidebar-w: 300px;
			- 사이드 바 폭 300px로 넓게
		- --navbar-h: 68px
			- 네비게이션 바 높이 60px
	- .tilte-input{  }
		- 제목 입력창 크기
	- .doc-canvas{  }
		- 본문 캔버스 최대 폭 설정
		- 한 줄에 더 많은 글자
		- 넓은 화면에서 여유로운 레이아웃 제공
- @meida (max-width: 768px){ }
	- .doc-canvas{}
		- max-width: 880px;
			- 본문 폭 880px로 축소 
	- 툴바 버튼 gap과 padding 조정으로 화면 최적화, 가독성 유지
- @media (max-width: 768px){}
	- .navbar padding 축소 -> 답답함 방지
	- .breadcrumb 글자 축소
	- .btn들 패딩과 폰트 사이즈 줄여서 공간 절약
	- .toolbar top 위치 조정으로 sticky위치 조정
	- .editor 최소 높이 조정으로 작은 화면 최적화
	- .peek-btn은 사이드바가 접힌 상태에서 열 수 있는 버튼
		- 이 버튼의 위치, 크기 조정으로 손가락으로 누르기 쉽게 
- `#sidebar` 
	- sidebar 아이디 속성을 가진 요소
	- 높은 우선순위
	- 사이드 바가 접히면 navbar안에 햄버거 버튼을 보여주고
	- 원래 떠있던 peek 버튼은 숨기는 로직
	- 즉 큰 화면에서는 Peek버튼으로 사이드 바를 열지만
	- 작은 화면에서는 navbar 햄버거 버튼만 사용
	- 

# 본문 편집기와 상태 동기화(자바스크립트)
## 앱 상태 설계 - STORAGE_KEY, defaultDocs, state
- const STORAGE_KEY = " "
	- 저장키 설정
	- 우리 앱은 사용자가 만든 페이지들을 브라우저에 저장해둬야 다시 열었을 때 그대로 복원할 수 있음
	- 브라우저는 localStorage 라는 작은 키 값 저장소 제공
	- 여기서 키는 우리 앱만의 라벨 -> 앱 고유 식별자
		- 프로젝트 명과 버전을 조합한 고유 문자열을 상수로 고정
		- 다른 앱과 라벨 충돌 방지
	- 절대 바뀌면 안되는 값이라 const로 선언
- const defaultDocs = [ ]
	- 기본 문서 데이터
	- 앱 첫 실행 시 연습용 페이지 제공
	- 사용자는 구조 이해 + 즉시 클릭과 편집 가능
	- 각 문서 속성 { } -> 첫 번째 객체
		- id: "welcome" -> 개발자 이해용 고정 id, 고유 식별자
			- 실제 생성 로직에서는 UID로 임의 아이디를 만들지만 기본 데이터는 이해하기 쉬운 이름형 아이디를 써도 무방
		- title: 문서 제목
		- icon: 아이콘/ 이미지
		- parentId: null -> 부모 관계 표시
			- null로 최상위 문서 임을 표시(root)
		- content: < p> 첫 문서 - < /p>
			- 간단 안내문
		- starred: false -> 별표, 즐겨찾기 표시
		- order: 0 -> 형제 순서
			- 0은 같은 형제들 중 첫 번째 순서
		- createdAt: Date.now() - 86400000
			- Date.now에서 밀리초를 빼서 어제 만들고 1시간 전에 수정한 것처럼 보이게 하는 연출
		- updateAt: Date.now() - 3600000
	- const 사용 이유
		- 이 변수 자체를 다른 배열로 바꾸지 않는다는 약속
		- 내부 원소는 상태 로딩 후 복사본으로 사용
		- 언제든 초기 상태로 복원 가능
	- { } -> 두 번째 객체
		- id: "guides"
			- guides 페이지 
		- parentId: null -> 부모 관계 표시
			- null로 최상위 문서 임을 표시(root)
		- starred: true -> 별표, 즐겨찾기에도 나타남
		- content: "< h2 > guide index " < /h2 >
			- H2와 UI 조합, 간단한 목차 포함
			- 자식 페이지들과 연결감 형성
		- order: 1;
	- { } -> 세 번째 객체
		- id: "setip"
		- parentId: "guides" -> guides의 자식 페이지
			- 부모 자식 관계는 단지 문자열 ID로 연결함
			- 별도의 트리 구조 불필요
- const state = { }
	- 실행 중 상태를 담는 state 그릇
	- 화면은 state를 참고해서 그려지고 사용자의 행동은 state만 변경함
	- 이렇게 단방향으로 정하면 언제든 무엇 때문에 이런 화면이 되었나를 스테이트 변화 추적만으로 알 수 있음
	- state는 앱 전역에서 공유되는 단일 상태 컨테이너
	- { docs: [] ;
		- 살아있는 모든 문서 리스트 배열
		- 초기 부팅 때 default docs 복사해서 채움
		- 이후에는 CRUD 동작이 docs 수정
			- create, read, update, delete
	- trash: [];
		- 휴지통 역할을 하는 프로퍼티
		- 빈 배열로 설정
		- 삭제는 진짜 삭제가 아니라 이 배열로 이동시키는 방식으로 구현해 복원 기능 지원
	- expanded: { };
		- expanded 프로퍼티의 객체는 펼쳐진 트리 노드들을 기억 상태 저장
		- 키 = 문서 id/ 값 = true
		- 리렌더 후에도 열림 상태 유지
	- activeId: null;
		- 현재 표시 중인 문서의 id
		- 초기값은 null
		- 라우팅 시 갱신
		- 체목 입력칸, 브레드크럼, 에디터 -> activeId 기준 출력
	- isMobile: matchMedia("(max-width:768px)").matches,
		- matchMedia는 브라우저에게 화면 너비가 최대 768px인 상태를 감시해줘라고 요청하는 함수 -> 조건이 바뀌는 순간 미리 작성해 둔 자바스크립트 함수 실행
		- .maches는 그 요청에 대한 현재 결과를 확인 -> true/ false로 값 반환
	- };
## localStorage와 UID로 상태 보존
- 새로고침 후에도 사용자가 만든 문서가 사라지지않고 유지되는 것이 핵심
- localStorage
	- 앱이 일종의 기억력을 가져야하는데 그 기억을 담당하는 것
	- 제한: 문자열만 저장 가능 -> 자바스크립트의 객체와 배열을 그대로 담을 수 없음
	- 해결: 저장 = JSON.stringify(문자화) / 불러오기 = JSON.parse(객체화)
	- load/ save 함수가 이 과정 관리
- function load( ){}
	- 앱이 시작되면 가장 먼저 실행되는 함수
	- const raw = localStorage.getItem(STORAGE_KEY);
		- getItem(): 데이터를 가져오겠다는 자바스크립트의 약속된 명령어
		- 앞서 정의한 STORAGE_KEY이름의 데이터 가져옴
		- 없으면 null 반환
		- if (!raw) {}
			- 조건문으로 초기화 처리
			- state.docs = defaultDocs.slice( );
				- 기본 문서 복사해 state.Docs에 넣음
				- slice를 쓰는 이유는 원본을 보호하기 위해서
				- 그냥 =으로 대입하면 원본과 복사본이 한 몸이 됨(참조)
				- slice를 통해 원본의 내용물을 똑같이 베껴서 새로운 독립적 배열 생성 -> 초기 데이터 불변
			- state.trash = [];
				- trash 상태는 항상 빈 배열로 시작
			- return;
	- const data = {  };
		- 데이터가 있는 경우 
		- JSON. parse( raw ); 
			- 문자열을 다시 객체로 복원
		- state.docs = data.docs || defaultDocs.slice();
		- state.trash = data.trash || [];
		- state.expanded = data.expanded || {}
		- state.activeId = data.activeId || null;
			- 복원된 객체 속성들을 state에 채움
			- ||( OR 연산자 )는 해당 필드가 없는 경우 기본값을 사용하라는 의미 
	- catch(e){ }
		- 안전망
		- 예기치 못한 에러가 발생한 경우 대비
		- console.warn( );
		- state.docs = defaultDocs.slice();
		- state.trash = [];
		- 콘솔에 경고 문구 출력 -> 기본 문서만 로드
		- 저장소가 망가져도 앱은 정상적으로 돌아갈 수 있게함
- function save( ){}
	- save 함수
	- const data = {
	- docs: state.docs,
	- trash: state.trash,
	- expanded: state.expanded,
	- activeId: state.activeId,
	- };
	- 현재 state에 담긴 데이터를 하나의 객체 data 객체로 모음
	- 문서 목록, 휴지통, 펼친 노드, activeId 모두 포함
	- 이렇게 한 덩어리로 저장해서 일관성을 보장함
	- 스냅샷 방식 -> 일부만 저장되는 불일치 방지
	- localStorage.setItem( STORAGE_KEY, JSON.stringify(data));
		- 마지막 단계로 setItem 호출
		- data 객체를 문자열로 변환하여 localStorage에 저장
		- 변환 이유는 객체를 안전하게 문자열로 저장하기 위해 
- function uid( ){ }
	- 새로운 문서를 만들 때 필요한 임시 아이디를 생성하는 함수
	- return Math.random( ).toString(36).slice(2, 11);
		- Math.random()으로 0~1의 난수 반환
		- toString(36)으로 36진수 반환 -> 숫자 알파벳 혼합 문자열
		- slice(2, 11) -> 앞에 불필요한 0. 제거 후 9자리 추출
## childrenOf 부터 isDescendant까지
- 부모와 자식 관계를 통해 트리 구조를 형성하도록 돕는 함수들
- 노션에서 중요한 점은 단순한 리스트가 아니라 계층 구조라는 점
- 폴더 안에 또 다른 페이지를 만들 수 있고 그 페이지 아래에도 다시 서브페이지를 만들 수 있음
	- 문서들 사이에 연결관계를 개선해주는 함수들 필요
- function childrenOf(pid) { }
	- return state.docs
	- .filter( (d) => d.parentId === pid )
		- 필터 메서드는 전체 문서들 중 parents 아이디가 입력받은 PID와 같은 것만 남기는 단계
	- .sort(( a,b) => a.order - b. order || a.title.localeCompare(b.title ) );
		- 자식 문서를 순서대로 정렬 
		- 첫 번째 기준으로 비교해보고, 만약 값이 같다면 두 번째 기준으로 순서 정함
		- 기준들은 모두 숫자를 뱉는다
		- a.order - b. order
			- 결과가 0이 아니면 숫자가 작은 것이 앞으로 옴
			- 결과가 0이면 자바스크립트에서는 false로 취급하기 때문에 다음 기준에 따라 정렬
		- a.title.localeCompare(b.title)
			- localeCompare은 글자의 순서를 숫자로 바꿔줌
			- a.title과 b.title 비교
			- a.title이 b.tiltle 보다 앞 순서면 음수가 결과 값으로 나오고 순서 그대로 유지
			- a.title이 b.title보다 뒷 순서일 때 양수가 결과 값으로 나오고 둘의 순서 바굼
			- 둘이 같은 글자인 경우 0을 결과 값으로 반환하고 순서 유지

	- 특정 부모 id의 자식 문서 배열 반환
	- 특정 부모 요소 pid에 속한 자식 요소들을 찾아내기 위해 정의된 함수
	- childrenOf : ~의 자식들 이라는 뜻으로 함수의 역할을 직관적으로 표현
- function findDoc( id ){ }
	- return state.docs.find((d) => d.id === id );
		- 특정 id를 가진 문서를 직접 반환
		- array.find()는 조건에 맞는 첫 번째 요소만 반환
		- id는 고유 -> 정확히 하나만 찾아옴
		- 편집 / 삭제 시 대상 문서에 즉시 접근
	- id를 줄테니 그 문서를 찾아와 라는 명령
	- state.docs는 현재 앱이 가지고 있는 모든 문서 데이터가 담긴 배열(목록)
	- .find( )는 자바스크립트 배열의 내장 함수로 조건에 맞는 첫 번째 요소를 찾아줌
	- (d) => d.id === id
		- 찾기 조건
		- 목록에 있는 각 문서 (d)를 하나씩 꺼내어 확인
		- 그 문서의 ID(d.id)가 내가 찾으려는 ID(id)와 일치하는지 확인
- function maxOrder( pid ) { }
	- const kids = childrenOf(pid);
	- return kids.length ? math.max(...kids.map( ( k ) => k.order ) ) + 1 : 0;
	- 특정 부모(pid) 아래서 새로운 문서를 추가할 때 그 문서의 order값을 얼마줄지 계산
	- 기존 문서들보다 뒤에 배치하기 위해 가장 큰 번호 +1을 해주는 로직
	- const kids = childrenOf(pid);을 통해 해당 부모(pid)에 딸린 자식 문서들만 모아 kids라는 리스트 만들기
	- kids.length ? math.max(...kids.map( ( k ) => k.order ) ) + 1 : 0;
		- 자식이 있다면 ? 뒤 복잡한 계산식 실행
		- 자식이 없다면 : 뒤에 0 반환
		- math.max(...kids.map( ( k ) => k.order ) ) + 1 
			- ...
				- 스프레드 연산자
				- 리스트를 낱개로 펼쳐줌
				- Math.max는 리스트 통째가 아니라 낱개 숫자들을 인자로 받기 때문
			- kids.map( ( k ) => k.order )
				- 자식들 목록에서 order값만 뽑아 숫자 리스트로 만듦
				- .map은 배열의 첫 번째 아이를 꺼내서(k)
				- 그 배열의 주머니에서 order값만 꺼내 새로운 리스트에 담ㅇ므
				- 그를 두번째, 세번째 끝까지 반복
				- 결국 숫자만 남은 리스트 반환
			- Math.max(...)
				- 이 코드는 배열을 계산하지 못하고 낱개 숫자만 계산 가능
				- 따라서 스프레드 연산자 사용
				- 펼쳐진 숫자 중 가장 큰 값 찾기
				- 그 값에 +1을 더해 다음 순서인 숫자 만들기 

- function existsInDocs(id){ }
	- return !!findDoc(id);
	- 주어진 id가 문서 목록에 존재하는지 확인
	- 반환값 -> true/ false
	- !!은 이중 부정 연산자
	- !의 반대를 의미하므로 데이터가 있으면 true 없으면 false 반환
	- 그냥 findDoc(id);를 쓰지않고 이중 부정 연산자를 붙이는 이유는 붙이지 않으면 객체 덩어리가 반환되므로 우리가 원하는 true/ false만 반환받기 위해
- function isDescendant(id, maybeAncestorId){ }
	- id
		- 자손인지 확인하고 싶은 문서의 ID
	- maybeAncestorId
		- 부모/ 조상 ID
	- if ( !id || !maybeAncestorId ) return false;
		- 두 아이디 중 하나라도 없으면(잘못된 값이면) false를 뱉고 종료
	- let cur = findDoc(id);
		- 현재 문서 cur을 먼저 찾음
		- 특정 아이디를 갖는 문서 직접 반환
		- 여기서 부터 위로 조상을 찾아감
	- while (cur && cur.parentId){ if (cur.parentId === maybeAncestorId ) return true; cur = findDoc( cur.parentId ); } return false;
		- while (cur && cur.parentId)
			- 현재 문서가 존재하고 그 문서에 부모가 있는 조건을 모두 만족할 때만 { } 안 내용 실행 
		-  if (cur.parentId === maybeAncestorId ) return true;
			- 올라가다가 부모 아이디가 우리가 찾던 조상 아이디(maybeAncestorId)와 일치하 true 반환
		- cur = findDoc( cur.parentId );
			- 일치하지 않으면 한단계 더 위의 부모로 이동해서 다시 검사
			- 조상이 아니라면 내 부모를 현재의 나(cur)로 바꿔치기 하는 것
			- 
		- return false;
			- 최상위 부모까지 다 올라갔는데도 목표 아이디를 못 만났다면 조상 아님이라는 뜻으로 false 반환
	- 어떤 문서가 다른 문서의 후손인가 여부 감시
## create, update, delete, restore 문서 생애주기 설계
- CRUD 구현
- findDoc같은 도우미로 파일을 읽어오고 화면 렌더러가 state를 곧장 읽기 때문에 CRUD의 R은 자연스럽게 해결
- 새로운 문서 만들기 - create
	- 먼저 부모 지정 필요
	- 어느 부모 밑에 둘지 결정
	- 형재 순서 order
	- 같은 부모 안에서 몇 번째 위치인지 지정
- function createDoc({ title = "Untitled", parentId = null, afterId = null }) {
	const id = uid();
	- 제목, 어느 폴더에 넣을지, 어떤 문서 바로 뒤에 붙일 것인지 결정
	- uid 함수로 고유한 번호 생성해 id라는 변수에 저장
	let order = maxOrder(parentId);
	- 아무런 지시가 없다면 새 문서는 맨 아래에 붙음
	- maxOrder을 통해 가장 마지막 순서 번호를 따옴
	if (afterId) {
	- 그러나 만약 특정 문서 뒤에 넣어 달라는 요청이 있다면
	const sibs = childrenOf(parentId);
	- 같은 층에 있는 형제 문서들을 모두 불러옴
	- afterId가 몇 번째 칸에 있는지 알아내려면 전체 목록(sibs)를 확인해야 함

	const idx = sibs.findIndex((s) => s.id === afterId);
	- 기준이 되는 문서 (afterId)가 몇 번째 인덱스(idx)에 있는지 찾음

	order = idx >= 0 ? sibs[idx].order + 0.5 : order;
	- 순서 번호에 0.5를 더해서 그 사이에 끼워 넣음
	- idx는 아까 findIndex로 찾은 기준문서(aftrerId)의 위치
	- afterId로 넘겨준 문서가 목록에 존재한다면 idx는 0,1,2..등이 될 것이므로 ture -> ?뒤 식 계산
	- 존재하지 않는다면 처음에 maxOrder로 받아두었던 order값을 그대로 사용하겠다
	- sibs[idx]는 sibs 형제 문서들의 배열 리스트에서 특정 인덱스를 가진 객체 덩어리
	
	}

	const doc = { id, title, icon: "", parentId, content: "", starred: false, order, createdAt: Date.now(), updatedAt: Date.now(), };
	- doc이라는 객체 생성
	- 위 속성들을 가진 객체
	- 여기서 order값에 위에서 만들어둔 값이 들어감

	state.docs.push(doc);
	- 새로운 문서 덩어리를 전체 문서 창고에 집어넣음

	normalizeOrders(parentId);
	- 아까 1.5처럼 지저분했던 문서를 정수로 다시 예쁘게 정렬

	save();
	- 저장
	return id;}
	- 이 함수를 부른 사람에게 새로 만든 문서의 아이디 값을 알려주고 종료
	- 라우터가 즉시 해당 문서로 이동하도록 할 때 사용됨

- function updateDoc( id, patch ){  }
	- const d = findDoc(id);
	- if (!d) return;
	- Object.assign(d, patch, { updateAt: Date.now( ) } );
		- Object.assign은 여러 객체를 하나로 합치는 도구
		- Object.assign(대상, 소스1, 소스2...)
		- 대상에 소스 들의 내용을 차례대로 부어 넣음
		- d는 현재 수정하려는 원본 문서 객체
		- patch는 변경분 즉 사용자가 수정한 새로운 정보
		- { updateAt: Date.now( ) }는 강제 업데이트로 수정 시간을 현재 시각으로
	- save();
	- 부분 업데이트
	- 전체 문서 교체 X
	- 필요한 조각만 안전하게 덮어쓰기
- function archiveDoc( id ){  }
	- const toArchive = [ id, ...descendantOf( id ).map(( d => d.id )) ];
		- 지울 대상 목록 만들기
		- id는 지우려고 선택한 본인
		- descendantOf( id )그 본인의 자손을 모두 모음
		- map(( d => d.id )) 그 자식 덩어리에서 ID만 뽑아옴
		- [ id, ... ]를 통해 본인 ID와 자손들의 ID리스트를 하나로 합침
	- toArchive.forEach( ( did ) => { const idx = state.docs.findIndex( x )=> x.id === did ); 
		- forEach를 통해 명단에 적힌 ID를 하나씩 꺼내서 실행
		- findIndex로 이 ID를 가진 문서가 전체 목록 중 몇 번째 줄에 있는지 위치를 찾음
		- 찾은 결과 값을 idx에 저장
		- 목록을 다 뒤졋는데도 못 찾았다면 idx는 -1이 됨
	- if (idx > -1 { state.docs[ idx ].__ originParentId = state.docs[ idx ].parentId ?? null ; state.trash.push(state.docs[ idx ]; state.docs.splice( idx, 1 ); save( ); })})
		- 원래 부모 기억하기
		- dx > -1는 목록에서 진짜 찾았을 때만 실행
		- state.docs[ idx ]는 아까 찾은 idx번째 칸에 있는 문서 객체
		- .__ originParentId은 문서 데이터에 새로운 이름표를 붙이는 것
			- 앞에 언더바를 붙이는건 임시 중요 데이터라는 것을 표현하는 관습
		- state.docs[ idx ].parentId ?? null ; 
			- 원래 이 문서가 들어있던 부모 폴더의 ID를 가져옴
			- 만약 부모가 없는 최상위 문서라면 대신 null을 넣어쥼
		- state.docs.splice(idx, 1); 실제로 문서를 제거하는 명령
			- 1은 idx 번 칸부터 딱 1개만 도려내서 버려라는 뜻
	- 삭제하면 휴지통으로 이동
	- 이 코드는 특정 문서와 그 밑에 달린 모든 자식 문서들을 통째로 아카이브(보관/ 삭제)하는 기능
	- 문서 하나만 지우는게 아니라 그 가문의 모든 후손들을 찾아내서 목록에서 제거
- function restoreDoc(id) {
- 복원 원래 자리로 보내기, 단 부모가 휴지통 상태라면 임시로 루트에 배치
	const idx = state.trash.findIndex((d) => d.id === id);
	- 휴지통 목록을 뒤져서 복구하려는 문서가 몇 번째 칸에 있는지 찾음
	if (idx === -1) return;
	- 만약 휴지통에 해당 ID가 없다면 -1 -> 함수 종료
	const doc = state.trash[idx];
	- 휴지통에서 해당 문서 데이터를 doc 변수에 저장
	state.trash.splice(idx, 1);
	- 휴지통 목록에서 삭제
  

	const desiredParentId = doc.__ origParentId !== undefined ? doc.__ origParentId : doc.parentId;
	- 돌아갈 부모 주소 확인하기
	- 아까 archiveDoc에 몰래 적어둔 __ origParentId값이 있다면 그걸 쓰고 없다면 doc.parentId으로 평소에 가지고 있던 parentId를 돌아갈 주소로 정함
	- 

  

	if (desiredParentId && !existsInDocs(desiredParentId)) {
	- 돌아갈 부모 주소는 있는데 그 부모폴더가 현재 문서 목록에 없다면 -> 즉 부모도 같이 휴지통에 있는 상황

	doc.parentId = null;
	- 부모 주소가 없으니 일단 최상위(null-> root)로 보냄

	doc.__ restoredOrphan = true;
	- 나중에 부모가 복구되면 다시 합쳐질 수 있으니 __ restoredOrphan = true;를 통해 고아상태임이라는 표식을 남김

	doc.__ origParentId = desiredParentId;
	- 원래 부모 주소를 기억해 둠
	toast("부모가 휴지통에 있어 루트로 복원되었습니다.", "success");

	} else {

	doc.parentId = desiredParentId ?? null;

	delete doc.__ restoredOrphan;

	}
	- 부모 폴더가 멀쩡하면 원래 부모 밑으로 복원
	- desiredParentId가 있으면 그 값 없으면 null
	- __ restoredOrphan 이라는 꼬리표는 떼버림

  

	state.docs.push(doc);
	- state.docs 목록에 문서 추가

	normalizeOrders(doc.parentId);
	- 부모 폴더 안 순서 번호를 정수로 다시 매김

	

	reattachOrphansFor(doc.id);
	- 부모가 복구되었으니 아까 부모 주소가 없어서 루트로 복원되었던 자식 문서들이 있는지 확인해서 다시 원래 부모 밑으로 보구언

	save();

	}
	
- function removeDoc(id) {
	-  휴지통에서 영구 삭제(자손 포함)
	const targetIds = new Set([id, ...descendantsOf(id).map((d) => d.id)]);
	- targetIds는 영구 삭제할 문서들의 ID목록
	- new Set( )은 중복을 허용하지 않는 집합
	- 삭제하려는 본인의 id와 그 밑에 딸린 후손들의 Id를 싹 모음

	for (let i = state.trash.length - 1; i >= 0; i--) {
	- i--는 거꾸로 인덱스
	- length - 1라는 가장 마지막 인덱스부터 0까지 거꾸로 내려감

	if (targetIds.has(state.trash[i].id)) state.trash.splice(i, 1);}
	- targetIds.has를 통해 지금 보고있는 휴지통에 i번째 문서가 아까 만든 삭제 명단에 들어있는지 검사
	- 있다면 그 칸을 도려내서 영구 삭제
	save();}
## moveDoc-normalizeOrders - 흔들림 없는 정렬
- moveDoc, normalizeOrders, descendantsOf, reattachOrphansFor
- moveDoc
	- 실제 이동을 집행하는 중심함수
	- 사용자가 특정 문서를 끌어 다른 문서의 위, 아래,안쪽 에 놓는 순간 함수 호출
	- before/ after/ inside
	- 이 세 경우를 하나의 분기에서 처리하는 이유는 문서 이동이라는 개념이 본질적으로 하나이기 때문
	- function moveDoc(srcId, targetId, pos) {
	if (!srcId || !targetId || srcId === targetId) return;
	- 이동해서는 안 되는 상황 차단
	if (isDescendant(targetId, srcId)) return; 
	-  자기 하위로 이동 금지
	- isDescendant(targetId, srcId)가 true면 return
- const src = findDoc(srcId);

	const tgt = findDoc(targetId);

	if (!src || !tgt) return;
- if (pos === "inside") {
	- pos는 moveDoc함수의 인자
	- 위치가 inside 일 때
	const oldParent = src.parentId;
	- 원래 부모 기억하기
	src.parentId = tgt.id;
	- 문서의 부모 id를 타겟 폴더의 id로 바꿈
	- 데이터 상으로 이 문서는 새 폴더 소속
	src.order = maxOrder(tgt.id);
	- 새 폴더의 맨 끝 번호 받기
	normalizeOrders(oldParent);
	normalizeOrders(tgt.id);}
	- 양쪽 순서 정렬하기
-  else {
	- before와 after인 경우
	const newParent = tgt.parentId ?? null;
	- 새로 들어 갈 부모의 주소 결정
	- 타겟 문서의 부모 ID를 가져옴
	- 만약 타겟 문서가 어떤 폴더에도 들어있지 않은 최상위 문서라면 이동시킬 문서의 부모도 null로 정함
	const oldParent = src.parentId;
	- 원래 부모 ID를 잠시 보관
	src.parentId = newParent;
	 - 같은 폴더 안에서 끼워 넣는 과정 혹은 다른 폴더의 문서 옆으로 이동하는 과정
	 - 새 부모 주소로 덮어씌우는 과정 필요
	src.order = pos === "before" ? tgt.order - 0.5 : tgt.order + 0.5;
	- 순서 정하기 로직
	- before이면 -0.5
	- after이면 +0.5
	console.log("src.order: ", src.order);
	- 개발자 확인 용으로 임시 번호가 몇 번인지 출력해주는 콘솔
	normalizeOrders(newParent);

	normalizeOrders(oldParent);}
	- 순서 정렬
	- 정수로 깔끔 정리
	src.updatedAt = Date.now();
	- 최종 수정 시간 업데이트
	save(); }

### 퍼즐 함수들 
- function normalizeOrders(pid){ 
	- const list = childrenOf(pid);
		- 특정 부모의 자식들을 가져와 list로 
	- list.forEach(d,i) => {d.order = i;} }
		- 그 배열의 앞에서부터 차례대로 실행
		- d는 지금 내 앞에 서있는 문서 데이터 그 자체
		- i는 지금 이문서가 서있는 줄의 번호
		- 즉, d의 새 번호표를 지금 서있는 순서 번호로 정한다는 의미
	- 정수 정리 보장기
	- 정수로 깔끔 정리
	- 실제 코드로 확인
	- 작지만 체감 품질 좌우
	- 트리 보정기 역할
- function descendentOf(id){ }
	- 자손을 한 번에 모으는 유틸리티
	- const res = [];
		- 찾아낸 자손들을 담을 빈 배열 바구니 준비
	- const walk = (pid) => {
	 state.docs.filter( ( d ) => d.parentId === pid )
		- 전체 문서(state.docs)중에서 부모 아이디가 지금 찾고있는 ID(pid)와 같은 문서들을 골라냄 -> 직계 자식들을 먼저 찾아내는 과정
	 .forEach( ( c ) => { res.push( c ); walk( c.id ); } ) } };
		- res.push로 찾은 자식( c )를 res에 담음
		- walk( c.id );를 통해 찾은 자식의 자식도 찾기위해 자기 자신을 다시 호출
		- 재귀 -> 자식이 없을 때까지 파고들어감
		- 핵심함수
		- 
	- walk( id );
		- 우리가 처음 입력한 id를 부모로 가진 애들부터 찾기 시작하라고 명령 -> 탐색의 시작점
	- return res;
		- 처음에 만들었던 배열 반환
	- walk함수는 처음에 입력값으로 pid(부모 ID숫자, 문자열)을 받기로 약속
		- c는 문서 객체 전체(이름, 날짜, 내용, ID등이 다 들어있는 덩어리)
		- c.id는 그 문서의 고유 번호
- function reattachOrphansFor(parentId){ 
	- 흩어졌던 고아 문서들을 다시 원래의 부모 폴더로 돌려 보내는 함수
	- let changed = false; 
		- 변화 확인용 스위치
		- 이번 작업에서 실제로 부모를 되찾아준 문서가 있는지 체크
		- 만약 아무도 이사를 안 갔다면 굳이 마지막에 normalizeOrders를 통해 번호 정리를 할 필요가 없기 때문
	- state.docs.forEach( ( d ) => { 
		- 전체 문서 전수 조사
		- 전체문서를 하나씩 확인하면서 두 가지 조건에 맞는 잃어버린 자식을 찾음
	- if (d.__ restoredOrphan && d.__ origparentId === parentId ) 
		- d.__ restoredOrphan은 고아문서라는 표시가 붙어있는가 여부를 확인하는 조건
		- d.__ origparentId === parentId에서 __ origParentId는 삭제되기 직전의 부모 ID를 별도의 임시 변수에 저장해 둔 것이기에 그 아이디와 지금 복구된(입력한 부모 아이디)와 일치하는지 여부를 검사
		- {d.parentId = parentId; 
			- 백업된 주소를 다시 진자 주소 칸에 집어 넣음
		- delete d.__ restoredOrphan;
			- 임시로 썼던 고아 표시 삭제
		- changed = true; } } )
			- 변화 확인용 스위치 true로 변화가 있었음 표시
	- if (changed) { normalizeOrders(parentId); } 
## 공통 헬퍼 세트 - $, $ $, el, toast, fmtDate
- 화면을 만들 때 매번 쓰이게 될 공통 도구들
- 반복 패턴 헬퍼화: 선택, 생성, 알림, 날짜 포맷 단순화
- DOM 캐싱 습관화: 핵심 요소 사전 참조 저장 => 성능, 일관성 향상
- 스케일 무관 필수: 소규모 대규모 모두 적용
- 기반층 확립: 이후 렌더링 이벤트 로직 = 헬퍼 기반

- const $ = (sel) => document.querySelector(sel);
- const $ $ = (sel) => Array.from(document.querySelectorAll(sel));
	- DOM 단축 선택자
	- 짧고 빠르게 DOM 선택
	- sel은 CSS 선택자 의미 (예 .class, div등)
	- $ $에서 Array.from을 붙이는 이유는 쿼리셀럭터올이 노드리스트 형태로 반환되기 때문에 배열로 바꿔주기 위해서 
- function el(tag, opts = {} ){ 
	- tag는 만들고싶은 HTML태그 이름
	- opts={}는 태그에 넣고 싶은 속성들(id, className..) ={}는 만약 함수를 호출할 때 두 번째 인자를 안 넣으면 에러를 내는 대신 빈 상자르 ㄹ기본 값으로 쓰겠다는 의미
	- const e = document.createElement(tag);
		- 메모리상에 입력받은 tag 이름의 요소를 실제로 생성
	- Object.assign(e, opts);
		- opts에 있는모든 내용(속성)을 대상(e)에다가 모두 복사해서 붙여넣음
		- 만약 `opts`에 `{ className: "bold", textContent: "안녕" }`이 들어있다면, 방금 만든 태그(`e`)에 자동으로 `e.className = "bold"`와 `e.textContent = "안녕"`이 실행
		- 
	- return e;}
	- 돔 요소를 새로 만들 때 필요한 반복 패턴을 줄여주는 함수
	- Object.assign(target, sources)
		- sources 객체로부터 target 객체로 속성을 복사해서 옮기는 내장 함수
- function toast(msg, type = ""){
	- const wrap = $("#toast");
		- 위에서 만든 $함수를 사용해서 HTML에서 # toast라는 이름의 컨테이너를 찾음
	- if ( !wrap ) return;
		- 만약 HTML에 # toast라는 컨테이너가 없다면 에러를 내지말고 그냥 함수를 종료하라는 의미 
	- const t = el( "div", {className: `toast ${type}`} );
		- 위에서 만든 el함수 사용
		- div태그를 만드는데 클래스 이름을 toast와 사용자가 넘겨준 type을 합쳐서 만듦 -> (div class = "toast success" )
	- t.textContent = msg;
		- 사용자가 보낸 메세지를 태그 안에 글자로 넣음
	- wrap.appendChild(t);
		- 완성된 알림(t)를 아까 찾은 wrap에 실제로 집어넣음
	- setTimeout( (  ) => {t.style.opacity = "0";
		- setTimeout( ( ) => t.remove( ), 200 );}, 1800 );}
			- 1.8초 뒤에 알람이 나타나고 시간이 지나면 0을 실행해서 투명하게
			- 투명해지는 애니메이션이 끝날시간 0.2초를 기다렸다가 HTML에서 완전히 제거 
	- 화면에서 잠깐 뜨는 알림 toast메세지를 만드는 함수
- function fmtDate( ts ){
	- const d= new Date(ts);
	- return d.toLocaleString( );}
	- 날짜 포맷 헬퍼
	- 입력(숫자 타입 스탬프)
	- 변환 new Date(timestamp)
	- 포맷  date.toLocaleString( ) -> 시스템 로케일 변경
	- 보통 timestamp는 1970년 1.1 부터 지금까지 흐른시간을 밀리초 단위로 나타낸 숫자
	- newDate(ts)는 이 숫자를 자바스크립트가 이해할 수 있는 날짜 객체로 변환
	- 마지막으로 toLocaleString()은 사용자의 브라우저 설정에 맞춰서 날짜와 형식 바꿔줌
## 사이드 바 트리 렌더링 파이프라인 - renderTrees -> renderTree -> renderNode
- 문서 데이터가 화면의 사이드 바의 트리 형태로 나타나도록 만드는 전 과정
- function renderTrees( ){ renderTree( );}
	- 전체 갱신 진입점( trees로 복수 형)
	- 현재 단계에서는 내부에서 renderTree만 호출
	- 즐겨찾기 휴지통 최근 문서 등 추가 섹션도 이 관문만 확장하면 전체 갱신 시나리오 자연스럽게 확대
	- -> 인터페이스 안정성: 외부에서는 renderTrees() 한 번이면 충분
	- 기능이 커져도 호출부 변경 없는 효과
	- 예를 들어 Favorites 블록을 추가하면 renderFavorites()+ renderTree() 순으로 호출 확장 -> 외부 코드는 변경 없음
- function renderTree( ) {
	- if (!docListRoot) return;
	- docListRoot.innerHTML = "";
		- docListRoot는 트리 목록이 그려질 HTML 상의 최상위 부모 요소(예: div id = "list)
		- innerHTML은 새로운 트리를 그리기 전에 기존에 그려져있던 내용을 초기화 -> 데이터가 중복으로 쌓이지 않고 최신 상태로 바뀜
	- const roots = childrenOf(null);
		- 부모 ID가 null인 문서들 즉 어디에도 속해있지 않은 최상위 폴더 찾기
	- if (roots.length === 0) {
		- 데이터가 없을 때
		- const p = el("p", { className: "muted", textContent: "No pages available", });
		- el함수를 써서 < p class = "muted"> No pages available" < /p>라는 안내 문구를 붙임
		docListRoot.appendChild(p);}
	- roots.forEach((d) => docListRoot.appendChild(renderNode(d, 0)));}
		- 데이터가 있을 때
		- 문서가 있는 경우 최상위 문서 roots를 하나씩 돌면서 renderNode(d,0)함수를 실행해 그 결과를 화면에 붙임
### renderNode 함수
- function renderNode(doc, level) {
	- const wrap = el("div");
		- 한 노드 (현재 줄+자식들 전체)를 감싸는 가장 큰 컨테이너 만듦
	- const row = el("div", { className: "tree-row", draggable: true });
		- 실제 내용(아이콘, 제목 등)이 들어가는 한 줄
		- draggable을 true로 줘서 마우스를 끌 수 있게 만듦
	- row.dataset.id = doc.id;
		- HTML 태그에 data-id = "문서ID"형태로 정보를 숨겨둠
		- 나중에 드래그 앤 드롭할 때 어떤 문서가 움직이는지 알아내기 위해
	- if (state.activeId === doc.id) row.classList.add("active");
		- 지금 클릭해서 보고 있는 문서라면 activeId라는 클래스를 추가해서 강조
	- row.style.paddingLeft = 12 + level * 12 + "px";
		- level이 깊어질 수록 왼쪽 여백을 12px씩 늘려 계층 구조 시각화
	- const caretBtn = el("div", { className: "caret", title: "Expand/collapse" });
		- 펼침 화살표 설정
		- 자식 있는 문서에서만 표시
	- const hasChildren = childrenOf(doc.id).length > 0;
		- **`hasChildren`**: 현재 문서(`doc.id`)를 부모로 둔 자식이 있는지 확인
		- .length의 개수가 0보다 크면 true 없으면 false
	- caretBtn.textContent = hasChildren 
		- 자식이 있으면
	- ? state.expanded[doc.id] 
		- ? "▾"
		- : "▸"
	- : "";
		- 자식이 아예 없으면 빈 문자열을 넣어 화살표 숨김
		- - state.expanded 속성에 따라 닫힘 열림 아이콘 변경
		- 자식이 하나라도 있으면 state.expanded[doc.id] 의 값 확인
		- 자식이 있는데 열려있으면 true로 아래 방향 
		- 자식이 있음에도 자식이 없는 화살표를 눌러 펼치지 않은 상태 -> false로 오른쪽 방향
	- if (hasChildren) {
		- caretBtn.addEventListener("click", (e) => {
		- e.stopPropagation();
			- 화살표를 눌렀을 때 그 화살표를 담고 있는 전체 줄(row)이 클릭된 것으로 착각해서 해당 문서로 이동해버리는 이벤트 전달을 막음
		- state.expanded[doc.id] = !state.expanded[doc.id];
			- 현재 이 문서의 펼침 상태를 반대로 뒤집음
		- renderTrees(); }); }
			- 값이 바뀌었으니 화면 전체를 다시 그리는 렌더링
	- const iconCls = "doc-icon " + (doc.icon ? "has-icon" : "no-icon");
		- 아이콘이 있으면 has-icon 없으면 no-icon이라는 클래스 이름을 붙여서 iconCls에 저장
	- const icon = el("div", {
		- className: iconCls,
		- textContent: doc.icon ? doc.icon : "∅",});
			- 아이콘 데이터가 있으면 그 이모지를 쓰고 없으면 "∅" 표시를 넣어 빈칸인 것을 알려줌
	- const labelCls = "label " + (doc.icon ? "has-icon" : "no-icon");
	- const label = el("div", { 
		- className: labelCls,
		- textContent: doc.title,
			- 문서 이름을 글자로 넣음
		- style: "flex:1 1 auto;  min-width:0;",});
			- 제목이 한 줄에서 남는 공간을 다 차지하게 해서 어디를 눌러도 제목을 클릭한 것 처럼 느껴지게
	- label.addEventListener("dblclick", (e) => {
		- e.stopPropagation();
		- inlineRename(doc.id, label); });
			- 제목을 더블클릭하면 inlineRename함수를 실행해 제목을 바로 수정할 수 있게 함
	- const actions = el("div", { className: "tree-actions" });
		- 우측에 나타날 버튼
	- const addBtn = el("div", {
		- className: "icon-btn ghost",
		- title: "Add child",
		- textContent: "＋", });
			- 자식 추가 버튼
	- addBtn.addEventListener("click", (e) => { 
		- e.stopPropagation();
		- const id = createDoc({ title: "Untitled", parentId: doc.id });
			- 버튼을 누르면 현재 문서를 부모로하는 새 문서를 만듦
			- 상태 갱신
		- state.expanded[doc.id] = true;
			- 목록을 펼침 상태로
		- toast("New note created!", "success");
			- 토스트 알람 주기
		- navigateTo(id); });
			- 새문서로 이동
	- const ddBtn = el("div", {
		- className: "dropdown-btn ghost", title: "More", textContent: "⋯", });
			- 더보기 버튼 만들기 
			- 평소에는 투명하다가 마우스를 올리면 살짝 나타나는 스타일을 입히기 위해 class에 ghost
			- HTML의 title 속성은 브라우저가 기본적으로 제공하는 설명 전용 속성
			- 버튼 바로 옆에 아주 작은 네모 상자를 띄우고 그 안에 More이라는 글자를 보여줌
	- ddBtn.addEventListener("click", (e) => {
		- e.stopPropagation();
		- openDropdownMenu(ddBtn, doc, label); });
			- 메뉴를 실제로 그려주는 다른 함수 실행
			- 어떤 버튼 위에 메뉴를 띄울지 정하기 위해 ddBtn으로 클릭한 버튼 전달
			- 어떤 문서에 대한 행위인지 알려주기 위해 doc 보냄
			- 메뉴에서 이름을 수정하거나 참고할 때 보내라고 제목 정보 label로 보냄
	- actions.append(ddBtn, addBtn);
		- 위에 만들어 둔 actions라는 바구니에 아까 만든 버튼 추가
	- row.append(caretBtn, icon, label, actions);
		- 실제 화면에 보일 한 줄 (row)에 화살표 아이콘 제목 버튼들 순서대로 왼쪽부터 차곡 차곡 끼워 넣기
	- row.addEventListener("click", () => navigateTo(doc.id));
		- 사용자가 이 줄의 아무데나 (버튼 제외)클릭하면 해당 문서의 본문을 보여주는 곳으로 화면 전환(MapsTo)
 
	- wrap.append(row);
		- 위에서 다 만든 row를 가장 큰 컨테이너인 wrap에 넣음
	- if (state.expanded[doc.id]) {
		- 만약 이문서가 펼처진 상태라면
		- 자식이 존재한다면
	- const kidsWrap = el("div", { className: "children" });
		- 자식들을 담을 전용 상자 kidswrap을 새로 만듦
		- el div 태그 만들기, 클래스 네임 붙이기
	- childrenOf(doc.id).forEach((ch) =>
		- 현재 문서 doc.id를 부모로 둔 자식들의 목록을 가져와 하나씩 꺼내면서 ch라는 이름
	- kidsWrap.appendChild(renderNode(ch, level + 1)));
		- renderNode(자기 자신. 현재 함수)를 다시 호출
		- 자식 또한 똑같이 render(그려서 가져와라고 명령)
		- 자식에게는 나보다 한 단계 높은 레벨
		- 자식 전용 주머니에 이어 붙이기
	- wrap.append(kidsWrap);}
		- 완성된 주머니를 전체 상자에 넣기
	- return wrap;}
		- 전체 덩어리 반환
## 드래그 앤 드롭
- dragstart -> dragover -> dragleave -> drop -> dragend의 순서와 맞물림 원리를 이해해야 정상 동작
- 사이드 바의 각 행 row는 이미 renderNode함수 안에서 Draggable true로 설정되어 있음 -> 이 속성이 있어야 브라우저가 드래그 이벤트들을 발생시킴
- row.addEventListener("dragstart", handleDragStart);
- row.addEventListener("dragover", handleDragOver);
- row.addEventListener("dragleave", handleDragLeave);
- row.addEventListener("drop", handleDrop);
- row.addEventListener("dragend", handleDragEnd);
- let dragSrcId = null;
- function handleDragStart(e){
	- 드래그 시작 시 실행
	- dragSrcId = this.dataset.id;
		- 소스 문서 Id 취득 후 전역 저장
		- 드롭 시 어떤 문서를 옮기는지 판정 기준
	- e.dataTransfer.effectAllowed = "move";
		- 이 아이템은 이동만 가능하다고 브라우저에 선언하는 것
		- effectAllowed 이 드래그 동작이 허용하는 효과의 종류를 정함(move, link, copy등이 있음)
	- e.dataTransfer.setData("text/plain", dragSrcId);}
		- etData(형식, 데이터) 바귄에 실제 정보를 집어 넣는 메서드
		- text/plain 들어가는 형식이 일반 텍스트 임을 알려줌
		- dragSrcId 드래그를 시작한 그 문서의 ID
		- dataTransfer은 드래그 앤 드롭이 일어나는 동안 데이터를 실어 나르는 투명한 이삿짐 트럭, 브라우저가 관리하는 공식적인 데이터 통로
- function handleDragOver(e) {
	- 드래그 항목이 특정 줄 위에 올라왔을 때 어느 위치에 떨어뜨릴지 실시간으로 판별하고 시각적으로 표시
	- e.preventDefault();
	- const rect = this.getBoundingClientRect();
		- 마우스 위치 계산
		- 현재 마우스가 올라가있는 이 줄의 실제 화면 위치와 크기 정보 가져옴
	- const y = e.clientY - rect.top;
		- 현재 마우스의 세로 위치에서 줄의 맨 윗부분을 뺌
		- 결과는 줄의 맨 위에서부터 마우스가 몇 픽셀 아래에 있는가를 나타내는 숫자가 됨
	- this.classList.remove("dragover-top", "dragover-bottom", "dragover-inside");
		- 새로운 위치를 계산하기 전에 기존에 붙어있던 드래그 효과들을 지워서 깨끗하게 만듦
	- if (y < rect.height * 0.25) { this.classList.add(dragover-top);}
		- 상단 25%미만 
		- 마우스가 줄의 아주 윗부분에 있다면 이 항목 위쪽에 끼워넣으려나 보네 라고 판단
	- else if (y > rect.height * 0.75) { this.classList.add(dragover-bottom);}
		- 하단 75%초과
		- 마우스가 줄의 아주 아랫부분에 있다면 이 항목 아랫쪽에 끼워넣으려나 보네 라고 판단
	- else { this.classList.add(dragover-inside);}}
		- 그 외 중간 쯤이면 안으로 
- function handleDragLeave( ){ this.classList.remove("dragover-top", "dragover-bottom", "dragover-inside") }
	- 마우스가 행을 벗어날 때 실행
	- 시각 힌트 정리
	- 드롭 가이드가 사라짐
- function handleDrop(e){
	- 실행시점 마우스를 놓는 순간
	- e.prventDefault( );
	- const targetId = this.dataset.id;
		- 지금 마우스를 뗀 곳, 즉 도착지가 어딘지 ID를 알아냄
	- const rect = this.getBoundingClientRect();
	- const y = e.clientY - rect.top;
	- let pos = "inside";
		- 기본 값은 inside
		- 최종적으로 어디에 배치할지 결정하는 변수
	- if (y < rect.height * 0.25) pos = before;
	- else if (y > rect.height * 0.75) pos = after;
	- moveDoc(dragSrcId, targetId, pos);
		- 실제 이사 실행
		- `dragSrcId`: 아까 `dataTransfer` 트럭에 실어뒀던 옮길 놈의 ID.
		- `pos`: 위에서 계산한 정확한 위치(before, after, inside)
	- this.classList.remove("dragover-top", "dragover-bottom", "dragover-inside")
	- renderTrees();
- function handleDropEnd(){
	- $ $( ".tree-row" ).forEach( ( r ) => r.classList.remove("dragover-top", "dragover-bottom", "dragover-inside" );
		- 화면에 있는 모든 트리 줄(tree-row클래스를 가진 요소들)을 전부 찾아옴
		- 찾은 줄을 하나씩 꺼내서 r이라고 부르며 작업 반복
		- 효과 모두 지우기
	- dragSrcId = null;  }
	- 드래그 앤 드롭의 모든 과정이 끝났을 때 실행되는 함수
	- 드롭이 성공했든 중간에 취소했든 상관없이 상태 초기화






















