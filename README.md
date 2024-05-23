## Git/Github# Git

### Git 이란?

- 버전 관리 시스템 (Version Control System)
- 파일의 이름 변경 없는 버전 관리 시스템

### Git 명령어

### ✅ git init

- 현재 디렉토리(버전 관리를 위한 디렉토리)에 작업을 진행하겠다고 git에게 알려주는 명령어
- .git 디렉토리 생성
- .git은 개발 과정에서 수 많은 commit과 branch 및 관리되는 파일의 정보들이 모두 저장되는 곳
- .git을 삭제하고 싶다면 <rm -rf .git> 입력

### ✅ git status

- git 저장소의 상태를 보여주는 명령어

### ✅ git add

- git에게 새로운 혹은 수정된 파일을 관리하도록 알려주는 명령어

: git add <파일> → 파일을 stage 영역으로 올려준다

- git add → stage → commit
- commit 대기 상태로 만들어 주고 파일을 stage 영역으로 올려준다

: stage 영역은 commit을 하기 위해 파일이 대기하는 영역  

### ✅ git commit

- git에 저장하는 명령어
- stage 영역의 commit 대기 상태의 파일을 commit한다
- commit은 각자 고유의 commit_ID를 갖는다
- commit 전 add 필요

: commit 한 개는 한 개의 작업을 가지고 있는게 가장 이상적이다

그런데 commit 시기를 놓쳤을 때 commit 하고자 하는 파일만 stage 영역에 올려  commit 시키기 위해 commit 전 git add 명령을 입력한다

*commit 옵션*

📌 git commit -m “커밋미세지” 

: 커밋을 진행하면 vim에서 커밋 메시지를 작성하는데 이러한 과정을 간소화 하기 위한 명령어

 

📌 git commit -am “커밋미세지”

: 별도의 add명령어를 사용하지 않고, 수정된 모든 파일에 대해 add→commit을 한번에 수행하고 commit

  메세지를 동시에 작성 하지만 한 번도 git add 되지 않은 파일은 commit되지 않는다. 따라서 적어도 한 번 
  은 add 되어야 한다

📌 git commit --amend

: 마지막 commit 메세지 수정 → commit 메세지 수정은 로컬 저장소에만 진행 할 것 push한 후 이후의 

  내용은 수정하지 않기 

### ✅ git log

- 지금까지의 (commit)히스토리를 보여준다
    
    
    *log 옵션*
    
    📌 git log -p
    
    : commit 사이의 소스상의 차이를 확인할 수 있다
    
    📌 git log --reverse
    
    : 로그를 역으로 보여준다 → 첫 번째 commit이 가장 상단에 위치 기존에는 제일 하단에 위치
    
    📌 git log <branch>..<branch>
    
    : branch 간의 차이를 알 수 있다
    
    📌 git log -p <branch>..<branch>
    
    : branch 간의 차이를 소스 코드 수준까지 알 수 있다
    
    📌 git log --branches --decorate
    
    : branch의 상태 확인이 가능하다
    
    📌 git log --branches --decorate --graph
    
    : branch의 상태를 graph로 보여준다 
    
    📌 git log --branches --decorate --oneline
    
    : branch의 상태를 graph로 표현하고 한 줄로 표시해준다 
    

### ✅ git diff

- 파일 수정후 commit 전(git add전) 해당 명령어로 수정 사항에 대해 오류가 있는지 소스 상의 차이를 확인할 수 있다

*diff 옵션*

📌 git diff <commit_ID>..<commit_ID>

: 두 commit 사이의 소스 상의 차이를 확인할 수 있다 

### ✅ git branch

- branch를 확인하는 명령어
- branch는 작업을 진행 중 필요에 의해서 분기되는 것을 의미
- 기본적으로 1개의 branch를 가지고 있다 (master or main branch)
- branch를 생성하면 기존의 상태(commit상태 ..등)를 그대로 복사한다

*branch 옵션*

📌 git branch <branch>

:  <branch> 이름의 branch 생성

