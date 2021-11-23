# Git Flow System
---
## 1. git flow란
- git branch의 활용사례
- master는 최종 배포용이므로 해당 부분에서 작업을 최소화 하는 방법
- master에서 작업을 하는 것이 아니라 바로 branch를 만들어서 테스트용 가지(development)로 만듦
- 각자가 master에서 branch를 만들어 작업 후 development에서 합침
- 이때 development branch에서 conflict 해결, 검토, 수정 후 master로 옮기기
**즉, master는 최종 배포용으로만 만들기**

## 2. git flow의 구성
<img src="https://github.com/suntonglife/TIL/blob/a9330f644c55a216bb5fdb68559e3e55cd0fe011/Git/img/git-flow.png" width="50%" height="50%">

### 2.1. master
- 제품으로 바로 출시될 수 있는 branch
-  master는 언제나 실행가능한 상태여야 함
- master에 올릴때마다 태그로 버전정보를 입력하는 것이 좋음(v1.0.0)
- **git merge --no-ff 병합할 branch**: 병합할 branch를 merge 할 때 fast forward 하지마! 
즉, 기존의 branch를 가만히 두고 새로운 commit을 만들어 해당 commit에서 merge

### 2.2. develop(dev,development)
- master에 올리기 위한 과정을 작업하는 branch

### 2.3. release
- 출시준비를 하는 branch
- 버그 등을 잡아서 지속적으로 develop branch로 병합시킴

### 2.4. feature
-기능을 개발하는 branch

### 2.5. hotfixs
- 긴급하게 수정해야할 오류를 수정하는 branch
