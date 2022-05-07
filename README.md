# Git-Github-Study
깃/깃허브 공부 레포지토리🔎


### checkout

- **git checkout :** 깃 브랜치 변경 (다른 브랜치의 마지막 커밋으로 HEAD 이동)
- **git checkout -b [브랜치명]** : 생성 + 변경
- **git checkout -t [저장소명]/[브랜치명]** : 원격 저장소의 브랜치 가져오기
    - 원격 저장소에 브랜치에 접근 전 `git remote update` 명령어로 갱신해줄 필요가 있다.
- git 2.23 버전부터 **switch** 등장

---

### branch

- **git branch** : 로컬 브랜치 목록 보기
- **git branch [브랜치명]** : 새 브랜치 생성
- **git branch -r** : 원격 브랜치 목록 보기
- **git branch -a** : 로컬 + 원격 브랜치 목록 보기
- **git branch -m [브랜치명] [바꿀 브랜치명]** : 브랜치 이름 바꾸기
- **git branch -d [브랜치명]** : 브랜치 삭제하기
- **git branch -v :** 브랜치의 마지막 커밋 메세지 확인
- **git push origin --delete [브랜치명]** : 원격 브랜치 삭제

---

### remote

- **git remote :** 현재 원격 저장소 확인
- **git remote -v :** 원격 저장소가 여러개 있으면 전부 보여준다. (이름 + url)
- **git remote add [저장소명] [github 저장소 주소] :** 원격 저장소 연결
- **git remote rename <기존 저장소 이름> <변경할 저장소 이름> :** 원격 저장소 이름 변경
- **git remote remove <리모트 저장소 이름>** : 원격 저장소 삭제

---

### push (+ add, + commit)

- **git push [저장소명] [브랜치명] :** 원격 저장소에 업로드
- **git push -u [저장소명] [브랜치명] :** 최초 입력 후 커밋 부터는 git push 만 날리면 되도록 해준다.
- **git push -f [저장소명] [브랜치명] :** 강제 푸쉬