📌 git branch -d <branch>

: <branch> 이름의 branch 삭제

### ✅ git checkout <branch>

- <branch> 이름의 branch로 branch 변경

*checkout 옵션*

📌 git checkout -b <branch>

: <branch> branch를 생성하고 해당 branch로 checkout 진행 

📌 git checkout <commit_id>

: <commit_id>로 branch 변경 

### ✅ git merge

- branch를 병합하기 위한 명령어
- Fastfoward 방식과 Recursive Strategy 방식 존재
- git merge <branch>

: 현재 branch에 <branch>를 merge한다

- FastFoward 설명
    
    ![스크린샷 2024-03-28 오후 12.47.56.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/635cc3d8-c6ad-4648-9ebb-f81c1fa49ea1/9fcbafe0-605a-49a4-928e-daa8d9e7906c/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-03-28_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_12.47.56.png)
    
    - C0 commit → C1 commit → C2 commit 후 iss53 branch로 분기
    - iss53 branch는 현재까지 master branch 상태와 동일한 상태를 갖는다
    
    ![스크린샷 2024-03-28 오후 12.48.07.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/635cc3d8-c6ad-4648-9ebb-f81c1fa49ea1/7efe4de2-3549-4b92-9bf1-baac72af5148/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-03-28_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_12.48.07.png)
    
    - iss53 branch는 수정 후 C3 commit 진행
    
    ![스크린샷 2024-03-28 오후 12.48.24.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/635cc3d8-c6ad-4648-9ebb-f81c1fa49ea1/6d102b24-5326-469a-9feb-90038451f5fd/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-03-28_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_12.48.24.png)
    
    - 급하게 수정 할 내용이 생겨 master branch에서 hotfix branch로 분기 후 파일 수정 후 C4 commit 진행
    - 현재 iss53과 hotfix branch는 동일한 부모 commit을 갖는다
    - hotfix branch는 더 이상 필요하지 않기 때문에 branch에서 삭제 시켜준다
    - fastfoward는 새로운 commit을 생성하지 않는디
    
    ![스크린샷 2024-03-28 오후 12.49.09.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/635cc3d8-c6ad-4648-9ebb-f81c1fa49ea1/8c36cfa6-861e-4bc3-b689-cf6e1067b5ef/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-03-28_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_12.49.09.png)
    
    - master branch에서 hoxfix bracnh를 merge 진행
    - 첫 번째 commit의 기록을 따라 도달할 수 있는 commit이 하나의 commit을 merge할 때 merge할 다양한 작업이 없기 때문에 단순히 포인터를 앞으로 이동항 작업을 단순화하는데 이를 fastforwar(빨리감기) 라고 한다

- Recursive strategy 설명
    
    ![스크린샷 2024-03-28 오후 1.03.01.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/635cc3d8-c6ad-4648-9ebb-f81c1fa49ea1/9ebe33c6-d0a7-4bed-a911-44aa260f4684/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-03-28_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_1.03.01.png)
    
    - 위 fastforwd 후 연속해서 진행하는 상태
    - iss53 branch에서 C5 commit 진행 후 master branch로 checkout
    - master branch에서 iss53 branch를 merge 준비
    
    ![스크린샷 2024-03-28 오후 1.03.10.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/635cc3d8-c6ad-4648-9ebb-f81c1fa49ea1/18b66e22-69c7-41cb-b25c-2e144d572f1b/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-03-28_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_1.03.10.png)
    
    - iss53 branch와 master branch는 C2라는 조상 commit을 갖는다
    - merge 수행 → 공통 조상을 이용한 3-way merge 진행
    
    ![스크린샷 2024-03-28 오후 1.03.20.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/635cc3d8-c6ad-4648-9ebb-f81c1fa49ea1/33310493-c21e-46a7-926d-49dea0bde4db/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-03-28_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_1.03.20.png)
    
    - 3-way merge는  merge시 merge commit을 즉 새로운 commit을 생성한다

### ✅ git stash

