# Git 사용법-VScode 활용
----
## 1. VScode 기본
### 1.0. Tip
- 화살표 ↑버튼: 이전에 친 명령어 자동입력
- 만약 프롬프트로 할 경우 cd 파일경로: 해당파일로 들어가겠다
- **clear**: 터미널 내용 지우기
- **esc+:q**: 빔 에디터를 나가는 방법
- **git 특정명령어(ex>remote) --help**: 관련 명령어의 세부설명 페이지 요청
   - ###### 이때의 설명 속 []내용은 선택사항으로 안써도 무방한 내용들
- **git tag v1.0**: 현재 commit에 태크를 다는 것으로 숫자 6자리 대신 이 버전(v1.0)을 입력해도 가능
- **git stash**: 현재 branch의 내용을 임시저장
- **git stash apply**: 임시저장 내용 불러오기
- **git stash list**: 임시저장 목록 불러오기
  - ###### stash로 임시저장한 내용은 다른 branch에서 불러오기도 가능(실수로 다른 branch에서 작업하고 있었을 때 효과적)

### 1.1. creat(파일생성)
- 원하는 위치에 파일 생성 후 vscode로 열기
- 파일 작성 후 저장
- **ctrl+`**: 터미널 열기
- (만약 프롬프트로 할 경우 **cd 파일경로**: 해당파일로 들어가겠다)
- **git init**: git의 관리를 받기 시작
- **git config --global user.name'suntonglife'**: 내 아이디로 연결
- **git config --global user.email'tjtsghd97@gmail.com'**: 내 아이디로 연결(두개 다 쳐줘야함)
- 저장폴더에 .git숨김파일이 열렸는지 확인

### 1.2. commit(버전생성)
- **git status**: 아직 stage에 올려지지 않은 파일종류 보기
- **git add –A**: stage에 모든파일 올리기
- **git add 파일명.파일형식(ex>file.txt)**: 특정 파일을 올리기
- **git rm 파일명.파일형식**: 특정 파일을 stage에서 내리기
- **git rm –r 폴더명**: 해당 폴더의 모든 파일을 stage에서 내리기
- **git diff**: 변경사항 보기
- **git commit –m "commit에 붙일 부가설명**": 부가설명과 함께 stage상 파일 commit 하기
- **git commit -am "commit에 붙일 부가설명**": add와 commit을 동시에 하는 명령어
- **git log**: history 보기
(만약 git log 입력 후 타자가 안쳐질 경우 **:q**를 누르면 해결가능)

### 1.3.gitignore
- 추적을 무시하고 싶은 경우 사용하는 것
- 여기에 git에서 관리하지 않았으면 하는 파일명을 올리면 해당 파일은 걸들이지 않음
- 이때 폴더형식, 파일형식은 꼭 다 갖춰서 적을 것
- 이미 commit을 한 파일을 제외하고 싶은 경우 제거해서 다시 commit 후 해당 파일을 등록해야함(이미 commit 된 상태로는 gitignore가 안됨)

### 1.4. reset(되돌리기)
- 과거로 돌아가고 해당 시점 이후의 수정사항은 삭제되는 것
- **git log**: history 보기
- **git reset <span style="color:darkblue">돌아갈시점의 commit의 앞 6자리</span> --soft**: 돌아갈 시점으로의 이동 및 수정사항 staged된 상태
- **git reset <span style="color:darkblue">돌아갈시점의 commit의 앞 6자리</span> --mixed**:돌아갈 시점으로의 이동 및 수정사항 modified된 상태 
 **git reset <span style="color:darkblue">돌아갈시점의 commit의 앞 6자리</span> --hard**: 돌아갈 시점으로 이동 및 이후 수정사항 초기화
  - ###### **soft, mixed, hard 존재**: soft는 stage에 올라간 상태, mixed는 stage에는 안올라간 상태, hard는 아예 삭제된 상태
-  **git reset HEAD~1**: 현 시점에서 1(숫자는 변경가능)개만큼 commit 취소

### 1.4. revert(되돌리기2)
- 과거로 돌아가되 해당시점 이후의 수정사항을 그대로 둔 상태로 새로운 revert 생성
- **git log**: history 보기
- **git revert  <span style="color:darkblue">취소할시점의 commit 앞 6자리**: 해당 수정내용을 취소하겠다
- **:wq**: 그대로 저장하겠다.
  - ###### 주의: 이전 단계부터 순차적으로 revert해야함(2단계 전으로 돌리고 싶다면 1단계씩 2번에 나눠서 해야함)
- 즉, revert는 클릭한 부분이 이전과 비교해 수정된 사항만 되돌리는 것!

### 1.5. branch(가지치기)
- 가지치기
- **git branch branch 이름**: branch이름으로 가지치기
- **git branch**: 현재 local branch 현황
- **git branch -a**: 원격, local의 branch 현황
- **git checkout <span style="color:darkblue">이동하고싶은 branch**</span>: 이동하고 싶은 branch로 이동
- **git checkout -b branch이름**: branch 생성 + 이동까지!
- **git checkout -b <span style="color:red">branch이름1</span> <span style="color:purple">원격이름(ex>orgin)</span>/<span style="color:darkblue">가져올 branch이름2**</span>: branch이름1을 새로 만들어 원격이름에 있는 branch이름2를 pull하고 branch이름1로 넘어가겠다! 
  - ###### 주의: 이동 전까지 현 branch의 내용을 commit을 한 뒤에 다른 branch로 넘어가야 현 branch에서의 수정사항이 날라가지 않음
  - ###### 만약 commit 없이 다른 branch로 이동하고 싶은 경우 stash사용
- **git stash**: 현재 branch의 내용을 임시저장
- **git stash apply**: 임시저장 내용 불러오기
- **git branch –D <span style="color:darkblue">삭제할 branch**</span>: local의 branch 삭제
- **git push -d <span style="color:darkblue">원격이름</span> <span style="color:red">branch이름**: 원격저장소의 branch 삭제

### 1.6. merge(병합)
- **git checkout <span style="color:darkblue">main이 될 branch**: main이 될 branch로 이동
- **git merge <span style="color:darkblue">main에 합쳐질 branch**: 합쳐질 branch를 main branch에 병합
- **git log --graph --all --decorate**: 그림으로 보여주기

### 1.7 cherry pick
- branch의 모든 commit을 병합하는 것이 아닌 일부 중요사항만 빼오는 것
- **git chrry-pick <span style="color:darkblue">빼올 commit의 앞6자리**: commit을 빼와서 branch에 내용 추가(두 branch가 병합되진 않음)

## 2. 협업하기
- **git remote <span style="color:darkblue">add local이름(ex>orgin) <span style="color:red">url**: 원격 url의 주소를 local 이름으로 저장해 두겠다.
- **git pull <span style="color:darkblue">원격이름(ex>orgin)**: 원격저장소에서 orgin의 버전을 가져옴
- **git push <span style="color:darkblue">원격이름(ex>orgin)</span> <span style="color:red">branch이름:** 원격저장소 orgin에 현재의 branch를 올림


## 3. Git Flow
### 3.1. 일반적으로 git flow란
- master는 최종 배포용이므로 해당 부분에서 작업을 최소화 하는 방법
- master에서 작업을 하는 것이 아니라 바로 branch를 만들어서 테스트용 가지(development)로 만듦
- 각자가 master에서 branch를 만들어 작업 후 development에서 합침
- 이때 conflict 해결, 검토, 수정 후 master로 옮기기
- 즉, master는 최종 배포용으로만 만들기

### 3.2 급한 버그발생시
- branch를 쳐서 바로 수정 후 master에 배포
- 이 때 버그 수정 후 최종본은 다시 테스트용 가지와 각자 파일본으로 다시 pull해와야 함
