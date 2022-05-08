# Git-Github-Study
깃/깃허브 공부 레포지토리🔎


### checkout

- **git checkout :** 깃 브랜치 변경 (다른 브랜치의 마지막 커밋으로 HEAD 이동)
- **git checkout -b [브랜치명]** : 생성 + 변경
- **git checkout -t [저장소명]/[브랜치명]** : 원격 저장소의 브랜치 가져오기
    - 원격 저장소에 브랜치에 접근 전 `git remote update` 명령어로 갱신해줄 필요가 있다.

---

### branch

- **git branch** : 로컬 브랜치 목록 보기
- **git branch [브랜치명]** : 새 브랜치 생성
- **git branch -r** : 원격 브랜치 목록 보기
- **git branch -a** : 로컬 + 원격 브랜치 목록 보기
- **git branch -m [브랜치명] [바꿀 브랜치명]** : 브랜치 이름 바꾸기
- **git branch -d [브랜치명]** : 브랜치 삭제하기
- **git branch -v :** 브랜치의 마지막 커밋 메세지 확인
- **git push [저장소명] --delete [브랜치명]** : 원격 브랜치 삭제

---

### remote

- **git remote :** 현재 원격 저장소 확인
- **git remote -v :** 원격 저장소가 여러개 있으면 전부 보여준다. (이름 + url)
- **git remote add [저장소명] [github 저장소 주소] :** 원격 저장소 연결
- **git remote rename <기존 저장소 이름> <변경할 저장소 이름> :** 원격 저장소 이름 변경
- **git remote remove <리모트 저장소 이름>** : 원격 저장소 삭제 (연결 끊기)

---

### reset

- **HEAD :** 현재 브랜치를 가리키는 포인터이며, 커밋 중 가장 마지막 커밋을 가리킨다
- **git commit --amend** : 메시지만 잘못 입력한 경우에는 메시지를 수정할 수 있다.
- **reset :** 시간을 **아예** 과거의 특정 사건(commit)으로 되돌린다.
    - 현재 브랜치가 가리키는 커밋을 바꾼다
    - 현재가 없었던 것 처럼 원하는 과거로 돌아갈 수 있다. (이력이 남지 않음)
    
    ```
    git reset --soft [commit ID] // commitID 는 끝까지 다 안써도 된다.
    git reset --mixed [commit ID]
    git reset --hard [commit ID]
    git reset HEAD~10
    git reset HEAD^
    ```
    
    - **soft** : commit된 파일들을 staging area로 돌려놓음. (commit 하기 전 상태로 = add)
        - HEAD가 가리키는 브랜치를 옮긴다.
        - 돌아가려는 커밋으로 되돌아가고, HEAD가 돌아가려는 커밋을 새롭게 가리키게 된다.
        - staging area와 working directory는 아무런 변화도 없다.
        
        ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ce6afc68-dc89-4210-bf37-bea167362d36/Untitled.png)
        
    - **mixed (**default): commit된 파일들을 working directory로 돌려놓음. (add 하기 전 상태로)
        - Index를 HEAD가 가리키는 상태로 만든다.
        - 돌아가려는 커밋으로 되돌아가고, HEAD가 돌아가려는 커밋을 새롭게 가리키게 된다.
        - staging area는 돌아가려는 커밋과 동일해지고, working directory는 아무 변화가 없다.
        
        ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/acbc95b1-dde5-44d3-a60e-34384297c080/Untitled.png)
        
    - **hard** : commit된 파일들 중 tracked 파일들을 working directory에서 삭제
        - 1. 워킹 디렉토리를 Index의 상태로 만든다.
        - 돌아가려는 커밋 이후의 모든 내용을 지워 버린다.
        - staging area와 working directory 모두 돌아가려는 커밋과 동일해진다.
        - 이미 push한 commit을 취소할 경우에는 강제로 push해주어야 한다.
            - git push -f 또는 git push origin +master
        
        ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7c5b7921-2739-4f3f-bf70-738e579f0ef4/Untitled.png)
        
    - **HEAD~취소할 커밋수** : 현재로부터 원하는 만큼의 커밋이 취소된다.
    - **HEAD^** : 가장 최근의 커밋이 취소된다.
    - `git reset --hard ORIG_HEAD` : pull 취소
    - `git reset --merge ORIG_HEAD` : merge 취소
        - ORIG_HEAD는 이전 작업한 곳의 HEAD를 의미
- 혼자만 사용하는 브랜치인 경우
- origin에 있지만 아무도 이 브랜치를 사용하지 않는다는 확신을 가지는 경우

---

### push (+ add, + commit)

- **git push [저장소명] [브랜치명] :** 원격 저장소에 업로드
- **git push -u [저장소명] [브랜치명] :** 최초 입력 후 커밋 부터는 git push 만 날리면 되도록 해준다.
- **git push -f [저장소명] [브랜치명] :** 강제 푸쉬

---

### merge

- merge 할 브랜치로 이동 후 작업
- **git merge [병합할 브랜치명] :** 현재 브랜치에 대상 브랜치를 병합
    - 하나의 브랜치와 다른 브랜치의 변경 이력 전체를 합치는 방법
    - 시간축에 따라 병합 커밋들이 사이사이에 들어간다.
    - 한번에 눈에 들어오지 않음
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/93a47628-abff-48c3-92df-1f475b6bf650/Untitled.png)
    
- **git merge —squash [병합할 브랜치명] :** 현재 브랜치에 대상 브랜치를 병합
    - 하나의 새로운 커밋이 생성됨 → git commit -m “message” 진행
    - **—squash :** 모든 커밋을 하나의 커밋으로 병합
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d12ef760-3431-4780-9fe7-825672011609/Untitled.png)
    

---

### stash

- ****코드 잠깐 저장하고, 다른 브랜치로 이동하기****
- A라는 Branch에서 작업을 하던중 급하게 들어온 요청 혹은 Bug가있어 B 브랜치로 이동해야할 때 → 작업은 완료되지 않아서 commit 해두기에는 애매하고, 그렇다고 다시 작업하기에는 작업량이 있어 버릴수는 없는경우 → 잠깐 다른 공간에 변경 내역을 기록해 두고 브랜치를 변경해서 작업한후 다시 돌아와서 변경 내역을 불러와 계속 작업을 이어 나갈 수 있다.
