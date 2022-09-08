✔리눅스 명령어
pwd = print working directory
ls = list
cd = change directory
mkdir = make directory
rm = remove

✔깃 초기화 하기
git init
✔깃 상태 확인하기
git status

on branch master : 현재 master브랜치에 있다.

No commit yet : 아직 커밋한 파일이 없다.

nothing to commit : 현재 커밋할 파일이 없습니다.

✔수정한 파일을 스테이징 하기
git add

✔스테이지에 올라온 파일 커밋하기
git commit 이고 -m 옵션을 붙이면 커밋과 함께 저장할 메세지 적을 수 있다.

✔깃에서 버전이란 수정하고 저장할 때마다 생기는 것.

![image](https://user-images.githubusercontent.com/108383234/188787198-908e8abb-10c5-4af3-821c-e45a9402917a.png)

작업 트리(working tree) : 파일 수정, 저장 등의 작업을 하는 디렉토리.
스테이지(stage) : 버전으로 만들 파일을 대기하는 곳.
저장소(repository) : 저장소 = 리포지토리. 
                         스테이지에서 대기하고 있던 파일들을 버전으로 만들어 저장하는 곳.



😢커밋하다가 생긴 오류

error: failed to push some refs to

생긴 이유 : 깃허브에서 직접 파일을 수정한 다음

​                    내 컴퓨터에 공부한 내용의 파일을 만듦.

​                    이후에 새로 만든 파일을 커밋하려니깐 

​                    할 수 없다는 에러가 뜸.

해결 방법 : git pull 원격저장소별칭 master

​                   이후에 다시 push하면 정상적으로 작동된다. 
