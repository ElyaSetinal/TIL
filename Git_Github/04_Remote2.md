##  **Git, Github #4 :: Local and Github Interaction**

### *Local to My Repositories*

로컬 저장소에서 원격 저장소로 내보내는 명령

> git과 계정 및 원격 레포지토리가 연결된 상태이며, Local에서 commit까지 완료된 것으로 가정

commit된 버전을 원격 저장소에 내보내는데는 `push` 명령어를 사용한다.

```bash
git push {Github remote name} {Branch name}
```

#### *Branch is not main branch*

Local에서 main 브랜치가 아니라 다른 브랜치(편의상 sub라 부르겠다.)에서 작업하고 원격 저장소에 내보낼 때는 다음과 같은 명령어를 작성한다.

```bash
git push {Github remote name} sub
```

성공적으로 마친 경우, github에 새로운 branch가 등록되었다고 알림 표시를 띄운다.

<br>

### *My Repositories to local*

원격 저장소에서 로컬 저장소로 가져오는 명령

```bash
git pull {Github remote name} {Branch Name}
```

{Github remote name}에 해당하는 {Branch Name}의 모든 파일을 내 로컬 저장소로 가지고 온 후(Fetch) Merge(병합) 작업을 시행한다.

> Merge?    
로컬 저장소의 버전과 원격 저장소의 버전이 서로 상이한 경우, 이를 하나의 버전으로 묶어주는 작업    
e.g., 서울(First Commit)에서 A(로컬), B(원격) 두 팀이 출발 > A팀은 광명-수원, B팀은 성남-용인 (버전이 다름) > 합류를 위해 두 팀 모두 평택으로 이동(Merge; 병합)

Merge 작업 동안 서로 충돌(Conflict)이 나는 부분이 나오는데, 이를 수정 혹은 선택하고 Merge를 종료하면 하나의 파일이 되고 이를 다시 Commit하면 Merge까지 완료된 버전이 기록된다.

> pull을 쓰지 말자는 의견이 있다.    
[원본 글(영문), 21/7/13](https://felipec.wordpress.com/2021/07/13/why-is-git-pull-broken/) --
[번역본](https://ryanking13.github.io/2021/10/17/why-git-pull-is-broken.html)
>

<br>

### *Shared Repositories to Local*

프로젝트나 협업 등의 이유로 다른 사용자의 레포지토리를 내 로컬에 저장해야 할 때

1. 최초 저장시 :: `Clone`

    ```bash
    git clone {Repository Address}
    ```

    별도로 `git init`은 필요하지 않으며, git bash에 표기되어있는 경로에 레포지토리 내용이 전부 저장된다.
    
    기존 commit 되었던 내역과 remote 정보도 같이 복사되어 저장된다.

2. 변경사항이 있을시

    clone 작업 이후 다른 사용자가 작업한 내용을 내 로컬에 저장해야 할 때는 pull을 사용하는데, 이때 clone 당시 복사되었던 remote 정보를 사용해야 한다.

    ```bash
    git pull {Github remote name} {Branch Name}
    ```

    - 다른 사용자가 remote name을 ori로 두었고, branch name을 master로 두었다면, git pull ori master 라고 입력해야 한다.

<br>

### *Local to Shared Repositories*

내가 작업한 내용을 다른 사용자의 레포지토리로 보내야할 때는 내 레포지토리에 내보내는 것과 다른 방식이다.

우선 내 레포지토리가 아니면 읽기 권한 외에는 부여되지 않는다. 따라서 권한이 없는 상태에서 내보내기(push)를 사용하면 에러가 발생하게 되고, 이를 해결하기 위한 방법은 두가지가 있다.

1. 레포지토리 소유자에게 권한 요청

    github에 공동 작업자 설정을 통하여 권한(공동 작업자)을 부여하는 방법이 있다. 이 경우 내 레포지토리에 내보내기를 할때와 동일하게 push를 할 수 있다.

    > 소규모의 팀 프로젝트나 신뢰할 수 있는 사용자와의 협업등에서의 방식

2. fork

    github 우측 상단에 Fork라는 것이 있다. 이 fork를 사용하면 해당 레포지토리를 내 계정에 복제한다.
    
    이 복제된 레포지토리는 내가 생성한 레포지토리처럼 사용할 수 있다. 다만 내가 어떤 작업을 시행해도 원본(다른 사용자의 레포지토리)과는 별개의 레포지토리로 취급되어 원본의 내용이 바뀌거나 하지 않는다.

    그렇기에, 내가 작업한 내용을 다른 사용자의 레포지토리에 기여(Contribute)하기 위해서 github상 `Contribute` 버튼을 클릭하여 `Open pull request`를 해야한다.

    > 오픈 소스등 불특정 다수가 접근 할 수 있는 레포지토리에서의 방식

<br>

#### *Pull Request; PR*

`Pull request(PR)`는 요약하면 '내가 작업한 것을 가져가주세요' 라고 볼 수 있다.    

변경 권한이 없는 사용자가 레포지토리에 PR을 열면(Open), 소유주나 관리자가 이 요청에 작성되어 있는 내용들을 확인하며 pull하여 병합할지(Merged), 거부할지(Closed) 결정한다.

PR을 Open할 때 요청자는 자신의 요청에 대한 상세한 내용을 기재할 수 있고, 병합되었을 때 본인의 커밋 기록이 남기 때문에, 가능한 커밋 메시지와 어떠한 내용들이 변경이 있었는지를 잘 기록해야 한다.

> 레포지토리 오른쪽 하단에 보면 Contributors라고 있는데, 이 유저들은 PR이 수락된 유저들이다.