- 특정 branch에서 작업을 진행하던 중 작업이 끝나기 전 다른 branch로 checkout 해야할 때 끝나지 않은 작업에 대한 commit을 진행하기 애매할 뿐더러 commit을 진행하지 않는다면 checkout이 불가능하다 이러한 문제를 해결하기 위해서 stash(숨기다) 작업을 통해서 수정사항을 commit을 진행하지 않고 내용을 숨겨두어 다른 branch로의 checkout이 가능해진다
- git stash가 되기 위해서는 파일에 대해 적어도 버전 관리(git add)가 시작되고 있어야 한다
- stash 목록은 LastInFirstOut 구조를 갖는다

*stash 옵션*

◽️ git stash save

1. save는 생략하고 git stash만 사용가능 다만 명확히 해주기 위해 git stash save로 작성

     (commit 되기전의)변경된 내용을 Working Directory에서 감춘다

📌 git stash list

: stash 목록을 확인 할 수 있다 

📌 git stash apply

: stash 목록에서 가장 최신 stash를 가져온다. 다만 stash list에서 사리지지 않는다

📌 git stash drop

: stash 목록에서 가장 최신 stash를 삭제 

📌 git stash pop

: git stash apply와 git stash drop 명령을 동시에 처리해준다

---

### Github 란?

- 형상 관리(변경 사항을 추적, 제어하는 과정) 플랫폼이다
- Git 시스템을 기반으로 소스 코드와 관련 파일을 저장하고 관리할 수 있는 웹 기반 호스팅 서비스 제공
- 버전 관리, 협업, 이슈 트래킹, 웹 호스팅, 오픈소스 라는 특징을 갖는다

### 원격 저장소 주소 방식

1. HTTP 방식
- HTTP 방식은 원격 저장소 접속 시 아이디와 비밀번호를 입력해야함

1. SSH 방식 
- SSH 경우 원격 저장소 접속 시 비밀번호 입력없이 안전하게 로컬 컴퓨터가 원격 저장소에 접근이 가능
- 그림과 같이 SSH 방식을 이용하기 위해서는 key가 필요하다 해당 키는 Mac을 기준으로 터미널에 
ssh-keyagent 명령어를 입력하여 두 개의 키를 생성할 수 있다. 해당 키 중 id_rsa.pub 키는 원격 저장소에 등록하여 사용하면 된다.

![스크린샷 2024-04-05 오전 8.34.55.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/635cc3d8-c6ad-4648-9ebb-f81c1fa49ea1/5e0c9bed-6753-4a83-8a00-5d84a6be65c3/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-04-05_%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB_8.34.55.png)

### Github(원격 저장소) 관련 Git 명령어

### ✅ git clone

- 원격 저장소의 내용을 로컬 저장소로 가져온다
- git clone은 remote add를 한 다음 pull까지 진행

*clone 옵션*

📌 git clone <원격 저장소 주소>  <로컬 디렉토리>

: 원격 저장소 주소로 로컬 저장소의 원하는 디렉토리로 내용을 가져온다. 디렉토리가 없다면 디렉토리를 생성, 
  <로컬 디렉토리> 는 생략 가능 

### ✅ git remote

- 우리의 로컬 저장소에 원격 저장소를 연결시킨다

*remote 옵션*

📌 git remote add origin <원격 저장소 주소>

: 원격 저장소 주소를 origin으로 정의하고 로컬 저장소와 원격 저장소를 연결해준다

 

### ✅ git push

- 로컬 저장소를 기준으로 원격 저장소로 작업을 내보낸다
- 작업 전 git pull을 통해 원격 저장소의 내용을 로컬 저장소로 가져오고 작업을 진행한 후 git push 진행

*push 옵션*

📌 git push -u origin <branch>

: 현재 checkout 되어 있는 로컬 <branch>를 origin에 해당되는 원격 저장소 <branch>로 동기화한다

그리고 git push 명령어를 입력하면 <branch>로 push된다

### ✅ git pull

- 원격 저장소의 내용을 로컬 저장소로 가져오는 작업을 한다
