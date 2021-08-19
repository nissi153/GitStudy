# GitStudy


깃 환경설정
1. 깃 설정 목록보기
git config --list
q //나가지

2. 깃 설정 에디터열기
git config --global -e

3.사용자 이름 설정
git config --global user.name "nissi153"
git config user.name 확인

4.사용자 이메일 설정
git config --global user.email "nissisoft21@gmail.com"
git config user.email 확인

5.캐리지리턴 \r 설정
  git config --global core.autocrlf true(윈도우즈)
  git config --global core.autocrlf input(맥)

현재 폴더를 깃으로 관리하기(.git폴더 생성)

1.깃 초기화
git init

2.깃에 파일 추가하기
git add . (현재 폴더아래 모든 파일)
git add *.png(확장자가 .png인 모든 파일)
git add image.png(image.png만)

3.커밋하기
git commit -m "first commit"

4.메인 브랜치 main으로 설정(예전에는 master)
git branch -M main

5 깃허브 원격저장소에 연결하기
git remote add origin [https url]

6. 원격저장소 목록 보기
git remote -v

7. 파일 내려받기
git pull origin

8. 목록만 내려받기
git patch origin

9. 파일 올리기
git push -u origin main

10. 깃 상태 보기
git status

11. 도움말보기
git 명령어 --h

12. 로그 보기
git log

13. 깃서버(깃허브) 저장소 파일 내려받기
git clong [git url] [폴더이름]
예) git clone https://github.com/nissi1543/GitTest.git Ex17_GitTest


충돌이 일어나는 상황

                 (개발자 A가 먼저 push함)
         +-- 개발자A가 수정한 a.java --+
a.java --+                             +-- a.java(A + B내용)
         +-- 개발자B가 수정한 a.java --+
                  (개발자 B는 push전/pull전)

예)git push origin master
에러메시지)
To https://github.com/nissi153/GitTest.git
 ! [rejected]        main -> main (non-fast-forward)
error: failed to push some refs to 'https://github.com/vlad/planets.git'

이때 개발자B는 어떻게 해야할까?
1. git pull origin main
에러메시지) CONFLICT (content): Merge conflict in a.java

2. a.java 편집하기 - 수동으로 최신 소스로 만들어 놓는다.
<<<<<<< HEAD  개발자B(나)가 편집한 내용
We added a different line in the other copy
=======
This line added to 개발자A가 올린 내용
>>>>>>> dabb4c8c450e8475aee9b14b4383acc99f42af1d

3. git add a.java
4. git status
5. git commit -m "resolved"
6. git push -u origin main
혹시 안되면 오류를 무시하고 그냥 강제로 올린다.   git push -u origin +main
7. git pull origin main

깃(Git) 사용하기
1. 깃허브 회원가입/로그인
팀장 역할
2. 깃허브 저장소(Repository) 생성하기 
* .git_ignore 파일에 *.jar를 주석처리해야 jar파일 올라감.
3. 설정에서 팀원 초대 메일 보내기
4. STS4 Ex17_GitTest 프로젝트 생성하기
5. git 프로그램 설치
6. Ex17_GitTest 프로젝트를 깃허브와 연결하기
6. 커밋/푸시/풀
팀원 역할
1. 초대 메일에서 링크 클릭
2. 깃에 연결된 소스 클론 해보기
3. 커밋/푸시/풀

+------------소스폴더--------------------+
|                    commit >            |  push>
|소스프로젝트  <-->깃 로컬저장소(.git)   | <--> 깃 원격저장소(깃허브)
|                     <pull              |  <patch
+----------------------------------------+

* 새로운 파일추가/삭제시 commit/push 시는 add to index해야 됨.

* 주의사항
1. 같은 파일을 푸시하지 않고 동시간대에 편집하지 않는다.
   충돌( Conflict )이 일어남 
   *충돌시 수동으로 머지(merge,병합) 해야 됨.
2. 같은 파일을 Push하고 나서 바로 팀원에게 알려서 Pull하고
    빌드 해보고, 오류가 없는지 확인후 작업 진행 한다.
3. 오류가 생기는 소스는 절대 Push하지 않는다. commit는 가능.
