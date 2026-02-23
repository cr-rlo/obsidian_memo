- 인터넷과 데이터 베이스를 이해하기 위한 핵심축
- client와 server 
- 여러 사람에 의해 공유되어 사용될 목적으로 통합하여 관리되는 데이터의 집합
- 기본 유저 -uroot(관리자)
- sql 중요하고도 쉬운 컴퓨터 언어
- column과 row
- mysql cheat sheet
- mysql data types
- 
![[스크린샷 2025-10-21 오전 9.56.28.png]]
- cd /usr/local/mysql/bin/

 bin % ./mysql -uroot -p

## 스키마(data base)
- 서로 연관된 표들을 그룹핑한 것
- 그들을 또 그룹핑한게 데이터베이스 서버
- 데이터 배이스 생성 = CREATE DATABASE 이름;
- 데이터 베이스 삭제 = DROP DATABASE 이름;
- 데이터 베이스 사용 = USE 이름;
- 

## 보안
- 자체적인 보안 체계 -> 안전하게 데이터 보관 가능
- 권한기능: 여러 사람 등록 가능 -> 전체적 혹은 부분적 읽기, 수정 가능 차등적 권한

## 데이터 작업
1. 데이터베이스 생성

![[스크린샷 2025-10-21 오전 9.37.55.png]]

2. 표 채우기
 ![[스크린샷 2025-10-21 오전 10.06.54.png]]

3. 표 확인하기
	- SELECT *FROM topic;

4. 표 확인하는 여러 방법
	-  SELECT id, title, created, author FROM topic;

5. 행 추가하기
- INSERT topic (title,description,created,author,profile) VALUES('ORACLE', 'ORACLE is',now(),'egoing','developer');
- 
6. 표 수정하기
- PDATE topic SET description='MongoDB is...', title='MongoDB',profile='data scientist',author='egoing'  WHERE id=2;

7. 표 합치기
- SELECT *FROM topic LEFT JOIN author ON topic.author_id = author.id;

8. 합친 표 불러오기
- SELECT topic.id, title, description, created, name, profile FROM topic LEFT JOIN author ON topic.author_id = author.id;
- SELECT topic.id AS topic_id, title, description, created, name, profile FROM topic LEFT JOIN author ON topic.author_id = author.id;

## MySQL workbench
- gui 기반      cf) 명령어 기반  
- MySQL 데이터베이스를 시각적으로 쉽게 관리하고 조작할 수 있게 해주는 도구
- ![[스크린샷 2025-10-21 오후 3.44.14.png]]