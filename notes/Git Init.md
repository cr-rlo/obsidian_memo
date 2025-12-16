- git init turns any directory into a git repository.

## what does git init do?
- `git init`은 Git으로 새 프로젝트를 시작하는 한 가지 방법
- 저장소를 시작하려면 `git init` 또는 `git clone` 중 하나만 사용, 둘 다 사용해서는 안됨
- 저장소를 초기화하기 위해 Git은 `.git`이라는 숨겨진 디렉토리를 생성
- 이 디렉토리에는 Git이 프로젝트 기록의 일부로 사용하고 생성하는 모든 객체와 참조가 저장
- 이 숨겨진 `.git` 디렉토리가 일반 디렉토리와 Git 저장소를 구분하는 역할

## how to use git init
- git init의 일반적인 사용법 및 옵션
- git init: 현재 디렉터리를 Git 저장소로 변환
- git init <디렉터리>: 현재 경로의 디렉터리를 Git 저장소로 변환
- git init --bare: 새로운 베어 저장소(개발 내용이 포함되지 않은 원격 저장소)를 생성

## examples of git init
- git init vs git clone
- git init: 한 사람이 로컬에 새 저장소를 만드는 경우
	- 프로젝트가 '이미' 로컬에 존재하지만 아직 Git이 설치되어 있지 않은 경우, git init이 적합함
	- 이 명령은 다른 공동 작업자가 프로젝트를 공유하더라도 한 번만 실행하면 됨
	- 먼저 저장소를 초기화함
	- 저장소를 초기화했으면 GitHub.com과 같은 곳에 원격 저장소를 생성
	- 그 다음 git remote add origin < URL > 명령을 사용하여 원격 URL을 로컬 Git 저장소에 추가
	- 이렇게 하면 원격 URL이 'origin'이라는 더 알아보기 쉬운 이름으로 저장됨
	- git add 명령을 사용하여 기존 파일을 스테이징하고 git commit 명령을 사용하여 스냅샷을 생성하여 히스토리를 최소 하나 이상의 커밋으로 구성
	- 최소 하나 이상의 커밋이 완료되면 git push -u origin main 명령을 사용하여 원격 저장소로 푸시하고 추적 관계를 영구적으로 설정
- git clone: 원격 저장소가 이미 존재하는 경우, git init 대신 git clone을 선택
	- 프로젝트를 '나중에' 원격 저장소로 옮길 목적으로 먼저 원격 저장소를 생성하는 경우, 몇 가지 추가 단계
	- 원격 저장소에 커밋이 없는 경우, 위에서 설명한 git init 단계
	- 원격 저장소에 커밋과 파일이 있지만 프로젝트 파일도 함께 포함시키려면 해당 저장소를 git clone
	- 그 다음 프로젝트 파일을 복제된 저장소로 이동
	- git add, git commit, git push를 사용하여 프로젝트 초기 단계에 맞는 히스토리를 생성
	- 이렇게 하면 팀에서 git init을 다시 실행하지 않고도 저장소와 상호 작용

## git init existing folder
- 기존 폴더에 git init 실행
- git init의 기본 동작은 현재 디렉터리를 Git 저장소로 변환하는 것입
- 기존 프로젝트를 Git 저장소로 만들려면 대상 '루트 디렉터리'로 이동한 다음 git init을 실행
- 또는 현재 경로의 디렉터리에 새 저장소를 만들 수도 있음 
- git init <디렉터리> 명령어를 사용하고 Git 저장소로 만들 디렉터리를 지정

## git init gone wrong
- git init 오류
- 잘못된 디렉터리에서 git init 실행
	- 잘못된 위치에서 `git init`을 실행하면 의도치 않은 저장소가 생성
	- Git을 사용할 때 이상한 오류 메시지가 표시될 수 있음
	- 상위 디렉터리가 Git 저장소로 사용되고 있다고 의심될 수도 있음
	- 이 문제를 해결하려면 먼저 의도치 않은 저장소가 생성된 디렉터리 찾기
	- `git status` 명령어를 사용하여 현재 디렉터리가 Git에서 추적되고 있는지 확인
	- 추적되고 있다면 `ls -al` 명령어를 실행하여 숨겨진 `.git` 디렉터리를 찾기

	- 찾을 수 없다면 `cd ...` 명령어를 사용하여 상위 디렉터리로 이동
	- 그런 다음 `git status`와 `ls -al` 명령어를 다시 실행
	- `.git` 디렉터리를 찾을 때까지 이 과정을 반복

- .git 디렉토리를 찾았고, 해당 디렉토리가 Git 저장소가 되기 원하지 않는다면 `rm -rf .git` 명령어
- 이 명령어는 .git 디렉토리를 삭제하여 해당 저장소의 초기화를 해제
- git status 명령어를 다시 실행하여 Git이 더 이상 해당 파일들을 추적하지 않는지 확인

## related terms
- git clone [url]: GitHub에 이미 존재하는 저장소를 모든 파일, 브랜치, 커밋을 포함하여 복제(다운로드)
- git status: 현재 브랜치, 작업 또는 스테이징 디렉토리의 파일, 기타 중요한 정보 표시
- git remote -v: 연결된 원격 저장소와 해당 저장소의 저장된 이름(예: origin)을 표시
- git remote add origin < url >: 새로 생성된 저장소에서 다른 사람들과 협업할 수 있도록 원격 저장소를 추가
- git push: 로컬 브랜치의 모든 커밋을 원격 저장소에 업로드 (스테이징)
- git push -u origin main: 브랜치를 처음 푸시할 때 이 명령어를 사용하면 원격 저장소와 로컬 저장소 간의 관계가 설정되어 이후에는 추가 옵션 없이 git pull과 git push를 사용 가능

## Git Flow 협업 방식
- 지금까지 코드 짰던걸 main 브랜치에 보관했다고 치자
- 신기능을 만들고 싶은데! main에 바로 신기능을 만들게되면 고치기 어려움
- dev 브랜치를 하나 생성하여 원본 코드 건들지 않고 신기능 개발과정 가능
- dev에 feature 브랜치 만들어서 신기능 개발해보고! 잘 되면 그걸 dev로 merge
- dev가 완성되어서 출시해도 된다 싶으면 ! dev에서 임시 브랜치 release를 만들어서 여러가지 테스트
- 이제 release도 만족스럽게 완성됐다 싶으면 main에 합치기
- dev에서는 또 추후 개발이 이뤄져야하기 때문에 release는 develop에도 merge되어야 함
- 완성된 main에서 버그가 생기면 main에서 바로 hotfix 브랜치 만들어서 수정
- 수정완료된 hotfix를 main과 dev에 merge

## Trunk-based 협업 방식
- 곁가지들을 치는 것이 아니라 main하나만 운영
- 새로운 기능, 버그 픽스가 필요할 때마다 메인 브랜치에서 브랜치 하나만 만들어서 코드 짜고 다시 main으로 바로 merge
- 소스코드를 여러 개 사용할 필요가 없다는 장점