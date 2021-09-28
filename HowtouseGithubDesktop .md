# 왕초보들을 위한 GitHub Desktop 사용법

깃허브 초보자를 위한 깃허브 데스크톱 사용법입니다 :) 사실 깃을 사용한 지 얼마 안되었을 때는 커맨드 창에 직접 명령어를 쓰면서 깃을 익히는 게 좋지만, `GUI` 툴 중 하나인 깃허브 데스크톱을 쓰는게 솔직히... 편하니까요..:smiley:

<br>

### 1. 깃허브 데스크톱 설치하기 :green_apple:

> https://desktop.github.com

<br>

### 2. 깃허브 데스크톱과 깃허브 계정 연동하기 :apple:

**로그인 하는 법 :**

**File :arrow_forward: Options :arrow_forward: Accounts :arrow_forward: Sign in :arrow_forward: 깃허브 계정으로 로그인하면 끝**

<br>

### 3. 저장소(Repository) 불러오기 :orange:

- **깃허브 데스크톱 상에서 불러오는 법**

  **File :arrow_forward: Clone Repository... :arrow_forward: 밑 화면에서 원하는 Repository를 클릭하고 Clone버튼을 누른다.**

  ![img_clone_repository](/Image/img_clone_repository.png)

- **깃허브 홈페이지에서 불러오는 법**

  Clone을 원하는 Repository에 들어가서 오른 쪽 상단에 뜨는 초록색 Code버튼을 누른 후, **Open With GitHub Desktop**을 누른다.

  ![img_clone_repository_2](/Image/img_clone_repository_2.png)

<br>

### 4. Commit하는 방법 :lemon:

git에서는 Local Repository(현재 자신의 데스크톱 레포지토리)에 새로운 파일이 생기거나 기존의 파일이 수정, 삭제 등이 될 경우 Commit을 할 수 있게 됩니다! 이 때 `GUI`툴을 쓰면 간단하게 Commit이 가능합니다.

![img_commit_way](/Image/img_commit_way.png)

<br>

:bulb: 깃허브 데스크톱에서는 위 사진과 같이 Repository에서 추가, 수정, 삭제 등의 작업이 이루어진 파일들이 왼쪽에 보이게 됩니다. 위 사진에서 왼쪽 하단을 보시면 **Summary (required)** 라고 적힌 입력창이 보이실 텐데요, 여기가 바로 **Commit 메시지**를 적는 칸입니다! 로컬의 작업물을 GitHub 사이트의 Repository에 올리기 위해서는 Commit 메시지를 작성하는 게 필수이므로, 모두 적절한 Commit 메시지를 남겨주시기 바랍니다 :)

<br>

**:heavy_check_mark: 여기서 참고하면 좋은 자료 : [Git Commit Message Convention](https://github.com/8-seconds/WIKI_FOR_8_SECONDS/blob/main/GitHub/CommitMessageConvention.md)**

<br>

### 5. Push하는 방법 :grapes:

**4번**에서 Commit 메시지를 작성한 후, 왼쪽 아래 Commit to main을 누르면, Push 버튼이 상단 버튼에 활성화 되는데 이것을 누르면 현재 **Branch**의 푸시가 완료되고, GitHub 사이트의 Repository에 파일들이 올라간 모습을 볼 수 있습니다.

![img_push_way](/Image/img_push_way.png)

<br>

### 6. Pull 하는 방법 :avocado:

외부 저장소(GitHub사이트에 있는 Repository)에서 변화가 생기면, Local Repository에서는 그것을 Pull 받아와서 현재 Local에 합쳐줄 수 있는데요, GitHub Desktop에서는 외부 저장소에서 변화가 생기면 자동적으로 Pull 버튼이 활성화되고(**위 5번 사진 push 버튼이 있는 자리에 활성화 됩니다!**) 이 때 이 버튼을 누르면 Pull이 완료됩니다. 
