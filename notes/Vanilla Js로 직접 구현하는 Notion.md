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
## normalizeOrder로 순서 정리, save로 상태 영속화
- function save( ){
	- const data = {
		- 저장할 바구니 만들기
		- 현재 상태에서 필요한 정보만 모아 하나의 큰 상자에 담음
		- docs: state.docs,
		- trash: state.trash,
		- expanded: state.expanded,
		- activeId: state.activeId, } ;
		- localStorage.setItem(STORAGE_KEY, JSON.stringify(data))}
			- 데이터를 글자로 바꾸기
			- setItem을 통해 브라우저가 제공하는 저장소에 저장
			- STORAGE_KEY는 이름표
## load로 기본 문서와 저장소 데이터를 안전하게 복원하기
- 새로고침하거나 어플리캐이션을 다시 열었을 때 이전에 저장해 둔 상태를 불러오기
- 초기화 과정(load 함수)이 동작하여 기본 docs와 저장소 데이터를 병합하고 사이드 바 트리 구성
- function load( ){ 
	- try{ const raw = localStorage.getItem(STORAGE_KEY);
		- if ( !raw ) { 
			- state.docs = defaultDocs.slice( ); 
			- state.trash = [ ];
			- return; } 
		- const data = JSON.parse(raw);
		- state.docs = data.docs || defaultDocs.slice( );
		- state.trash = data.trash || [];
		- state.expanded = data.expanded || { };
		- state.activeId = data.activeId || null;}
		- catch ( e ){ 
		- console.warn("Failed to load, using defaults", e ); 
		- state.docs = defaultDocs.slice( );
		- state.trash = [ ];}}

