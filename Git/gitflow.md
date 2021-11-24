# Git Flow System
---
## 1. git flow란
- git branch의 활용사례
- master는 최종 배포용이므로 해당 부분에서 작업을 최소화 하는 방법
- master에서 작업을 하는 것이 아니라 바로 branch를 만들어서 테스트용 가지(development)로 만듦
- 각자가 master에서 branch를 만들어 작업 후 development에서 합침
- 이때 development branch에서 conflict 해결, 검토, 수정 후 master로 옮기기
**즉, master는 최종 배포용으로만 만들기**
<br>

## 2. git flow의 구성
<img src="https://github.com/suntonglife/TIL/blob/a9330f644c55a216bb5fdb68559e3e55cd0fe011/Git/img/git-flow.png" width="50%" height="50%">

### 2.1. master
- 제품으로 바로 출시될 수 있는 branch
-  master는 언제나 실행가능한 상태여야 함
- master에 올릴때마다 태그로 버전정보를 입력하는 것이 좋음(v1.0.0)
- **git merge --no-ff 병합할 branch**: 병합할 branch를 merge 할 때 fast forward 하지마! 
- 즉, 기존의 branch를 가만히 두고 새로운 commit을 만들어 해당 commit에서 merge
<img src="https://github.com/suntonglife/TIL/blob/94d32b211e675e43b661c3e1c5f234369b16caf1/Git/img/no--ff.gif" width="80%" height="80%">

### 2.2. develop(dev,development)
- master에 올리기 위한 과정을 작업하는 branch

### 2.3. release
- 출시준비를 하는 branch
- 버그 등을 잡아서 지속적으로 develop branch로 병합시킴

### 2.4. feature
-기능을 개발하는 branch

### 2.5. hotfixs
- 긴급하게 수정해야할 오류를 수정하는 branch
<br>

## 3. Git flow command line program(gitflow cli)
<img src="https://github.com/suntonglife/TIL/blob/94d32b211e675e43b661c3e1c5f234369b16caf1/Git/img/gitflowcil.png" width="80%" height="80%">

### 3.1. 관련 코드
- **git flow init**: git flow model 생성(5가지의 branch 이름 설정창이 나타남)
- **cat . git/config**: git flow와 관련된 설정들이 나타남
  
### 3.2. feature(새기능 개발)
- 해당 작업(branch, merge)은 모두
- **git flow feature start 브랜치 이름**: 브랜치 이름을 가진 feature branch 생성(develop branch에서 진행)
- **git flow feature finish 브랜치 이름**: 브랜치 이름을 가진 feature branch를 병합(feature branch에서 진행)
   - 이때 자동으로 local branch의 해당 feature branch는 삭제됨
- **git flow feature publish 브랜치 이름**: 브랜치 이름을 가진 브랜치를 원격저장소로 push
- **git flow feature pull origin 브랜치 이름****: 브랜치 이름을 가진 브랜치를 원격 저장소에서 pull

### 3.3. release(출시준비)
- **git flow release start **브랜치 이름****: 브랜치 이름(주로 버전을 입력)의 브랜치가 생성되고 해당 브랜치로 이동까지 하게 됨
- **git flow release publish **브랜치 이름****: 브랜치 이름의 브랜치를 원격 저장소에 push
- **git flow release finish **브랜치 이름****: 브랜치 이름의 브랜치를 master와 develop에 동시에 업로드 하는 작업
   - 이때 release branch는 삭제됨
   - **첫번째 뜨는 화면**: master와 병합하는 작업에 대한 commit message
   - **두번째 뜨는 화면:** master에 병합시 붙일 태그
   - **세번째 뜨는 화면**: develop과 병합하는 작업에 대한 commit message
   - ###### 맨 윗줄에 입력 후 :wq 입력 시 저장

### 3.4. hotfix(master에 긴급한 버그 발생)
- **git flow hotfix start 브랜치 이름**: 가장 최근의 master에서 브랜치 생성
- **git flow hotfix finish 브랜치 이름**: 브랜치 이름의 브랜치를 master와 develop에 동시에 업로드 하는 작업
   - 이때 release branch는 삭제됨
   - **첫번째 뜨는 화면**: master와 병합하는 작업에 대한 commit message
   - **두번째 뜨는 화면:** master에 병합시 붙일 태그
   - **세번째 뜨는 화면**: develop과 병합하는 작업에 대한 commit message
   - ###### 맨 윗줄에 입력 후 :wq 입력 시 저장
<br>

## 참고자료
- 생활코딩 https://www.youtube.com/watch?v=w2F8O9J1keM

- CS Visualized: Useful Git Commands https://bit.ly/3nMHGfM