- try{ const raw = localStorage.getItem(STORAGE_KEY);을 통해 저장된 문자열 불러오기
	- 만약 저장된 값이 없으면 if ( !raw ) { 문으로 defaultDocs.slice 메서드로 복사한 기본 문서를 state.docs에 넣음
	- 휴지통 빈 배열로 초기화하고 save호출 없이 단순히 초기 상태만 유지
	- return으로 함수 종료하고 catch까지 도달하지 않음
- 저장된 값 raw가 있는 경우 cosnt 부터 실행
	- raw는 긴 문자열 텍스트임
	- 그 문자열을 JSON.parse를 통해 객체화하여 data값에 저장
	- data값의 docs를 state.docs로 집어넣기, 만약 그 값이 없으면 defaultDocs채우기
	- state.trash = data.trash || [];부터 모두 마찬가지
- 저장된 값이 있는데 에러가 발생한 경우 catch ( e ){ 으로 처리
	- 경고 메세지를 띄우고 defaultDocs값을 복사해서 채워넣음
	- 휴지통 초기화

## 인라인 이름 바꾸기 - 더블클릭, enter, escape로 라벨 자연스럽게 편집
- 사이드 바 트리에서 문서 이름을 직접 바꾸는 기능
- 사용자가 문서를 더블클릭하면 기존 라벨이 입력창으로 전환되고 엔터키를 누르거나 포커스를 잃으면 이름이 반영
- function inlineRename(id, labelEl){ 
	- const doc = findDoc(id);
	- if (!doc) return;
	- const input el("input", { value: doc.title, className: "label-edit" })
	- input.addEventListener("click", (e) => e.stopPropagation( ));
	- input.addEventListener("keydown", (e) => {
		- if (e.key === "Enter" {
			- e.preventDefault( );
			- input.blur( );}
		- if (e.key === "Escape") {
			- e.preventDefault( );
			- input.value = doc.title;
			- input.blur( );} )};
	- input.addEventListener("blur", ( ) => {
		- const title = input.value.trim( ) || "Untitled";
		- updateDoc(id, { title }); 
		- renderTrees( );
		- if (state.activeId === id ){
			- $("#titleInput").value = tilte;
			- updateDocMeta( );})};
	- labelEl.replaceWith(input);
	- input.focus( );
	- input.select( );

- inlineRename(id, labelEl)에서 두 개의 인자를 받음
	- id는 수정하려는 문서의 고유번호 
	- labelEl은 현재 화면에 그려져있는 제목 글자 요소(HTML Element)
		- 즉 눈에 보이는 글자 덩어리
		- 입력창으로 변경시킬 글자 자리를 알기 위해 입력
-  const doc = findDoc(id);는 인자로 받은 Id를 열쇠 삼아, 전체 데이터(state.Docs)중에서 어떤 문서인지 찾아냄
	- 만약 해당하는 문서가 없다면 if (!doc) return;으로 함수 종료
- 해당하는 문서가 있다면 const 부터 순차적으로 실행
	- const input el("input", { value: doc.title, className: "label-edit" })을 통해서 새로운 < input > 태그창을 만듦
	- value: doc.title를 통해 아까 찾은 문서의 제목을 입력창 안에 미리 적어둠
	- value는 입력창 안에 적혀있는 실제 글자 내용을 의미함 
- input.addEventListener("click", (e) => e.stopPropagation( ));
	- 입력창 클릭했을 때 이벤트 실행
	- e.stopPropagation( )으로 클릭 신호가 부모에게까지 전달되는 것을 막음
- input.addEventListener("keydown", (e) => {은 키보드 키를 눌렀을 때 실행된느 이벤트 설정한 것
	- if (e.key === "Enter" { 엔터키를 누른 경우 실행
		- e.preventDefault( );으로 브라우저 기본 키 동작 취소하고
		- input.blur( ) 함수 호출 -> 실행
		- blur는 커서가 빠져나가는 상태를 의미
- if (e.key === "Escape") { ESC키를 누른 경우 실행
	- 마찬가지로  e.preventDefault( );으로 브라우저 기본 키 동작 취소하고
	- input.value = doc.title; 원래 저장되어있던 제목을 input.value에 대입
	- 결과적으로 입력창의 글자가 다시 원래 제목으로 되돌아감 -> 취소 기능
	-  input.blur( )로 커서가 빠지면서 blur이벤트 자동 실행
- input.addEventListener("blur", ( ) => {
	- 커서가 빠지는 순간 실제로 데이터를 바꾸는 작업이 실행됨
	- const title = input.value.trim( ) || "Untitled"; 입력값의 앞 뒤 공백을 없앤 값을 제목으로 지정하는데, 만약 그 값이 없다면 untitled라고 지어주기
	- updateDoc(id, { title });에서 id는 수정할 대상의 고유 id, { title }은 { title: title }의 줄인 말로 새로운 제목이 담긴 객체 -> 실제 데이터 제목 업데이트
	- renderTrees( );를 통해 트리 목록을 다시 그려서 화면 새로 고침
- if (state.activeId === id ){ 지금 이름을 바꾼 문서가 현재 에디터에 열려있는 문서라면
	- 목록(사이드 바)의 이름만 바꾸는 것이 아니라 오른쪽 상단의 타이틀도 변경
	- $("#titleInput").value= title;는 에디터 오른쪽 상단에 크게 써있는 제목 입력창을 가리킴 그 값의(value) 내용을 수정한 이름으로 바꿈
	-  updateDocMeta( ); 을 통해서 수정한 정보 갱신
		- 수정 시간 저장상태 표시 등을 갱신
- 마지막으로 labelEl.replaceWith(input);을 통해서 우리가 처음에 함수 두 번째 인자로 받아왔던 제목 글자(HTML 요소)를 초반에 메모리상 만들어 둔 input으로 변경
	- replaceWith은 HTML요소를 통째로 바꿔치기하는 명령어
	- input.focus( );으로 입력창이 나타나면 커서가 깜빡거리도록
	- input.select( );으로 입력창 안에 기존 제목을 전체 드래그 된 상태로 만듦
- focus와 select를 마지막에 위치해 있는 이유
	- input이 있어야 작동하기 때문
	- input은 const input줄에서 생성되었을 떄 아직 메모리 상에만 존재하는 상태
	- labelEl.replaceWith(input)을 통해서 입력창으로 변경되어야 실제 화면으로 구현되기 때문에
	- 실제화면으로 구현된 직후에 focus와 select가 실행될 수 있기 때문
## 사이드바 액션 버튼 - +로 자식 추가, ...으로 더보기 메뉴
- const actions = el("div", { className: "tree-actions" });
- const addBtn = el("div", {className: "icon-btn ghost", title: "Add child", textContent: "+", })
- addBtn.addEventListener("click", (e) => {
	- e.stopPropagation( );
	- const id = createDoc( { title: "untitled", parentId: doc.id });
	- state.expanded[doc.id] = true;
	- toast("New note created!", "success");
	- navigateTo(id);});

- const ddBtn = el("div", {className: "dropdown-btn ghost", title: "More", textContent: "...", });
- ddBtn.addEventListener("click", (e) => {
	- e.stopPropagation( );
	- openDropdownMenu(ddBtn, doc, label);})

- actions.append(ddBtn, addBtn);
- row.append(caretBtn, icon, label, actions);
	- actions 컨테이너 채우기
	- 화살표, 아이콘, 제목, 버튼 모음으로 구성된 문서 한 줄 완성

- actions라는 컨테이너를 만들고 그 안에 두 개의 버튼 생성
- const addBtn = el("div", {className: "icon-btn ghost", title: "Add child", textContent: "+", })
	- div 상자를 만들고 
	- className 후에 css로 디자인 바꾸기 위해 설정
	- title: "Add child"으로 말풍선 힌트
	- textContent: "+"는 버튼 정중앙에 보여줄 글자
	- ddBtn도 마찬가지

- addBtn.addEventListener("click", (e) => {
	- addBtn이 클릭되었을 때 이벤트 실행
	- e.stopPropagation( );으로 부모 요소에 이벤트가 전파되는 것 방지
	- const id = createDoc( { title: "untitled", parentId: doc.id });
		- doc.id는 그 버튼이 만들어지던 순간의 doc.id 그 id를 부모 id로 설정
			- 생성된 문서가 클릭된 문서의 자식으로 생성됨
	- state.expanded[doc.id] = true;로 부모 폴더가 열린 상태로 바뀌게 설정
		- 방금 만든 새문서가 바로 보이도록 하는 것
	-  toast("New note created!", "success");을 통해 생성 성공 알림
		- 첫 번째 인자는 눈에 보이는 실제 내용
		- 두 번째 인자는 알림의 타입 설정 -> css 디자인 변경
	- navigateTo(id)을 통해서 주어진 Id에 해당하는 요소 도는 라우트로 이동

- ddBtn.addEventListener("click", (e) => {
	- ddBtn이 클릭되면 이벤트 발생
	- e.stopPropagation( );
	- openDropdownMenu(ddBtn, doc, label);})으로 메뉴 보여주기
		- ddBtn은 메뉴창이 뜨는 위치를 알려주는 좌표 역할
		- doc은 메뉴에 있는 기능이 처리될 문서
		- label은 제어대상 예를 들어 제목을 바꾸는 기능을 처리할 때 필요 

## 해시 라우팅과 본문 렌더링 - 사이드바 클릭부터 에디터 갱신까지
- 사용자가 문서를 선택하면 주소창 해시가 바뀌고 해시를 다시 해석하여 현재 활성 문서를 결정한 뒤 오른쪽 본문 영역에는 제목, 본문내용, 브레드 크럼, 이모지, 즐겨찾기 상테, 메타정보가 모두 갱신됨
- 문서 본문 영역을 렌더링할 때 반드시 필요한 핵심 요소들 미리 잡아둠
	- const emojiPicker = $("#emojiPicker"); 문서 아이콘 선택 팝업
	- const emojiGrid = $("#emojiGrid"); 이모지 선택 영역
	- const titleInput = $("#titleInput"); 제목 표시/ 즉시 수정 입력창
	- const docMeta = $("#docMeta"); 생성/ 수정 시각 정보
	- const editor = $("#editor"); 본문 표시, 편집 핵심 영역
- function navigateTo(id){
	- if (!id) {
		- location.hash = "#/documents";}
		- else { location.hash = "#/documents/" + id;}}
	- 이 함수는 사이드바에서 문서를 클릭했을 때 실행됨
	- 내부적으로 상태를 직접 바꾸지 않고 오직 브라우저 주소창의 해시를 변경
	- 문서 아이디가 없다면 # /documents라는 루트 경로로 해시 설정
	- 있으면 # /documents/" + id로 해시 설정
	- 이 시점에서 브라우저는 hashchange이벤트를 발생시켜 다음 함수 실행될 준비

- funciton syncFromLocation( ){
	- const m = location.hash.match(/#\ /documents \ /?([\ w-] +) );
	- const id = m && m[ 1 ] ? m[ 1 ] : null; 
	- state.activeId = id;
	- renderTrees( );
	- renderPage( );
	- save( );}
- window.addEventListener("hashchange", syncFromLocation);
	- 해시 변경을 실제 상태와 화면에 반영하는 함수
	- 정규식을 통해 주소창 해시에서 문서 아이디 추출 
		- location.hash는 URL에서 # 이후의 문자열 반환
		- 정규식 # 문자 매칭
		- \ / documents 문자열 매칭
		- \ /? /가 있어도 없어도 됨
		- ([\ w-] +)은 캡쳐 그룹 - 영문자, 숫자, _ , -로 이뤄진 ID추출
		- const id = m && m[ 1 ] ? m[ 1 ] : null; 는 m이 없으면 null, m[1]이 없으면 null 정상매칭되면 id
		- 이렇게 추출한 ID를 state.activeId 상태에저장 
		- renderTrees( );
			- 현재 state를 기반으로 사이드바 렌더링
			- activeId가 바뀌었으니 트리에서 해당 항목을 하이라이트,선택 표시
		- renderPage( );
			- state.activeId에 해당하는 문서 본문 내용을 화면에 렌더링
			- 선택된 문서의 실제 콘텐츠를 표시
		- save( );
			- 현재 상태를 로컬 스토리지에 저장

- function pathOf(id){
	- const path = [ ];
	- let cur = findDoc(id);
	- while(cur){
		- path.unshift(cur);
		- cur = cur.parentId ? findDoc(cur.parentId) : null;}
		- return path; }
	- const path = [ ]; 
		- 조상들을 차례로 담을 빈 배열 생성
	- let cur = findDoc(id); 
		- 내가 찾고자하는 그 문서를 찾아서 cur이라는 변수에 담음
		- 현재 위치 파악
	- while(cur){은 조상 찾기 반복문
		- cur이 존재하는 동안, 즉 더 이상 올라갈 부모가 없을 때까지 반복
		- path.unshift(cur);여기서 unshift를 사용한 이유는 배열의 맨 앞에 끼워넣기 위해서 -> 추가될 때마다 뒤가 아니라 맨 앞에 차례로 쌓임
	- cur = cur.parentId ? findDoc(cur.parentId) : null;}
		- 부모 ID가 있으면 그 부모를 findDoc으로 찾아와서 새로운 cur로 변경
		- 부모가 없으면 null을 넣어 반복문 종료
	- return path; 으로 만든 배열 결과로 전달

### 렌더페이지 함수
- function renderPage() {
	- if (!breadcrumbs || !titleInput || !editor || !starBtn || !docMeta) return;
	- if (!state.activeId) {
		- breadcrumbs.textContent = "No page selected";
		- titleInput.value = "Welcome 👋";
		- docMeta.textContent = "—";
		- editor.innerHTML = "< p>좌측에서 문서를 선택하거나 새로운 페이지를 만들어 보세요.< /p>";
		- starBtn.textContent = "☆";
		- return; }
	- const doc = findDoc(state.activeId);
	- if (!doc) {
		- breadcrumbs.textContent = "Unknown page";
		- titleInput.value = "Not found";
		- editor.innerHTML = "< p>이 문서는 존재하지 않습니다.< /p>";
		- return;}
	- const path = pathOf(doc.id).map((d) => d.title).join(" / ");
	- breadcrumbs.textContent = path;
	- titleInput.value = doc.title;
	- editor.innerHTML = doc.content || "< p>< /p>";
	- starBtn.textContent = doc.starred ? "★" : "☆";
	- updateDocMeta();}

- 렌더페이지 함수는 에디터 오른쪽 화면을 채우는 인테리어 담당자
- if (!breadcrumbs || !titleInput || !editor || !starBtn || !docMeta) return;
	- 경로, 제목 입력창, 에디터, 메타정보창 중 하나라도 없으면 함수를 실행하지 않겠다는 뜻 
- if (!state.activeId) {
	- 선택된 문서가 없다면
	- breadcrumbs.textContent = "No page selected"; 브레드 크럼의 택스트 내용 변경
	- 타이틀 값 welcome으로 변경
	- 문서 정보 -로 변경
	- 에디터 본문 내용을 좌측에서- 문구로 채움
	- 즐겨찾기 표시 빈 별로 초기화
- const doc = findDoc(state.activeId);
	- 선택된 문서가 있다면 그 문서 데이터 찾아서 doc 변수에 담기
- if (!doc) { 
	- 선택된 문서가 있는데 데이터가 없다면 -> 에러가 발생한 경우
	- 브레드 크럼 경로 텍스트 변경
	- 제목 값 변경
	- 본문에 이 문서는 존재- 내용 넣기
	- 함수 종료
- const path = pathOf(doc.id).map((d) => d.title).join(" / ");
	- 선택된 문서가 있고 데이터가 있는 경우
	- pathOf를 통해서 문서들이 차례로 담긴 배열 가져오기
	- map을 통해서 배열 내용의 제목들만 골라낸 후 
	- join("/")을 통해 리스트 사이에 / 을 넣어서 하나의 문장으로 합치기
- breadcrumbs.textContent = path;
	- 브레드크럼(경로 표시 창) 내용을 아까 만든 path 내용으로 넣기
	- titleInput.value = doc.title;
		- 제목 입력창에 현재 문서의 제목 넣기
	- editor.innerHTML = doc.content || "< p>< /p>";
		- 에디터 본문에 문서 내용 넣기, 없으면 빈 문단 넣기
	- starBtn.textContent = doc.starred ? "★" : "☆";
		- 즐겨찾기가 되어있으면 별, 아니면 빈 별
	- updateDocMeta();}
		- 문서 부가 정보 업데이트 함수

- function updateDocMeta() {
	- if (!docMeta) return;
	- const d = state.activeId ? findDoc(state.activeId) : null;
	- const ld = $("#lastEdited");
	- if (ld) ld.textContent = new Date().toLocaleDateString();
	- if (!d) {
		- docMeta.textContent = "—";
		- return;}
	- docMeta.textContent = `Created ${fmtDate(d.createdAt)} · Updated ${fmtDate( d.updatedAt )}`;}

- if (!docMeta) return;
	- 메타 정보를 표시할 공간이 화면에 없으면 함수 종료
- const d = state.activeId ? findDoc(state.activeId) : null;
	- 있으면 먼저 활성화된 문서의 데이터를 가져오고 없으면 null
-  const Id = $("#lastEdited");
	- 화면에서 lastEdited라는 이름표를 가진 곳을 찾아서 Id에 저장
	- if (Id) ld.textContent = new Date().toLocaleDateString();
		- 만약 그 값이 있으면 지금 현재의 컴퓨터 날짜를 가져와서 한국식 날짜 형식으로 바꾼 후 아까 찾은 Id 자리에 내용으로 넣기
	- if (!d) { 만약 값이 없으면 
		- 정보 칸에 -를 넣고 함수 종료
- docMeta.textContent = `Created ${fmtDate(d.createdAt)} · Updated ${fmtDate( d.updatedAt )}`;}
	- 백틱 안에서의 ${}은 글자가아니라 자바스크립트 코드가 들어있음을 의미
	- fmtDate(d.createdAt)
		- 문서 데이터에서 만든 날짜(createdAt를 꺼내서 fmtDate라는 함수에 보내 한국식 날짜로 변경한 값
	- 중간에 .은 읽기 쉬우라고 넣은 단순한 기호
	- 생성일과 수정일을 채워 넣음 

### 초기화 함수
- function init( {
	- load( );
	- if (state.isMobile) {
		- collapse( );
	- else{
		- resetWidth( );}
	- renderTrees( );
	- renderTrash( );
	- if (!location.hash) { 
		- navigateTo("welcome");
	- else { syncFromLocation( );}
	- const id = $(#lastEdited");
	- if(Id) Id.textContent = new Date( ).toLocaleDateString( );
	- syncMenuBtnVisibility( ); }
	- init( ); 

- load( ); 
	- 저장소애서 이전에 썼던 문자 데이터를 싹 불러옴
- if (state.isMobile) { collapse( );
	- 사용자가 모바일로 접속했으면 사이드바를 접고(collapse)
- else{ resetWidth( );}
	- pc로 접속했으면 사이드 바 너비를 원래대로 resetWidth로 맞춤
- renderTrees( );  renderTrash( );
	- 트리구조와 휴지통 안 목록 그리기
- if (!location.hash) {
	- 만약 주소창에 아무런 정보가 없다면 navigateTo("welcome");으로 welcome 페이지 보여줌
-  else { syncFromLocation( );}
	- 주소가 있다면 그 번호에 맞는 문서를 화면에 띄움
- const id = $(#lastEdited");
	- 오늘 날짜 기록하기
	- HTML 설계도에서 id = lastEdited라는 이름표를 가진 칸을 찾기
	- if(Id) Id.textContent = new Date( ).toLocaleDateString( );
		- 그 자리가 존재하면 현재 컴퓨터 시간을 채우기
- syncMenuBtnVisibility( ); }
	- 현재 상태에 맞춰 메뉴 버튼을 보여줄지 말지 결정
- init( ); 
	- 이 모든 설정을 마친 뒤 함수를 실행해서 앱 가동

## 제목 본문 편집과 자동 저장 - 즉시 반영과 디바운스
- const titleInput = $("#titleInput"); 제목 입력창
- const docMeta = $("docMeta"); 메타 영역
- const editor = $("#editor"); 본문 에디터
	- 핵심 DOM참조
	- 본문 렌더링과 편집을 잇는 연결고리
- ### 실시간 제목 업데이트 코드
- titleInput?.addEventListener("input", ( )=> {
	- if (!state.activeId) return;
	- const t = titleInput.value.trim( ) || "untitled";
	- updateDoc(state.activeId, { title: t });
	- renderTrees( );
	- updateDocMeta( ); } );

- titleInput?.addEventListener("input", ( )=> {
	- titleInput이라는 제목 입력창
	- ?.은 옵셔널 체이닝 
	- .addEvent이렇게 바로 시작하지 않고 ?를 붙여서 입력창이 있는지 보고 코드 실행
- if (!state.activeId) return;
	- 지금 수정할 문서가 선택되어 있지 않다면 함수 종료
- const t = titleInput.value.trim( ) || "untitled";
	- 있다면 입력창의 값을 앞 뒤 공백 제거한 후 t라는 변수에 저장, 없으면 untitled
- updateDoc(state.activeId, { title: t });
	- 지금 선택된 문서를 찾아가서 그 문서의 제목을 t로 덮어쓰기
- renderTrees( ); - updateDocMeta( ); } );
	- 차례대로 실행

### 본문 편집 디바운스
- let saveTimer = null;
- function saveEditorDebounced( ){
	- clearTimeout(saveTimer);
	- saveTimer = setTimeout(saveEditor, 400);}
- function saveEditor( ){
	- if (!state.activeId) return;
	- const html = editor.innerHtml;
	- updateDoc(state.activeId, { content: html } );
	- updateDocMeta( );}
- editor?.addEventListener("input", saveEditorDebounced);

- let saveTimer = null;
	- 저장할 시간을 잴 타이머 마련
	- 처음엔 null 값
- function saveEditorDebounced( ){
	- clearTimeout(saveTimer);
		- 함수가 실행되면 먼저 saveTimer 초기화
	- saveTimer = setTimeout(saveEditor, 400);
		- 지금으로 부터 0.4초 뒤에 saveEditor 실행
		- 실행하겠다는 예약을 하면서 번호를 매기는데 그 값을 saveTimer에 저장
- function saveEditor( ){
	- if (!state.activeId) return;
		- 먼저 실행중인 문서가 있는지 확인하고 없으면 함수 종료
	- const html = editor.innerHtml;
		- 있으면 에디터 본문 칸에 적힌 글자를 모두 모아 html이라는 변수에 담음
	- updateDoc(state.activeId, { content: html } );
		- 현재 실행중인 문서의 데이터를 덮어씌워 저장
	-  updateDocMeta( );}
		- 저장이 끝났으니 수정 날짜 갱신
- editor?.addEventListener("input", saveEditorDebounced);
	- 에디터 본문 칸이 화면에 있는지 확인하고(?.) 인풋 이벤트 실행
	- 즉 글자 입력이 감지되면 saveEditorDebounced함수 실행

## 테마 전환 & 사이드바 너비 접기 - 로컬스토리지, 미디어쿼리, 애니메이션
### 테마 전환
- const THEME_KEY = "vnotion:theme"; //'light' | 'dark'
	- THEME_KEY는 문자열 상수
	- vnotion:theme는 브라우저의 저장소에 테마 정보를 저장할 때 사용할 이름표
	- 노션 앱 전용 테마 보관함임을 표시
	- // 뒷부분은 코드를 읽는 개발자들에게 하는 말 -> 라이트 혹은 다크만 들어올 수 있다는 것을 가이드 해줌
	- 범위는 스크립트 전체, 모듈 스코프, 로컬 스토리지에 THEME을 저장하거나 읽어올 때 식별자로 사용됨
	- localStorage.getItem(THEME_KEY), localStorage.setItem(THEME_KEY,value)를 하지 않아도 안전하게 동일 키 참조 가능

- function applyTheme(theme){
	- // theme: 'light' | 'dark' 
	- document.documentElement.setAttribute("data-theme", theme); }

	- 테마를 적용하는 함수
	- 어떤 색으로 바꿀지 theme재료를 주기 -> dark 혹은 light가 들어감
	- document.documentElement는 우리 웹사이트의 가장 최상위 루트를 찾는 것 -> HTML문서 전체를 감싸고 있는 < html > 태그를 의미
	- setAttribute("data-theme", theme); 는 그 뿌리 태그에 data-theme라는 이름표를 붙이고 그 값으로 light혹은 dark를 써넣어라는 명령
		- 예를 들면 이렇게 < html data-theme="dark">

- function saveTheme(theme) {
	- try{
		- localStorage.setItem(THEME_KEY, theme);}
		- catch(e) { } }

	- 사용자가 선택한 테마 설정을 브라우저의 기억 저장소에 영구적으로 기록하는 함수
	- 단순히 저장만하는 것이 아니라 에러 방지 문이 씌워져 있는 것이 특징
	- 용량이 꽉 찼거나 브라우저 설정에서 차단했거나 등 에러가 발생하는 상황 보호
	- localStorage.setItem(THEME_KEY, theme)을 통해서 브라우저 저장소의 THEME_KEY("vnotion:theme")라는 칸에 사용자가 고른 테마 값을 저장
	- 사용자가 브라우저를 껐다 켜도 앱은 사용자가 어떤 모드를 사용했는지 기억 가능
	- 만약 에러가 발생하면 아무것도 하지 말고 그냥 넘어가기 

- function loadTheme ( ){
	- try{ 
		- const t = localStorage.getItem(THEME_KEY);
		- if (t === "light" || t === "dark" ) return t; }
		- catch(e) { } 
		- return "dark"; }

	- 브라우저 저장소에서 THEME_KEY로 저장되어 있는 값이 있는지 확인하고 있으면 변수 t에 담기
	- 그 값이 dark나 light인 경우 그 값을 돌려주기
	- 만약 에러가 나거나 값이 없으면 기본적으로 dark값을 반환

- let currentTheme = loadTheme( );
	- currentTheme은 상위 스코프 변수로 선언되어 이후에도 최신 테마 상태 
	- loadTheme( )가 문자열 반환 -> currentTheme에 즉시 저장
- applyTheme(currentTheme);
	- 저장된 값을 넘겨 HTML 데이터 theme속성 부여 
	- 화면은 로딩과 동시에 사용자의 마지막 설정과 같은 테마 설정으로 불러와짐

### 사이드바 너비, 접기
- const LS_LAST_WIDTH_KEY = "vnotion: lastSidebarwidth"; // 숫자 || null
	- 사이드바 너비를 저장할 저장소 칸의 이름표 설정
- let lastSidebarwidth = null;
	- 마지막으로 설정된 너비 값을 담을 변수를 만들고 처음에는 빈 상태로 둠
- function readLastwidth( ){
	- try{
		- const raw = localStorage.getItem(LS_LAST_WIDTH_KEY);
		- if (raw){
			- const n = parseFloat(raw);
			- if (!isNaN(n)) lastSidebarwidth = n;  }
			- } catch (e) { } }
	- 저장소에서 예전에 저장한 너비 값을 읽어오는 함수
	- const raw = localStorage.getItem(LS_LAST_WIDTH_KEY);는 저장소에 가서 LS_LAST_WIDTH_KEY를 찾아 raw라는 변수에 담기 -> 이때 가져온 데이터는 아직 문자 형태
	- 만약 raw값이 존재하면 parseFloat(raw)을 통해서 문자를 소수점이 있는 숫자로 변환하여 변수 n에 담음
	- isNaN은 괄호 안에 있는 n이 숫자가 아닌지 물어보는 것
	- 그렇다면 역으로 !isNaN은 숫자면 true를 반환 -> true일 때만 lastSidebarwidth = n;으로 n값을 lastSidebarwidth에 넣는 것
	-
- function writeLastwidth(w){
	- lastSidebarwidth = w;
	- try{
		- localStorage.setItem(LS_LAST_WIDTH_KEY, String(w)); }
		- catch (e) { } }

	- 다시 방문했을 때 동일 값으로 복원할 수 있게 해주는 핵심 함수
	- 너비 값을 실제로 저장하는 함수
	- 지금 화면에 보이는 너비 w를 lastSidebarwidth 변수에 저장
	- 저장소의 LS_LAST_WIDTH_KEY에 새로운 너비를 문자 형태로 저장
		- 저장소는 오직 문자만 저장할 수 있기에 이 과정 필요

- function getCurrentSidebarwidth( ){
	- const sb = document.querySelector("#sidebar");
	- if (!sb) return null; 
	- const v = parseFloat(getComputedStyle(sb).width || "0" );
	- return isNaN(v) ? null : v; }

	- getCurrentSidebarwidth( )를 통해 화면에 그려진 사이드 바의 진짜 크기 측정
	- 문서에서 ID가 sidebar인 요소를 찾음
	- 만약 사이드 바가 없으면 중단
	- parseFloat(getComputedStyle(sb).width || "0"
		- css파일, < style >태그, 브라우저 기본 설정 등 모든 값을 합쳐서 계산된 최종 스타일 값들을 읽어옴 -> 색상, 폰트, 마진, 너비 등
		- 우리가 css값을 줄 때 여러 가지 단위를 쓰는데, 브라우저는 반드시 픽셀단위로 변환되어야 그 값을 사용할 수 있음 
			- computed는 이 변환이 끝난 픽셀 값을 가져옴
		- .width는 그 값들 중에서 너비 픽셀만 가져오는 것
		- parseFloat을 통해서 소수점 숫자로 변환
		- v값이 숫자가 아니면 null 값을, 숫자면 v값을 반환

- function defaultSidebarwidth( ){
	- return window.matchMedia("(max-width:768px)").matches ? 280 : 260; }

	- 사용자가 한 번도 너비를 조절한 적이 없을 때 모바일인지 pc인지에 따라 적당한 크기를 정해줌
	- 현재 화면 가로 폭이 768 px 이하라면 280px을, 아니라면 260px을 기본 값으로 사용

- function setSidebarwidth(px){
	- document.documentElement.style.setProperty("--sidebar-w", px + "px" );}

	- documentElement는 HTML문서의 가장 꼭대기인 < html > 태그를 가리킴
	- --sidebar-w은 css에서 사용하는 변수 
		- 개발자가 css파일에 미리 만들어 둔 전역 변수임
		- 보통 :root { --sidebar-w: 260px; } 이런 형식
	- setProperty를 통해서 자바스크립트가 그 변수 값을 실시간으로 변경

- function animateSidebarwidth(toPx, duration = 300){
	- const fromPx = getCurrentSidebarwidth( ) || 0;
	- if (fromPx === toPx) {
		- setSidebarwidth(toPx);
		- return;}
	- const start = performance.now( );
	- function frame(now){
		- const progress = Math.min(1, (now - start)/ duration);
		- const cur = fromPx + ( toPx - fromPx ) * progress;
		- setSidebarwidth(cur);
		- if (progress < 1) requestAnimationFrame(frame);
		- else setSidebarwidth(toPx);}
		- requestAnimationFrame(frame);}

	- 사이드바가 부드럽게 움직이게 만드는 애니메이션 엔진
	- function animateSidebarwidth(toPx, duration = 300){ 에서 매개변수 toPx은 목표 폭, duration은 총 재생시간
	- const fromPx = getCurrentSidebarwidth( ) || 0;
		- 지금 사이드바 너비가 몇 픽셀인지 가져오기
	- if (fromPx === toPx) 목적지와 지금 너비가 같으면 함수 종료
	- const start = performance.now( );
		- 애니매이션 버튼을 누르는 순간의 시간을 정밀하게 기록
		- performane.now()는 일반 시계보다 훨씬 정확해서 애니메이션을 끊김 없이 계산할 때 필수
	- function frame(now){
		- 브라우저가 화면을 새로 그릴 때마다 실행되는 함수
	- const progress = Math.min(1, (now - start)/ duration);
		- 전체 시간 중에 얼마나 지났는지 계산
		- now - start는 현재 시각에서 애니메이션 시작 시간을 뺌
		- 진행된 시간, 지나온 시간 도출 도출
		- 지나온 시간 나누기 총 재생시간은 진행율
		- 즉, 시간이 이정도 지났으니까 사이드바를 그에 맞춰 요만틈 옮겨야 겠네 가 가능해짐
		- Math.min(1,
			- 100%를 넘지 않도록 안전장치
			- 애니매이션 총 진행시간이 300ms인데 마지막 frame이 실행도니 순간의 시간이 310이라면 진행율이 100을 넘어버림
			- Math.min을 통해 1과 계산값 중 작은 값을 골라 progress에 대입
	- const cur = fromPx + ( toPx - fromPx ) * progress;
		- 지금 이 순간의 사이드바의 너비는 몇이어야하는지 구함 -> 현재위치
		- toPx - fromPx는 총 움직여야 할 거리
		-  * progress; 그 거리중에서 몇 퍼센트나 왔는지 구함
		- 마지막으로 시작점을 더해줌
		- 시작점에서 몇 퍼센트 왓는지 구해서 좌표
	- setSidebarwidth(cur);
		- 바로 위에서 계산한 현재 위치를 가지고 아까 배운 함수 호출
		- css 너비 값을 변환하는 함수
	- if (progress < 1) requestAnimationFrame(frame);
		- 진행율이 100%보다 작으면 frame함수 지속적으로 호출
		- else setSidebarwidth(toPx);}
			- 진행율이 100%가 되었거나 도착했을 때 실행
			- 더 이상 requestAnimationFrame을 부르지 않기 때문에 반복되던 함수 호출을 멈추고 애니메이션이 끝남
	- requestAnimationFrame(frame);}
		- 모든 시스템의 첫 시동을 거는 코드
		- 이 줄이 실행되어야만 frame함수가 처음으로 브라우저의 부름을 받고 일을 시작하게 됨
		- 

- function collapse( ){
	- const cur = getCurrentSidebarwidth( );
	- if (cur && cur > 0) writeLastwidth(cur);
	- sidebar.classList.add("is-collapse");
	- animateSidebarwidth(0);
	- syncMenuBtnvisibility( );}

	- 사이드바를 접는 기능
	- const cur = getCurrentSidebarwidth( );
		- 현재 사이드바의 너비가 몇 픽셀인지 측정
	- if (cur && cur > 0) writeLastwidth(cur);
		- 너비 값이 제대로 측정됐고 0보다 크다면 그 값을 저장소에 저장
	- sidebar.classList.add("is-collapse");
		- 사이드바 태그에 is-collapse라는 클래스 붙이기
		- css 목표
	- animateSidebarwidth(0);
		- 위에서 만들었던 애니메이션 함수를 통해 0까지 자연스럽게 줄임
	- syncMenuBtnvisibility( );
		- 사이드바가 사라졌으니 사이드바를 다시 열 수 있는 버튼을 보여줄지 말지 상태를 맞춰주기
		- 

- function resetWidth( ){
	- sidebar.classList.remove("is-collapse");
	- const remembered = lastSidebarwidth && lastSidebarwidth > 0 ? lastSidebarwidth : defaultSidebarwidth( );
	- animateSidebarwidth(remembered);
	- syncMenuBtnVisibility( );}

	- 사이드 바를 다시 펼치는 함수
	- 사이드 바에 붙었던 is-collapse 클래슺 ㅔ거
	- lastSidebarwidth && lastSidebarwidth > 0 ? lastSidebarwidth : defaultSidebarwidth( );
		- 저장소에 사이드바의 너비가 저장되어 있고 그 값이 0보다 크면 그 값을 쓰고 아니면 디폴트 값을 써서 remembered 변수에 담기
	- animateSidebarwidth(remembered);
		- 결정된 너비까지 사이드바르 부드럽게 펼치기
	- syncMenuBtnVisibility( );
		- 메뉴 열기버튼을 숨기거나 표시하거나 상태 맞추기

- function syncMenuBtnVisibility( ){
	- if (!menuBtn) return;
	- const show = state.isMobile || sidebar.classList.contains("is-collapsed");
	- menuBtn.style.display = show ? "grid" : "none"; }

	- 메뉴 버튼 요소를 찾지 못했으면 함수 종료
	- state.isMobile
		- 지금 모바일 환경인가
	- sidebar.classList.contains("is-collapsed");
		- 또는 사이드바가 지금 접혀있는가
	- show가 true이면 디스플레이 방식을 grid로 설정해서 버튼을 나타나게 함

## 드롭 다운 메뉴, 서식 툴바
- let currentDropdown = null;
	- 전역 변수/ 현재 열려 있는 드롭다운 메뉴 참조
	- 단일 메뉴 원칙: 새 메뉴 열기 전 기존 메뉴 반드시 닫음
- function openDropdownMenu(anchorEl, doc, labelEl){
	- closeDropdownMenu( );
	- const rect = anchorEl.getBoundingClientRect( );
	- const menu = el("div", { className: "dropdown-menu open" });
	- const miRename = el ("div", { className: "menu-item", textContent: " Rename (F2)", });
	- const miStar = el("div", { className: "menu-item", textContent: doc.starred ? "Unstar" : "Add to favorites", });
	- const miDel = el("div", { className: "menu-item", textContent:  "Delete (move to trash)", });
	-  const sep = el("div", { className: "menu-sep" });
	-  const editedBy = el("div", { className: "menu-item muted" });
	- editedBy.textContent = "Last edited by: Guest"; 

	- closeDropdownMenu( );으로 새 메뉴 열기 전에 이미 열려있는 다른 메뉴 닫기
	- const rect = anchorEl.getBoundingClientRect( );
		- 메뉴를 띄울 기준 버튼(acchorEl)이 화면 어디에 잇고 크기가 얼마인지 계산
		- getBoundingClientRect( )는 해당 요소의 위치와 크기에 대한 8가지 정보가 담긴 보관함(객체)를 돌려줌
			- 모든 수치는 px단위
			- y축, x축, bottom, right, left, width, height
		- 가장 중요한 특징은 뷰포트 기준
			- 문서 전체가아니라 지금 눈에 보이는 브라우저 화면 기준 -> 스크롤하면 값 변함
	- const menu = el("div", { className: "dropdown-menu open" });
		- 메뉴 아이템들을 담을 컨테이너 생성
	- 메뉴칸들 생성
	- sep은 구분선 
	- editedBy는 정보를 보여줄 칸, 글자색은 좀 흐릿하게, 칸에 내용 채워넣기





	- miRename.addEventListener("click", (e) => {
		- e.stopPropagation( );
		- inlineRename(doc.id, labelEl);
		- closeDropdownMenu( ); } );
	- miStar.addEventListener("click", (e) => {
		- e.stopPropagation( );
		- updateDoc(doc.id, { starred: !doc.starred } ); 
		- if (state.activeId === doc.id) {
			- const d = findDoc(doc.id);
			- starBtn.textContent = d.starred ? " * " : "x "; }
		- renderTrees( );
		- clsoeDropdownMenu( ); } );
		- 
	- miDel.addEventListener("click", (e) => {
		- e.stopPropagation( );
		- confirmModal(`move "${doc.tilte}" and its subpages to trash?, ( ) => {
			- archiveDoc(doc.id);
			- toast("Note moved to trash!");
			- if (state.activeId === doc.id) navigateTo(null);
			- renderTrees( );
			- renderTrash( ); } ); 
		- closeDropdownMenu( ); } );

	- 메뉴 클릭 이벤트들
	- 

	- menu.append(miRename, miStar, miDel, sep, editedBy);
	- document.body.appendChild(menu);
	- const top = rect.bottom + 6;
	- const left = Math.min(rect.left, window.innerWidth - 260);
	- menu.style.top = top + "px";
	- menu.style.left = left + "px";

	- currentDropdown = menu; }

	- 아까 만든 메뉴들을 메뉴 컨테이너에 추가하기
	- 완성된 메뉴 컨테이너를 실제 웹페이지 bodydp sjgrl
	- 메뉴가 나타날 위치 게산하여 top과 left 변수에 담고
	- 그 좌표를 실제 메뉴의 스타일로 적용시킴
	- 지금 열려있는 메뉴를 currentDropdown 에 기록
	- 나중에 다른 곳을 클릭하거나 다른 메뉴를 열 때 어떤 메뉴를 닫을지 알기 위해서

-  function closeDropdownMenu( ){
	- if (currentDropdown){
		- currentDropdown.remove( );
		- currentDropdown = null;} 
- document.addEventListener("click", closeDropdownMenu);
	- 지금 화면에 currentDropdown이 있으면 currentDropdown을 지우고 그 변수도 비우기
	- 여백 클릭 시 메뉴가 닫히는 기능도 구현
	- 

## 서식 툴바 완전 분석 - Bold, 목록, 인용, 코드, 할 일 버튼 동작 관리
- $("#toolbar")?.addEventListener("click", (e) => {
	- const btn = e.target.closest("button");
	- if (!btn) return;
	- const cmd = btn.dataset.cmd;
	- const fmt = btn.dataset.format;
	- editor.focus( );
	- 
	- if (cmd){
		- document.exeCommand(cmd, false, null);
		- saveEditor( );
		- return;}
	- if (fmt){
		- document.exeCommand("formatBlock", false, fmt === "p" ? "p" : fmt ); 
		- saveEditor( );
		- return; } } );

	- 텍스트 편집기 상단에 있는 툴바를 선택했을 때의 로직
	- 아이디가 toolbar인 요소를 찾아서 그 안에서 클릭이 일어나면 다음 일들을 시작하라는 것
	- ?.을 통해 화면에 툴바가 없어도 에러를 내지않고 조용히 넘어가기
	- 클릭된 요소(e.target)에서 가장 가까운 부모버튼(button)을 찾아내서 btn에 담기
		- 버튼 안에 아이콘이나 글자가 들어있는 경우 그들을 선택해도 버튼을 누른 것으로 판단
	- 클릭된 곳이 버튼이나 버튼 안쪽이 아니라면 함수 종료
	- 버튼의 data속성 즉 data-cmd 혹은 data-format을 읽어와서 cmd/ fmt에 담기
	-  editor.focus( );
		- 버튼을 누르는 순간 포커스가 툴바로 옮겨가는데, 이를 다시 편집창으로 옮겨서 글을 바로 이어쓸 수 있도록 해주는 매너있는 코드
	- if (cmd){
		- 만약 cmd정보가 있다면 브라우저에게 그 명령을 실행하라고 함
		- document.exeCommand(cmd, false, null);
			- exeCommand(명령어, 사용자 UI여부, 추가값)
			- 명령어 부분에는 무엇을 할지 입력
			- 사용자 UI여부는 브라우저 기본 UI를 보여줄 지 말지인데 보통 false
			- 추가 값은 폰트 크기나 색상처럼 추가 정보가 필요할 때 넣음
	- if (fmt){
		- 글자 모양이 아니라 문단 전체의 성격을 바꾸는 역할
		- 만약 버튼이 data-format 정보를 갖고있다면 아래 내용 실행
		- 보통 제목이나 일반 본문, 인용구 등이 여기에 해당
		- **`"formatBlock"`**: 브라우저에게 "지금 커서가 있는 이 줄(블록) 전체의 태그를 바꿔줘"라고 명령하는 특수한 명령어
		- fmt === "p" ? "p" : fmt
			- 만약 넘겨받은 값이 p라면 그냥 p를 쓰고 아니라면 h1이나 h2같은 해당 값을 그대로 쓰기
- cmd는 드래그한 글자들, fmt는 커서가 있는 줄 전체

- $("#bulletsBtn")?.addEventListener("click", ( ) => {
	- editor.focus( );
	- document.execCommand("insertUnorderedList");
	- saveEditor( ); } );

	- 글머리 기호 매기기 
	- document.execCommand
		- 브라우저에게 명령
		- nsertUnorderedList는 점 모양의 글머리 기호 목록을 넣어줌

- $("#numbersBtn")?.addEventListener("click", ( ) => {
	- editor.focus( );
	- document.exeCommand("insertOrderdList");
	- saveEditor( );})

- $("#codeBtn")?.addEventListener("click", ( ) => {
	- editor.focus( );
	- document.exeCommand("formatBlock", false, "PRE");
	- saveEditor( ); } );
	- 지금 커서가 있는 줄을 코드 전용 태그인 < pre >로 감싸라는 명령

- $("#quoteBtn")?.addEventListener("click", ( ) => {
	- editor.focus( );
	- document.exeCommand("formatBlock", false, "BLOCKQUOTE");
	- saveEditor( ); } );
	- 지금 커서가 있는 줄을 < blockquote >의 인용구 태그로 감싸라는 명령

- $("#todoBtn")?.addEventListener("click", ( ) => {
	- const box = document.createElement("div");
	- box.innerHTML = `<label><input type = "checkbox"> <span>TO-do </span></label>`;
	- const sel = window.getSelection( );
	- if (!sel.rangeCount) {
		- editor.appendChild(box);
	else {
		sel.getRangeAt(0).insertNode(box);}
		saveEditor( ); } } );

	- 브라우저 내장 명령어가 없어서 직접 만드는 방식
	- 새로운 div 박스 생성
	- 그 박스 안에 체크박스와 todo라는 글자 조립해서 집어넣음
	- sel은 지금 현재 사용자의 커서 위치 정보 저장
	- if (!sel.rangeCount) {
		- 만약 커서 위치가 어딘지 찾을 수 없다면
		- 에디터의 맨 마지막 부분에 체크박스 생성
		- rangeCount는 사용자가 선택한 영역이 몇 개인지 알려주는 숫자
			- 만약 글자를 드래그했거나 에디터 안에서 커서가 깜빡이고 있으면 숫자는 보통 1
			- 선택된 곳이 전혀 없다면 0 -> false
	- sel.getRangeAt(0).insertNode(box);}
		- getRangeAt은 여러 개의 선택 영역 중에서 0번 즉 첫 번째 영역의 정보를 가져오라는 뜻
		- 그 위치에 insertNode로 체크박스 끼워넣기
		- 

## 이모지 아이콘과 즐겨찾기
- function openEmojiPicker( ){
	- const btn = document.getElementById("iconBtn");
	- if (!btn || !emojiPicker) return;
	- const rect = btn.getBoundingClientRect( );
	- emojiPicker.style.left = Math.min(rect.left, window.inner
	  Width - 340) + "px";
	- emojiPicker.style.top = rect.bottom + 8 + "px";
	- emojiPicker.classList.add("open"); }

	- 이모지 선택창을 화면의 적절한 위치에 나타나게 만드는 함수
	- 화면에서 이모지버튼을 찾아서 btn이라는 변수에 담기
		- 이 버튼 바로 아래에 이모지 창을 띄워야해서 기준점이 되는 버튼을 먼저 찾는 것
	- 버튼이 없거나 이모지 선택창 객체가 안 만들어졌다면 함수 종료
	- btn의 정확한 좌표 가져와서 rect 변수에 담기
	- Math.min(rect.left, window.inner
	  Width - 340) + "px"
		- 버튼의 좌표 왼쪽 끝 또는 전체 화면 너비에서 이모지 창 너비만큼 뺀 값
		- 둘 중에서 더 작은 값을 선택
		- 이모지 창이 오른쪽 밖으로 빠져나가는 것 방지
	- emojiPicker.classList.add("open");
		- 이모지 선택창에 open이라는 클래스 추가해서 이모지 창이 화면에 보이도록

- function closeEmojiPicker( ){
	- emojiPicker?.classList.remove("open");}

- document.getElementById("iconBtn")?.addEventListener("click", (e) => {
	- e.stopPropagation( );
	- buildEmojiGrid( );
	- openEmojiPicker( );});

	- 아이콘 버튼을 클릭했을 때 일어나는 이벤트
	- 부모로 이벤트 전파되는 것 방지
	- buildEmojiGrid( );
		- 창을 열 때마다 최신 이모지 목록 준비
	- openEmojiPicker( );}
		- 이모지 창을 화면에 띄움

- document.addEventListener("click", (e) => {
	- if (
		- emojiPicker && !emojiPicker.contains(e.target) && e.target.id !== "iconBtn" ) 
	- closeEmojiPicker( ); });

	- 화면 어디든 클릭했을 때 창을 닫는 것
	-  일단 이모지 창이 존재하고, 클릭한 지점이 이모지 창 안쪽이 이니며, 클릭한 곳의 id값이 이모지 창을 여는 버튼이 아닐 때 이모지 창 닫기 

- function buildEmojiGrid( ){
	- if (!emojiGrid) return;
	- emojiGrid.innerHTML = "";
	- EMOJI.forEach((em) => {
		- const b = el("button", { textContent: em } );
		- b.addEventListener("click", ( ) => {
			- if (state.activeId) {
				- updateDoc(state.activeId, { icon:em } ); 
				- const btn = document.getElementById("iconBtn");
				- if (btn) btn.textContent = em; 
				- renderTrees( );}
				- closeEmojiPicker( ); } ) ;
		- emojiGrid.appendChild( b ); } ); }
	- 이모지 선택창의 내부를 실제로 채우고 기능을 부여하는 핵심 함수
	-  if (!emojiGrid) return;
		- 이모지들을 담을 그릇이 없으면 함수 종료
	- emojiGrid.innerHTML = "";
		- 이모지 그릇 안에 들어있던 기존 내용물 싹 비우기
		- 창을 열 때마다 실행하여 내용물들이 호출될 때마다 추가되는 것 방지
	- EMOJI라는 목록 배열 안에 담긴 이모지들을 하나씩 꺼내서 반복작업 시작
		- **`em`**: 반복문 안에서 현재 처리 중인 이모지 문자 하나(예: "😀")를 의미
	- const b = el("button", { textContentL em } );
		- 새로운 버튼 요소를 만들고 그 안에 이모지 하나(em)을 글자로 넣기
	- b를 클릭하면
		- if (state.activeId) {
			- 사용자가 어떤 문서를 선택해서 읽고 있는 경우
			- updateDoc(state.activeId, { icon:em } ); 
				- 그 문서의 아이콘 데이터 베이스 변경
			- const btn = document.getElementById("iconBtn");
				- 문서의 iconBtn아이디를 가진 요소 btn변수에 담기
				- 화면 상단에 있는 대표 아이콘 버튼
			- if (btn) btn.textContent = em;
				- 그 버튼이 있다면 그를 em으로 변경
		- 사이드 바 목록 다시 그리고
		- 이모지 선택창 닫기
	- emojiGrid.appendChild( b ); } ); }
		- 만든 버튼을 이모지그리드에 담기

- starBtn?.addEventListener("click", ( ) = >{
- if (!state.activeId) return;
- const d = findDoc(state.activeId);
- updateDoc(state.activeId, { starred: !d.starred } );
- const nd = findDoc(state.activeId);
- starBtn.textContent = nd.starred ? " 별 " : " 별 x " ; 
- renderTrees( ); } );

	- 별 버튼을 누르면 이벤트 시작
	- 만약 열려있는 문서가 없다면 함수 종료 
	- 현재 문서의 원래 상태가 어던지 데이터베이스에서 찾아와 d에 담기
	- 별이 있었다면 없게, 없었다면 있게 데이터 베이스를 업데이트
	- 방금 업데이트 된 데이터 상태를 다시 nd에 담ㄱ시
	- 버튼의 글자를, nd.starred가 true면 별을 붙이고 반대면 별 없애기
	- 사이드 바 목록 다시 그리기

## 새 페이지 생성 - 하위 문서 , 루트 문서 추가
- newChildBtn?.addEventListener("click",( ) => {
	- const pid = state.activeId || null;
	- const id = createDoc( { title: "Untitled", parentId: pid } );
	- if (pid) state.expanded[pid] = true;
	- toast("New subpage created:", "success");
	- navigateTo(id); });

	- 현재 내가 보고있는 페이지 내부에 새로운 하위 페이지를 만드는 기능
	- 하위 페이지 생성버튼을 클릭하면 실행되는 이벤트
	- const pid = state.activeId || null;
		- 지금 보고 있는 페이지의 ID를 부모 id로 설정, 없다면 null로
	- const id = createDoc( { title: "Untitled", parentId: pid } );
		- 데이터 베이스에 새 문서 생성
		- 제목은 Untitled로 하고 부모 아이디는 방금 정한 pid로 설정
		- 이 명령이 실행되면 지금 보고있는 페이지 밑에 하위 문서 생성
	- if (pid) state.expanded[pid] = true;
		- 만약 부모 페이지가 있다면
			- 그 부모 페이지의 쳘침 상태를 true로 설정 
			- state.expanded 목록 들(사전)에서 pid 의 상태를 변경
	- 알람을 띄우고 생성한 함수로 이동

- const actionAddPage = document.getElementById("actionAddPage");
- const actionCreateRoot = document.getElementById("actionCreateRoot");
- [actionAddPage, actionCreateRoot].forEach( (btn) => {
	- if (btn){
		- btn.addEventListener("click", ( ) => {
			- const id = createDoc( { title: "Untitled", parentId: null } ); 
			- toast("New page created!", "success" );
			- navigateTo(id); } ); } });

	- 가장 최상위 페이지를 만드는 버튼들에 기능을 부여하는 함수
	- [actionAddPage, actionCreateRoot].forEach(btn) => {
		- 두 버튼들을 하나의 리스트로 묶어서 반복문
	- 만약 btn이 있다면 
		- 즉 [ ] 배열 안에 있는 버튼들이 실제로 있다면
		- 이벤트 함수 등록
		- const id = createDoc( { title: "Untitled", parentId: null } )
			- 이름이 Untitled인 문서, 부모 아이디는 null -> 루트에 생성
## 휴지통 시스템 해부 - 삭제, 복원, 영구삭제, 팝오버 위치
- const trashTrigger = $("trashTrigger");
	- 사이드바 하단/ 네비게이션의 휴지통 아이콘 버튼, 목록 열기/ 닫기 트리거
- const traghPopover = $("trashPopover);
	- 삭제 문서 리스트를 보여주는 팝오버 영역 (평소 숨김 -> 클릭 시 표시)
	- 이 두 요소를 미리 상수로 캐싱해두는 이유는 이후 여러 함수에서 반복 접근하므로 빠르게 참조하기 위함
	- 성능과 가독성 향상, 불필요한 DOM 탐색 감소, 코드 간결 명확

- function positionTrashPopover( ){
	- if (!trashTrigger || !trashPopover) return;
	- const rect = trashTrigger.getBoundingClientRect( );
	- const bottom = window.matchMedia("(max-width: 768px)").matches;
	- if (bottom){
		- trashPopover.style.left = 
			- Math.min(rect.left, window.innerWidth - 340) + "px"; 
		- trashPopover.style.top = rect.bottom + 8 + "px";}
	- else { 
		- trashPopover.style.left = Math.min(rect.right + 8, window.innerWidth - 340) + "px";
		- trashPopover.style.top = rect.top + "px"; }

	- 휴지통 팝오버의 위치를 결정하는 함수
	- 가장 먼저 실행되는 부분은 if 절
		- trashTrigger 휴지통 버튼과 팝오버 창 중 어느 하나라도 없으면 함수 종료
	- rect 변수에 화면상 휴지통 버튼의 위치를 구함
		- 반환 값은 top/left/right/bottom/width/height
	- window.matchMedia("(max-width: 768px)").matches;
		- matchMedia 메서드는 현재 화면이 모바일인지 아닌지 판별
		- 뷰포트가 768보다 작거나 같으면 true 반환
		- 이는 모바일과 데스크탑에서 팝오버를 표시하는 위치가 달라져야 하기 때문에 필요
	- if (bottom){
		- 조건문 분기에서 bottom이 true 즉 모바일인 경우 먼저 처리
		- trashPopover.style.left = 
			- Math.min(rect.left, window.innerWidth - 340) + "px"; 
				- 가로 위치 설정
				- 버튼의 왼쪽 좌표를 기준으로 삼되, (rect.left)
				- 현재 내 브라우저 창의 전체 너비(window.innerWidth) 에서 휴지통 팝오버의 너비(340px)을 뺀 값
				- Math.min 을 통해서 괄호 안 두 숫자 중 더 작은 숫자를 선택
		- trashPopover.style.top = rect.bottom + 8 + "px";}
			- 세로 위치는 버튼 아래쪽 8px 여백을 두고 위치
	- else { 
		- 데스크탑 환경인 경우 팝오버가 버튼 오른쪽에 나타나도록 배치
		- trashPopover.style.left = Math.min(rect.right + 8, window.innerWidth - 340) + "px";
			- 가로 위치는 버튼 오른쪽에서 8px 떨어진 위치
			- 창의 전체 너비에서 팝오버 창의 너비를 뺀 값
			- 둘 중 더 작은 값을 left위치로 
		- trashPopover.style.top = rect.top + "px"; }
			- 세로위치는 버튼과 같은 높이에 맞춰 정렬
## 휴지통 팝오버 전체 흐름 - 토글, 리사이즈, 외부클릭제어
- function toggleTrash( ){
	- if (!trashPopover) return;
	- if (trashPopover.classList.contains("open")){
		- trashPopover.classist.remove("open");
		- return;}
	- positionTrashPopover( );
	- trashPopover.classList.add("open"); }

	- 팝오버의 열림과 닫힘을 실제로 제어하는 핵심 함수
	- DOM 구조상 팝오버 요소가 없을 때 함수 종료
	- if (trashPopover.classList.contains("open")){
		- 현재 팝오버가 열려있는지 판단
		- 열림 상태면 open 클래스를 제거하고 즉시 함수 종료
		- 이렇게 하면 버튼을 한 번 누르면 열리고 다시 누르면 닫히는 토글 구조가 완성
	- positionTrashPopover( );
		- 반대로 열려있지 않은 상태라면 위 함수를 호출해 화면상 위치를 버튼 기준으로 계산
	- trashPopover.classList.add("open"); }
		- add 메서드로 open 클래스를 붙여 css로 팝오버 요소가 보이도록 구현
		- 

- trashTrigger?.addEventListener("click", (e) => {
	- e.stopPropagation( );
	- toggleTrash( );});

	- 토글 함수를 실제 사용자 행동에 연결하는 단계
	- 휴지통 버튼에 클릭 이벤트를 바인딩하는 코드
	- 클릭 버블링 차단
	- 버블링을 차단하고 버튼 클릭은 toggleTrash만 실행

- window.addEventListener("resize", ( ) => {
	- if (trashPopover?.classList.contains("open")) positionTrashPopover( );} )
	- 팝오버는 반응형 레이아웃에서도 위치가 올바르게 유지되어야 함
	- 창 크기를 변경할 때 팝오버가 열린 상태라면 -> 위치를 다시 계산하는 로직

- document.addEventListener("click", (e) => {
	- if (
		- trashPopover && ! trashPopover.contains(e.target) && e.target !== trashTrigger )
		- trashPopover.classList.remove("open");});
		- 버튼 외부를 눌렀을 때 자동으로 닫히는 전역 이벤트 핸들러
		- 핵심은 세 가지 조건
			- 팝오버가 존재해야함
			- 클릭 대상이 팝오버 내부가 아니어야 함
			- 누른 대상이 휴지통 버튼이 아니어야 함
			- 이 조건들이 모두 만족되면 open 클래스가 제거되고 팝오버 닫힘
			- 

## 휴지통 목록 & 실시간 검색 - renderTrash와 입력 위임, 복원 영구 삭제 흐름
- 실제 목록을 만드는 renderTrash와 검색 입력 이벤트를 연결하는 전역 인풋 리스너
### renderTrees()
- function renderTrees( ){
	- 휴지통 목록을 화면에 그려주는 함수
	- const list = $("trashList");
		- 휴지통 아이템들을 담을 상자 요소인 trashList를 가져와서 list라는 변수에 담기
		- 화면에 목록을 뿌려줄 도화지를 준비하는 것
	- 
	- if ( !list ) return;
		- 만약 리스트라는 상자가 화면에 없으면 함수 종료
		- 즉, HTML요소인 trashList가 없으면 함수 종료
	- const search = ($("trashSearch")?.value || "").trim( ).toLowerCase( );
		- ID가 trashSearch인 입력창에 입력된 글자, 검색창이 없거나 비어있으면 빈글자의 앞뒤 공백을 없애고 모두 소문자로 바꾼 뒤 search라는 변수에 저장
	- list.innerHtml = "";
		- list에 있던 기존의 내용들 지우기
		- 새로 목록을 그리기 전에 비우기
		- 중복으로 불러와지는 것을 막기 위함
	- const filtered = state.trash.filter( (d) => d.title.toLowerCase( ).includes(search) );
		- 휴지통 데이터(state.trash)중에서 필터링하기
		- 데이터의 제목을 소문자로 변환한 값에 아가 찾은 검색어가 포함된 문서들만 골라서 필터링한 후 filtered라는 변수에 담기

	- if (filtered.length === 0) {
		- 위에서 필터링 한 결과가 0일 때
		- 휴지통이 아예 비어있거나 검색어에 맞는 결과가 없을 때
		- const p = el("p", {
			- className: "muted",
			- textContent: "No documents found",});
				- 화면에 글자를 보여줄 새 문단 태그 만들기
				- css를 조절하기 위해 muted 클래스 붙이기
				- 그 문단 안에 찾는 문서가 없습니다 라는 안내 문구 적어 넣기
		- list.appendChild(p);
			- 아까 비워둔 휴지통 상자(list)안에 이 안내 문구 집어 넣기
			- 사용자에게 아무 것도 없다는 사실을 시각적으로 보여줌
		- return;)
			- 결과가 없으니 이 밑에 이어질 목록 그리기 코드는 실행할 필요가 없으므로 여기서 함수 종료
			- 
	- filtered.forEach(doc) => {
		- 검색된 문서들을 하나씩 꺼내서 doc이라고 부르고 이어질 작업 반복
		- const row =  el("div", { className: "trash-row" } ); 
			- 문서 한 줄을 통째로 감쌀 커다란 상자를 만들고 trash-row라는 클래스 붙이기
			- 이 상자 안에 제목, 복원버튼, 삭제 버튼 등이 들어갈 것
		- const title el("span", { textContent: doc.title, style: "flex;1 1 auto; min-width:0, } );
			- 문서 제목을 담을 칸 만들기
			- 그 칸 안에 실제 문서의 제목을 적어 넣음
			- flex: 1 1 auto;은 제목이 차지할 수 있는 공간을 최대한 넓게 쓰라는 의미
				- 첫 번째 1은 상자에 빈 공간을 다 차지하겠다는 의미
				- 두 번째 1은 상자가 좁아지면 제목이 차지하는 공간도 줄어들겠다는 의미
				- 세 번째 auto는 제목이 가진 글자 길이에 맞춰 자리를 잡아달라는 의미
			- min-width:0,
				- 보통 css에서 글자 상자(span, div)등은 안에 들어있는 글자 길이 보다 줄어들 수 없게 설정되어있음
				- 최소 너비를 0으로 지정해서 줄어들 수 있게 설정
		- const info = el("span", {
			- 마찬가지로 span 태그 생성 
			- className: "muted",
			- textContent: doc.__ origParentId && !existsInDocs(doc.__ origParentId) ? " -> 복원 시 루트로 이동" : "", } );
				- doc.__ origParentId은 이 문서가 삭제되기 전에 가졌던 부모의 ID
				- existsInDocs는 지금 살아있는 문서 목록에 그 부모 아이디가 존재하는지 체크하는 함수 -> !이 붙었으니 목록에 존재하지 않는다면
				- 즉, 원래 부모가 있었고 그 부모가 지금 문서 목록에 존재하지 않는다면 복원시 루트로 이동이라는 글자를 span 태그의 내용으로
				- 그러나 이 조건이 거짓이면 아무메세지도 출력하지 않음
		- const acts = el("div", { className: "trash-actions" });
			- 버튼 도구함 만들기
			- 사용자가 직접 누르게 될 복원, 영구 삭제 등을 담는 상자 만들기
		- const restore = el("div",
			- { className: "icon-btn",
			- title: "Restore",  
			- textContent: "화살표" } );
				- 버튼의 모양을 아이콘 모양으로 설정하기 위해 클래스 붙이기
				- 마우스를 버튼 위에 올렸을 때 복원이라는 설명 풍선이 뜨게 함
				- 화살표 모양의 아이콘을 버튼의 내용으로 설정
				- 위 div 요소를 생성
		- const del = el("div", {
			- className: "icon-btn",
			- title: "Delete permanently",
			- textContent: "휴지통",});
				- 영구 삭제 기능을 할 버튼
				- 마우스를 올리면 영구적으로 삭제라는 경고 문구 
				- 휴지통 아이콘을 버튼의 내용으로 설정
		- restore.addEventListener("click", (e) => {
			- 복원 버튼 클릭 이벤트
			- e.stopPropagation( );
				- 버블링 전파 막기 
			- restoreDoc(doc.id);
				- 복원 기능을 담당하는 함수
				- 대상은 휴지통에 있는 이 문서의 아이디
			- renderTrees( );
			- renderTrash( ); });
				-  사이드바와 휴지통 목록을 렌더링하여 화면에 반영
		- del.addEventListener("click", (e) => {
			- 영구 삭제 버튼 클릭 이벤트
			- e.stopPropagation( );
			- confirmModal(`Delete "${doc.title}" permanently?`, ( ) => {
				- 영구 삭제 여부를 묻는 확인창 띄우기
				- confirmModal(메세지, 실행할 함수)
				- 사용자가 확인을 눌렀을 때만 함수 실행


				- removeDoc(doc.id);
					- 데이터 베이스에서 영구 삭제하는 함수
				- toast("Note deleted!", "error");
					- 화면 구석에 알림창 띄우기
				- renderTrash( ); }); });
					- 삭제가 완료되었으니 휴지통 목록 다시 그리기
		- acts.append(info, restore, del);
			- 버튼 바구니에 안내 메세지, 복원 버튼, 삭제 버튼 순서대로 담음
			- 예를 들면 [ 안내문구 | ↩️ | 🗑️ ]
		- row.append(title, acts);
			- 한 줄 상자에 제목과 방금 만든 버튼 묶음을 넣음
		- row.addEventListener("click", ( ) => {
			- 만약 줄 전체를 아무데나 클릭하면 
			- trashPopover?.classList.remove("open");
				- 열려 있던 휴지통 팝업창을 닫음
			- navigateTo(doc.id); });
				- 해당 문서가 있는 곳으로 화면을 이동시킴
		- list.appendChild(row);  }); }
			- 완성된 줄을 list에 붙이기 
			- 이 과정이 forEach를 통해서 문서 개수만큼 반복
- document.addEventListener("input", (e) => {
	- if (e.target && e.target.id === "trashSearch") renderTrees( ); });

	- renderTrees 함수를 언제 실행할 것인가를 결정하는 이벤트 리스너
	- 이 문서 전체에서 사용자가 뭔가 입력하는 사건이 발생하는지 감시하라 
	- 만약 입력 사건이 발생하면 그 사건 정보(e)를 들고 이 함수 실행
	- 방금 글자가 입력된 곳의 id가 trashSearch인가
	- 그렇다면 renderTrees 함수 실행 
- 왜 검색창에 직접 리스너를 붙이지 않고 document에 붙였는가?
	- 직접 바인딩의 한계: 인풋에 리스너 직접 붙이면 다시 열 때 연결 끊기 발생
		- list.innerHTML = "";을 해서 화면을 싹 지우고 다시 그림
		- 검색창도 휴지통을 열고 닫을 때마다 새로만들어지는 구조
		- 창을 닫고 다시 열 때 리스너는 이전 검색창에 붙어있으므로 이벤트 연결이 끊김
		- 이 문제를 해결하기 위해 절대 사라지지 않는 document 문서 전체에 이벤트를 위임
	- 문서 전체에 input 이벤트 위임하고 e.target && e.target.id === "trashSearch"을 통해서 휴지통 검색창만 식별
	- 조건 만족시 renderTrees 재호출 
	- 검색 파싱, 필터 즉시 재실행
	- 한 글자 입력마다 실시간 필터링, 붙였다 떼는 UI에서도 안정적 이벤트 관리 

## Favorites Modal 구현 - 목록 정렬, 빠른 이동, 닫기 UX
- 사용자가 사이드바나 내비게이션 바에서 Favorites 버튼을 눌렀을 때 전체 화면을 덮는 오버레이가 열리고 즐겨찾기한 문서들이 목록으로 정렬되어 표시
- 여기서 별을 해제하거나 문서를 클릭해 바로 이동할 수 있도록 함

### 핵심 DOM 변수 캐싱
- const favoritesOverlay = $("#favoritesOverlay");]
	- 전체 오버레이
- const favoritesListModal = $("#favoritesListModal");
	- 즐겨찾기 목록 컨테이너
- const openFavoritesModalBtn = $("#openFavoritesModal");
	- 모달 열기 버튼
- const favoritesCloseBtn = $("#favoritesClose");
	- 모달 닫기 버튼
### 즐겨찾기 모달 열고 닫기 함수
- function openFavoritesModal( ){
	- buildFavoritesModal( );
		- 현재 상태 기준 목록 재 빌드
		- 목록을 매번 새로 그리는 이유는 사용자가 직전에 별을 추가하거나 제거했을 수도 있기 때문에 올바른 상태 반영을 위해서 
	- if (favoritesOverlay) favoritesOverlay.style.display = "grid"; }
		- 즐겨찾기 화면이 페이지에 존재하는지 확인한 후
		- style.display = "grid";을 통해서 display(보여주기) 상태를 grid로 바꿔서 화면에 오버레이를 보이게 함
		- 평소에는 display: none 으로 숨겨져 있음
		- 즐겨찾기 화면이 페이지에 존재하는지 확인한 후
- function closeFavoritesModal( ){
	- if (favoritesOverlay) favoritesOverlay.style.display = "none"; }
	- display = "none"으로 화면에서 숨김
### 즐겨찾기 모달을 구현하는 핵심 함수
- function buildFavoritesModal( ){
	- if (!favoritesListModal) return;
		- 즐겨찾기 목록을 담을 상자가 없으면 함수 종료
	- favoritesListModal.innerHTML = "";
		- 새로 즐겨찾기 목록을 그리기 전에 예전에 그려놨던 목록 초기화
	- const favs = state.docs.filter( (d) => d.starred ).sort( (a,b) => a.title.localeCompare(b.title));
		- 모든 문서 중에서 d) => d.starred 즉 별표가 true 인것만 필터
		- 골라낸 것들을 sort로 제목 순대로 정렬
		- sort(a, b)
			- a는 비교 대상 첫 번째
			- b는 비교 대상 두 번째
			- 둘 중 누가 앞에 와야하는지 물어보는 과정
		- localeCompare은 사용자의 언어 설정에 맞춰 글자를 비교하겠다는 의미 
			- 보통 ㄱㄴㄷ, abc 순
	- 
	- if (favs.length === 0){
		- favoritesListModal.innerHTML = `< div class = "muted" style = "padding: 12px"> NO favorites yet < /div>`';
		- return; }
			- 위에서 정렬한 문서들의 목록이 0이라면
			- 즉, 별표 친 문서가 없다면
			- 즐겨찾기 목록 상자에 div 요소를 만들어서 즐겨찾기가 없다는 글자를 보여주고 함수 종료
	- 
	- favs.forEach((doc) => {
		- const row = el("div", { className: "fav-row"});
			- 즐겨찾기 한 문서들을 하나씩 순회하면서
			- 제목, 아이콘, 별 버튼 등을 모두 품게되는 부모 상자 하나 생성
		- const ico = el("div", {
			- className: "doc-icon" + (doc-icon ? "has-icon" : "no-icon" 
			- textContent: doc.icon || "없음", )});
				- 아이콘 요소를 생성하는데 기본적으로 doc-icon 클래스를 붙이고 
				- doc-icon에 뭐라도 들어있으면 -> true로 has-icon을 붙이고 아니면 no-icon
		- const titile = el("div", { textContent: doc.titile, style: "flex:1"});
			- 문서의 진짜 이름이 적힌 div 상자를 만들고
			- 모든 공간을 다 차지하라는 flex:1 설정
		- const acts = el("div", { className: "fav-actions" });
			- 버튼들을 담아둘 상자 만들기
		- const unstar = el("div", { className: "icon-btn", title: "unstar", textContent: "빈 별", });
			- 즐겨찾기 해제 기능을 할 별 모양 버튼
			- 마우스를 이 별 위에 올리면 unstar라는 작은 도움말 풍선


	- unstar.addEventListener("click", (e) => {
		- 별 모양 버튼을 눌렀을 때 이벤트
		- e.stopPropagation( );
		- updateDoc(doc.id, { starred: false } );
			- 이 문서의 데이터를 찾아서 별표 상태를 거짓으로 바꾸기
			- 즐겨찾기 취소 기능
		- if (state.activeId === doc.id) {
			- 이 문서가 지금 보고 있는 문서라면
			- const d = findDoc(doc.id);
				- 바로 위에서 updateDoc으로 데이터를 수정한 그 문서의 최신 상태를 데이터베이스에서 다시 찾아와 d라는 변수에 저장
			- if (starBtn) starBtn.textContent = d.starred ? "별" : "빈 별";}
				- 만약 화면에 본문의 별 버튼이 존재하면 
				- 그 버튼의 데이터가 별표상태가 true면 별
				- 아니면 빈 별
			- 즐겨찾기 창에서 한 행동이 본문 화면에도 일치하도록 동기화
		- renderTrees( );
			- 사이드 바 목록도 다시 그리기
		- buildFavoritesModal( ); });
			- 즐겨찾기 창을 처음부터 다시 그려서 별표를 해제한 문서는 목록에서 사라지게
	- favs.forEach((doc) => {
		- row.append(ico, title, acts);
			- 아까 만든 긴 상자에 아이콘, 제목, 버튼 주머니를 순서대로 넣기
		- acts.append(unstar);
			- 버튼 주머니에 별 버튼 넣어주기
		- row.addEventListener("click", ( ) => {
			- 그 줄을 클릭했을 때
			- closeFavoritesModal( );
				- 즐겨찾기 창 닫기 
			- navigateTo(doc.id); } );
				- 클릭한 문서가 있는 페이지로 화면 이동
			- 
	- openFavoritesModalBtn?.addEventListener("click", openFavoritesModal);
		- 즐겨찾기 버튼을 누르면 창을 열고
	- favoritesCloseBtn?.addEventListener("click", closeFavoritesModal);
		- 닫기 버튼을 누르면 창을 닫기
	- favoritesOverlay?.addEventListener("click", (e) => {
		- if (e.target === favoritesOverlay) closeFavoritesModal( ); } );
			- 창 바깥의 어두운배경(오버레이)를 클릭하면
			- 클릭한 지점이 정확히 어두운 배경 부분일 때만 
			- 즐겨찾기 모달 닫기
	- document.addEventListener("keydown", (e) => {
		- ESC키로 닫기
		- if (favoritesOverlay && favoritesOverlay.style.display === "grid" && e.key === "Escape" ) {
			- 즐겨찾기 창이 존재하고
			- 오버레이 창이 열려있는 상태이며
			- 누른 키가 ESC 키일 때
			- e.preventDefault( );
			- closeFavoritesModal( ); } } ); 
				- 모달 닫기 
### 열고 닫는 버튼 연결
- openFavoritesModalBtn?.addEventListener("click", openFavoritesModal);
	- 즐겨찾기를 여는 버튼이 존재하면 클릭 이벤트를 연결하고 없으면 종료
- favoritesCloseBtn?.addEventListener("click", closeFavoritesModal);
	- 즐겨찾기를 닫는 버튼이 존재하면 클릭 이벤트를 연결하고 없으면 종료
- favoritesOverlay?.addEventListener("click", (e) => {
	- if (e.target === favoritesOverlay) closeFavoritesModal( ); });
		- 오버레이 창에도 이벤트 연결
		- 사용자가 클릭한 그 지점이 정확히 오버레이 창인 경우
		- 즐겨찾기 모달 닫기


- document.addEventListener("keydown", (e) => {
	- if (favoritesOverlay && favoritesOverlay.style.display === "grid" && e.key === "Escape") {
		- e.preventDefault( );
		- closeFavoritesModal( ); } });
## 검색 오버레이 구현 - 실시간 필터링과 엔터 이동
- const searchOverlay = $("searchOverlay");
- const searchInput = $("#searchInput");
- const searchResults = $("#searchResults");
	- 검색 결과 컨테이너/ 클릭 가능한 행이 동적으로 추가/ 재랜더링
- let searchActiveIndex = -1;
	- 키보드 내비게이션 상태를 기억하는 선택 인덱스(0 기반)
	- 초기값 -1. 값 변경 시 하이라이트 재 랜더
- function openSearch( ){
	- if (searchOverlay & searchInput) {
		- searchOverlay.style.display = "grid";
		- searchInput.value = "";
		- renderSearchResults("");
			- 모든 결과가 보이는 기본 결과 렌더
		- searchInput.focus( ); } }
			- 즉시 포커스
			- 열자마자 타이핑 누락 방지

- function closeSearch( ){
	- if (searchOverlay) searchOverlay.style.display = "none";}

- function renderSearchResults(q) {
	- if (!searchResults) return;
	- const items = state.docs.filter( (d) => d.title.toLowerCase( ).includes(q.toLowerCase( )));
	- searchResults.innerHTML = "";
	- items.forEach((d, i) => {
		- const row = el("div", { className: "trash-row" } );
			- 클래스 이름이 trash-row인 이유는 휴지통과 동일 스타일 재사용 
			- 
		- row.innerHTML = `< span>${d.icon || "" } ${d.title} < /span>`;
			- 이모지 아이콘과 제목을 innerHTML로 삽입
		- row.addEventListener("click", ( ) => {
			- closeSearch( );
			- navigateTo(d.id); } );
		- if (i === searchActiveIndex) row.style.background = "var(--panel-3)";
		- searchResults.appendChild(row); }); }

- searchInput?.addEventListener("input", ( ) => {
	- 추가, 삭제, 붙여넣기 등 모든 값 변화가 있을 때
	- searchActiveIndex = -1;
		- 이전 하이라이트 초기화
		- 잘못된 강조 방지
	- renderSearchResults(searchInput.value); });
		- 즉시 재랜더
		- 입력한 값을 포함한 문서 목록 랜더링

- searchInput?.addEventListener("keydown", (e) => {
	- 검색창에서 키보드가 눌리면 이벤트 시작
	- const items = searchResults?.children || [];
		- 검색 결과창 안에 들어있는 자식요소(검색된 항목들)을 모아서 items라고 불러라
		- 만약 검색 결과가 없다면 빈 배열을 items라고 불러라
	- if (e.key === "Escape") {
		-  방금 누른 키가 ESC인가
		- e.preventDefault( );
		- closeSearch( ); }
			- 검색창 즉시 닫기
	- if (e.key === "ArrowDown") {
		- 아래 화살표가 눌렸다면
		- e.preventDefault( );
		- searchActiveIndex = Math.min(item.length -1, searchActiveIndex + 1 );
			- 검색 결과 안에 들어있는 자식 요소들(검색된 항목들)의 길이 -1 => 마지막 번호
			- 현재 선택된 위치(인덱스)에서 한 칸 아래
			- 둘 중 작은 값 선택해서  searchActiveIndex로
		- renderSearchResults(searchInput.value);}
			- 위치가 바뀌었으니 바뀐 위치에 하이라이트를 줘서 다시 랜더링
	- if (e.key === "ArrowUp") {
		- e.preventDefault( );
		- searchActiveIndex = Math.max(0, searchActiveIndex - 1 );
			- 0번 인덱스
			- 지금 인덱스보다 -1
			- 둘 중 큰 값 선택해서  searchActiveIndex 
		- renderSearchResults(searchInput.value); } 
	- if (e.key === "Enter") {
		- e.preventDefault( );
		- if (items.length && searchActiveIndex >= 0) {
			-  items.length가 존재하는가 -> 검색 결과 목록에 뭐라도 들어있는가
			- searchActiveIndex >= 0
				- 처음 searchActiveIndex는 -1
				- 그 값이 0보다 크거나 같다는 것은 화살표 키를 눌러 항목 중 하나를 제대로 가리키고 있다는 상태
			- 두 값을 만족했을 때
			- items[searchActiveIndex].click( ); }}});
				- 목록 중에서 searchActiveIndex(지금 화살표로 선택된 번호)의 항목을 선택해 
				- .click으로 마우스로 클릭한 것과 같은 효과를 내라

- document.addEventListener("keydown", (e) => {
	- 키보드가 눌린 사건이 발생한다면 
	- if (searchOverlay && searchOverlay.style.display === "grid" && e.key === "Escape" ) {
		- 검색창 오버레이가 존재하고
		- 그 검색창이 실제로 눈에 보이게 열려있는 상태이며
		- 눌린 키가 ESC라면
		- e.preventDefault( );
		- closeSearch( ); } });
			- 검색창을 닫아라

- searchOverlay?.addEventListener("click", (e) => {
	- if (e.target === searchOverlay) closeSearch( ); });

- document.querySelectorAll("#actionSearch").forEach(el) => {
	- el.addEventListener("click", openSearch); });
		- querySelectorAll로 두 곳의 동일 ID 버튼을 모두 선택
		- forEach로 순회하며 이벤트 바인딩
		- 어느 위치의 검색 버튼을 눌러도 같은 openSearch 흐름 실행
		- 모달 상태 항상 동일하게 초기화
		- 원칙 적으로 중복 ID는 지양하는게 맞으나 템플릿 제약 등으로 불가피할 땐 이렇게 명시적으로 처리해 예측 가능한 동작 보장
## 설정 모달 & 테마 동기화: 열기/ 닫기/ 라이트/ 다크 즉시 적용, 영구 저장
- const settingOverlay = $("#settingOverlay");
	- 화면 전체 오버레이 .style.display로 열림, 닫힘 제어
	- grid로 중앙 정렬된 모달/none으로 완전 숨김
- const themeToggle = $("themeToggle")// "use light theme"체크 박스
	- 설정 모달 내부 체크박스(라이트 모드 사용 여부)
	- 가드 패턴 if로 존재 확인 후 처리
	- 템플릿 변형, 비동기 초기화로 요소가 없을 때 에러 방지

### 모달을 실제로 여는 함수
- function openSettings( ){
	- currentTheme = loadTheme( );
		- loadTheme호출로 currentTheme갱신 (localStorage)에서 라이트 다크 읽기
	- if (themeToggle) themeToggle.checked = currentTheme === "light";
		- 체크박스인 themeToggle이 존재하면 checked 속성을 현재 theme와 동기화
	- if (settingsOverlay) settingOverlay.style.display = "grid";}

- document.querySelectorAll("#actionSettings").forEach((el) => {
	- el.addEventListener("click", openSettings);});
	- 모달을 여는 트리거는 사이드바와 상단 navbar에 각 하나씩 두 개 존재
### 모달을 닫는 함수들
- $("#settingsClose")?.addEventListener("click", ( ) => {
	- if (settingsOverlay) settingsOverlay.style.display = "none";} )
	- 닫기 버튼 존재 확인 후 처리
	- 클릭 시 모달 즉시 숨김
	- 별도 상태 변수 없이 표시 속성만 토글
- settingsOverlay?,addEventListener("click", (e) => {
	- if (e.target === settingsOverlay) settingsOverlay.style.display = "none"; });
	- 외부 클릭 시 닫기 
	- 내부 클릭 보호: 모달 콘텐츠 클릭은 버블링 돼도 닫히지 않음
	- 타깃과 리스너 요소 일치 비교로 의도치 않은 닫힘 방지
- document.addEventListener("keydown", (e) => {
	- if (settingsOverlay && settingsOverlay.style.display === "grid" && e.key === "Escape") {
		- e.preventDefault( );
		- settingsOverlay.style.display = "none";} });

### 라이트 다크 즉시 전환
- themeToggle?.addEventListener("change", ( ) => {
	- const next = themeToggle.checked ? "light" : "dark";
		- 체크돼었을 때 light
		- 해제돼었을 때 dark
	- currentTheme = next;
		- 메모리 동기화
	- applyTheme(next);
		- 즉시 적용
			- < html data-theme = 갱신 -> css 변수로 전역 색상 즉시 전환
	- saveTheme(next);});
		- localStorage에 저장

## Export/Import - Blob + URL로 JSON 저장, FileReader로 불러오기 반영
### export 버튼을 클릭했을 때(내보내기 기능)
- $("#exportBtn")?.addEventListener("click", ( ) => { 
	- const data = localStorage.getItem(STORAGE_KEY) || "{ }";
	- const blob = new Blob([data], { type: "aplication/json" });
	- const url = URL.createObjectURL(blob);
	- const a = document.createElement("a");
	- a.href = url;
	- a.download = "notion-export.json";
	- a.click( );
	- URL.revokeObjectURL(url);});

	- ID가 exportBtn인 버튼을 찾고 있다면 클릭 이벤트 연결
	- 브라우저 창고(localStorage)에 저장된 우리 앱의 전체 데이터 가져옴
		- 가져올 때는 문자열 형태, 만약 브라우저 창고가 비어있다면 빈 객체 문자열을 대신 사용
	- blob은 가상의 파일 덩어리를 만드는 것
		- new Blob([ ], { type: } )은 브라우저에 내장된 생성자 함수
		- 메모리 속에 있는 일반적인 텍스트를 컴퓨터 파일 시스템이 이해할 수 있는 이진 데이터 덩어리로 변환
		- 괄호 안 첫 번째 재료
			- 반드시 대괄호 [ ]로 감싸 배열 형태로 넣어줘야 함
			- 이 글자들을 모두 모아서 파일 알맹이로 써줘 라는 의미
		- 두 번째 재료
			- { type: }는 이 파일의 파일임을 알려주는 것
			- 컴퓨터가 이 부분을 보고 메모장으로 열지, 브라우저로 열지 판단
			- "application/json", "text/html", "image/png" 등이 들어갈 수 있음
	- URL.createObjectURL(blob);
		- 컴퓨터 메모리 속에만 존재하는 실체 없는 데이터 덩어리(Blob)에게 임시 주소를 만들어주는 과정
		- 브라우저가 기본으로 가지고 있는 URL이라는 내장 객체에 소속된 정적 메서드
		- 메모리에 떠다니는 Blob객체를 가리키는 일회용 URL 생성
		- 우리가 위에 만든 Blob은 브라우저 메모리에만 잠깐 머물고 있는 데이터라서 주소가 없음 -> 이때 위 메서드를 사용하면 가짜 주소를 발행할 수 있음
	-  const a = document.createElement("a");
	- a.href = url;
	- a.download = "notion-export.json";
		- 발행한 임시 URL을 가지고 실제로 사용자의 컴퓨터에 파일을 저장시키는 역할
		- 일단 메모리상에 a 태그(링크 버튼)을 생성함
		- 아까 만든 URL을 a 링크의 목적지로 설정 -> 링크를 누르면 메모리에 있는 데이터 덩어리로 연결
		- a.download = "notion-export.json"
			- a태그가 가신 내장 속성
			- 원래 링크는 누르면 그 주소로 이동하지만 이 속성이 있으면 브라우저는 이동하지 않고 연결된 데이터를 ""이름으로 다운로드하도록 동작 방식을 바꿈
	- a.click( );
		- 모든 HTML 요소가 기본으로 가지고 있는 내장 메서드
		- 컴퓨터가 사람 대신 이 링크를 눌러줌
	- URL.revokeObjectURL(url);});
		- 메모리 관리
		- 브라우저의 URL 내장 객체에 들어있는 내장 메서드
		- createObjectURL로 만들었던 임시 주소 파괴

### Import 버튼에서 파일을 클릭했을 때
- $("importFile")?.addEventListener("change", (e) => {
	- const file = e.target.files[0];
	- if (!file) return;
	- const reader = new FileReader( );
	- reader.onload = ( ) => {
		- try {
			- localStorage.setItem(STORAGE_KEY, reader.result);
			- load( );
			- renderTrees( );
			- renderPage( );
			- toast("Import complete", "success");}
		- catch (err) {
			- toast("Import failed", "error");} };
		- reader.readAsText(file);})
	
	- 사용자가 컴퓨터에 있는 파일을 선택하면 그 내용울 읽어서 앱의 데이터를 통째로 교체하는 로직
	- $("importFile")?.addEventListener("change", (e) => {
		- 사용자가 파일 선택 창에서 파일을 고르고 열기를 누르는 순간 발생
	- e.target.files[0];
		- input type = "file" 요소가 가진 내장 속성
		- .files는 브라우저가 input파일 선택기를 통해 들어온 파일들을 담아두는 전용 보관함
		- 사용자가 파일을 하나만 선택하더라도 브라우저는 이 데이터를 목록 형태로 관리
		- .files[0] 안에는 파일의 알맹이 뿐만 아니라 파일에 대한 정보들이 들어있음
			- 이름, 크기, 종류, 마지막으로 수정한 날짜
		- 사용자가 선택한 파일들의 목록 중 첫 번째 파일을 집어옴
	-  const reader = new FileReader( );
		- new FileReader( )는 브라우저에 내장된 생성자 함수
		- 사용자의 컴퓨터에 있는 파일을 자바스크립트가 읽을 수 있도록 도와주는 객체를 만듦
		- 웹 브라우저는 보안상 사용자의 컴퓨터 파일을 직접 열어볼 수 없기 때문에 FileReader라는 특수 도구 사용
	- reader.onload = ( ) => {
		- .onload로 파일 읽기가 끝나는 순간에 실행
		- 파일 읽기가 무사히 끝나면 try 실행
	- try {
		- localStorage.setItem(STORAGE_KEY, reader.result);
			- 브라우저 저장소를 열고 파일에서 방금 읽어온 데이터로 내용물을 바꾸기 
		- load( );
		- renderTrees( );
		- renderPage( );
		- toast("Import complete", "success");}
	- reader.readAsText(file);})
		- FileReader 객체가 가진 내장 메서드
		- 사용자가 선택한 파일을 글자 형식으로 읽기

## confirm 모달 - 메세지 콜백, ESC. 배경 클릭까지
- 최종 확인을 받기 위한 컨펌 모달
- const modalOverlay = $("#modalOverlay");
	- 화면 전체를 덮어 모달 뒤 요소와의 상호작용 차단
- let modalResolver = null;
	- 확인 버튼 클릭 시 실행할 콜백을 임시 보관하는 저장소

- function confirmModal(message, onConfirm) {
	- const t = $("#modalTitle"), 
		- m = $("#modalMessage");
	- if (t) t.textContent = "Confirm";
	- if (m) m.textContent = message;
	- if (modalOverlay) modalOverlay.style.display = "flex";
	- modalResolver = onConfirm; }

	- function confirmModal(message, onConfirm) {
		- message인수는 모달 본문에 표시할 텍스트
		- onConfirm은 사용자가 확인을 눌렀을 때 실행할 함수
	-  if (modalOverlay) modalOverlay.style.display = "flex"
		- 오버레이 노출
	- modalResolver = onConfirm; }
		- 확인 버튼이 눌렸을 때 실행될 로직 보관
		- 예시
			- confirmModal("이 문서를 정말 삭제하시겠습니끼?', removeDoc)
			- 확인 시 removeDoc 실행

- $("modalCancle")?.addEventListener("click", ( ) => {
	- if (modalOverlay) modalOverlay.style.display = "none";
	- modalResolver = null; });

	- 취소버튼 클릭 -> 모달 닫기, 오버레이 숨김
	- modalResolver = null; });
		- modalResolver 초기화
		- 남은 콜백이 없으므로 아무 동작도 실행되지 않음

- $("#modalConfirm")?.addEventListener("click", ( ) => {
	- if (modalOverlay) modalOverlay.style.display = "none";
	- if (modalResolver) modalResolver( );
	- modalResolver = null; });

	- 확인 버튼 클릭 -> 모달 닫기, 오버레이 숨김
	-  if (modalResolver) modalResolver( );
		- modalResolver 실행
		- 여기에는 컨펌모달 초기에 전달했던 콜백 함수가 들어있으므로 원하는 로직이 그대로 실행
	- modalResolver = null; });
		- 실행이 끝나면 null로 초기화해 중복 실행 방지
		- 

## 키보드 단축키 - 검색, 새 문서, 이름 변경
- document.addEventListener("keydown", (e) => {
	- const meta = e.ctrlKey || e.metaKey;
	- 
	- if (meta && e.key.toLowerCase( ) === "k") {
		- e.preventDefault( );
		- openSearch( );}
		- 
	- if (meta && e.altKey && e.key.toLowerCase( ) === "n") {
		- e.preventDefault( );
		- const pid = state.activeId || null;
		- const id = createDoc( { title: "untitled", parentId: pid } );
		- if (pid) state.expanded[pid] = true;
		- navigateTo(id); }
	- if (e.key === "F2" && state.activeId) {
		- e.preventDefault( );
		- const row = document.querySelector( 
			- `.tree-row[data-id = "${state.activeId}"`] );
	- if (row) {
		- const label = row.querySelector(".label");
		- if (label) inlineRename(state.activeId, label); } } });

	- 전역 키 리스너 등록 -> 앱 전역에서 키 입력 감지
	- keydown으로 키 입력 시 이벤트 실행
	- 인자로 넘어오는 이벤트 객체 e는 keyboardEvent
		- 이 객체 안에는 어떤 키가 눌렸는지, 보조키가 눌렸는지
	-  e.ctrlKey || e.metaKey;
		- 브라우저 내장 속성
		- 윈도우의 컨트롤 키나, 맥의 커맨드 키가 눌렸는지 확인
	- if (meta && e.key.toLowerCase( ) === "k") {
		- 컨트롤 k가 눌렸는지 확인
		- openSearch()로 검색창 열기
	- if (meta && e.altKey && e.key.toLowerCase( ) === "n") {
		- 컨트롤 알트 n 을 눌렀을 때
		- const pid = state.activeId || null;
			- 현재 활성화된 문서의 아이디를 부모 아이디로, 없으면 루트 생성
		- const id = createDoc( { title: "untitled", parentId: pid } );
			- 제목은 untitled로, 부모 id는 위에서 설정한 pid로해서 문서 생성
		- if (pid) state.expanded[pid] = true;
			- 부모 문서가 존재할 경우 자동으로 펼쳐지도록 상태 조정
		- navigateTo(id); }
			- 곧바로 새 문서 페이지로 이동
	-  if (e.key === "F2" && state.activeId) {
		- f2키 눌렸을 때
		- const row = document.querySelector(`.tree-row[data-id="${state.activeId}"]`);
			- 사이드바는 문서가 한 줄(tree-row)
			- 클래스 이름이 .tree-row인 녀석들 중에서 찾아라 
			- 그 중에서도 data-id라는 이름표의 값이 지금 선택한 id와 같은 녀석을 골라라 

## 사이드바 폭 제어 - 접기, 펼치기, 드래그 리사이즈, 반응형 자동 보정
- collapseBtn?.addEventListener("click", ( ) => {
	- collapse( );
	- syncMenuBtnVisibilty( );
	- });

	- 사이드 바 내부의 접기 버튼
	- 버튼을 클릭하면 collapse실행
	- 애니메이션 폭 0으로 축소
	- writeLastWidth( )로 접기 전 폭 저장 -> 펼칠 때 복원
	- syncMenuBtnVisibilty( ); 
		- 햄버거 메뉴 버튼 표시 여부 갱신
		- 사이드 바 접힘/모바일 -> 버튼 표시
		- 일반 레이아웃 -> 버튼 숨김


- menuBtn?.addEventListener("click", ( ) => {
	- resetWidth( );
	- syncMenuBtnVisibility( );
	- });

	- 네비게이션 바에 있는 햄버거 버튼
	- resetWidth( ) 실행 -> 사이드 바 펼치기
	- lastSidebarWidth 있으면 그 값 복원
	- 없으면 defaultSidebarWidth 적용
	- 


- sidebarPeekBtn?.addEventListener("click", ( ) => {
	- resetWidth( );
	- syncMenuBtnVisibility( );});

	- 피크 버튼

### 마우스로 사이드 바 폭을 조절하는 동작
- let isResizing = false;
	- 드래그 중인지 여부 판단
- resizingHandle?.addEventListener("mousedown", (e) => {
	- if (e.detail === 2) {
		- e.preventDefault( );
		- if (sidebar.classList.contains("is-collapsed") {
			- resetWidth( );
		- else {
			- const px = defaultSidebarWidth( );
			- animateSidebarWidth(px);
			- writeLastWidth(px); }
		- isResizing = false;
		- syncMenuBtnVisibility( );
		- return;}
		- is Resizing = true;
		- e.preventDefault( ); });

	- resizingHandle: 사이드 바 끝에 붙어있는 경계선 요소
	- mousedown: 마우스 버튼을 꾹 누르는 순간 발생하는 이벤트
	- if (e.detail === 2) {
		- 마우스가 연속으로 몇 번 클릭됐는지 알려줌 
		- 2는 더블클릭
		- if (sidebar.classList.contains("is-collapsed") { resetWidth( );
			- 사이드 바 클래스가 is-collpase를 담고 있다면 -> 사이드바가 접혀있다면
			- resetWidth( );으로 원래대로 되돌려라
		- else {
			- 사이드 바가 열려있다면
			- const px = defaultSidebarWidth( );
				- 앱이 정한 기본 너비를 가져옴
			- animateSidebarWidth(px);
				- 부드러운 애니메이션과 함께 사이드바 너비를 기본값으로 조절
			- writeLastWidth(px); }
				- 사용자가 설정한 이 너비를 기억해둠 -> 새로고침해도 유지되도록
		- is Resizing = true;
			- 더블클릭이 아니라 마우스로 꾹 누른거라면
			- e.preventDefault( );
				- 드래그할 때 글자들도 선택되는 현상 막기
				- 

- document.addEventListener("mousemove", (e) => {
	- if (!isResizing) return;
	- let w = e.clientX;
		- 브라우저 화면 왼쪽 끝에서 마우스 포인터가지의 가로 거리 
		- 이게 곧 사이드바의 너비가 됨
	- if (w < 220) w = 220;
		- 사이드바의 최소 너비 220px 유지
	- if (w > 420) w = 420;
		- 최대 너비 유지
	- sidebar.classList.remove("is-collapse");
		- 사용자가 조절을 시작했으니 사이드 바가 열려있는 상태 유지하도록
	- setSidebarWidth(w);
		- 계산된 너비를 사이드 바의 css너비값으로 적용 
		- 화면이 실시간으로 변하는 효과
	- writeLastWidth(w);});
		- 새로고침해도 지금의 크기를 유지하도록 저장소에 저장
- document.addEventListener("mouseup", ( ) => {
	- isResizing = false; });
	- 마우스를 놓으면 드래그 종료

- matchMedia("(max-width: 768px)").addEventListener("change", (ev) => {
	- state.isMobile = ev.matches;
	- if (state.isMobile) {
		- collapse( );}
	- else {
		- resetWidth( ); }
	- syncMenuBtnVisibility( ); });
	- 
	-  matchMedia("(max-width: 768px)")
		- 브라우저 뷰포트 폭이 768px 이하일 때를 감지
		-  ev.matches;
			- matches 속성이 true면 state.isMobile로 모바일 환경으로 간주
			-  collapse( );} 로 사이드 바 접기
	-  else {
		- 모바일 폭이 아닐 때 -> 데스크탑 폭일 때
		- resetWidth( ); }로 이전 상태로 복원


- if (state.isMobile) {
	- collapse( ); }
- else { resetWidth( ); }
- syncMenuBtnVisibility( );

	- 앱 시작 시 초기 분기 실행
	- 모바일 환경인지 확인하고 그 값에 따라 sidebar를 접거나 복원

- window.addEventListener("orientationchange", ( ) => {
	- if (state.isMobile) {
		- setSidebarWidth(0); } } );
		
	- 화면 회전이 발생했을 때
	- 모바일 환경인지 확인 -> 사이드바 숨기기
		- 사이드 바 너비를 0으로 만들어서 열려있던 사이드바 닫기
		- 레이아웃이 갑자기 바뀌지 않도록 사이드 바 폭 고정하는 것
		- 

-  window.addEventListener("resize", ( ) => {
	- const vw = window.innerWidth;
	- if (vw < 768 && !sidebar.classList.contains("is-collapse")) {
		- collapse( );}
	- syncMenuBtnVisibility( );});

	- 창 크기가 바뀔 때 실행
	- const vw = window.innerWidth;
		- 현재 뷰포트 폭 확인
	- 뷰포트가 768px 미만이고 사이드 바 펼침 상태면 -> 자동 접기
	- 모바일 크기에서는 항상 접힌 상태 유지

## 앱 초기화 - 상태 복원, 사이드바/ 휴지통 렌더, 라우팅/ 메뉴 초기화
- function init( ){
	- load( );
	- if (state.isMobile) {
		- collapse( );}
	- else {
		- resetWidth( ); }
	- renderTrees( );
	- renderTrash( );
	- if (!location.hash) {
		- navigateTo("welcome");}
	- else {
		- syncFromLocation( ); }
	- const id = $("lastEdited");
	- if (id) id.textContent = new Date( ).toLocaleDateString( );
	- syncMenuBtnVisibility( ); }
	- init( );

	- 앱이 처음 켜질 때 딱 한 번 실행되는 초기 설정 마스터 함수
	- load( );
		- 앱의 브라우저 저장소를 열어 저장된 데이터를 메모리로 가져옴
	- if (state.isMobile) {collapse( );}
		- 모바일 환경인지 확인하고 그렇다면 사이드 바를 접은 상태로 시작함
	- else { resetWidth( ); }
		- 모바일 환경이 아니면 원래 설정한 너비로 열기
	- 사이드바와 휴지통 목록 렌더링
	- if (!location.hash) {
		- location.hash 는 브라우저 주소창의 URL 중에서 # 뒤에 붙는 글자들을 말함
		- 웹 앱에서 이 # 은 현재 내가 어떤 페이지나 문서에 머물고 있는지 알려주는 역할
		- 만약 그 글자가 없다면 
		- navigateTo("welcome");}
			- 앱이 자동으로 welcome 패이지로 이동시킴
	-  else {
		- 글자가 있다면 
		- syncFromLocation( ); }
			- 이 사람이 예전에 보던 문서가 있으면 그 해당 문서를 바로 열어줌
	- const id = $("lastEdited");
		- HTML에서 id가 lastEdited인 요소를 찾아옴
	- if (id) id.textContent = new Date( ).toLocaleDateString( );
		- 만약 그 요소가 존재한다면 
		- 현재 시스템의 날짜와 시간 정보를 생성하여 
		- 날짜를 그 나라의 형식에 맞게 바꿔줌
		- 그 값을 위에서 찾은 요소의 텍스트 내용으로 바꿈
	- syncMenuBtnVisibility( ); }
		- 사이드바가 열려있는지 닫혀있는지에 따라 메뉴버튼을 보여줄지 말지 최종 확인
	- init( );

	






















