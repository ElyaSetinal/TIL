## Git, Github #3 :: gitignore, Commit, Branch

### *pre :: .gitignore*

개발 환경과 관련된 파일이나, 프로젝트에 필요하나 공유하면 안되는 것들이 폴더에 포함된 경우가 있다. framework key나, 개인정보가 포함된 파일 등..

commit을 안함으로써 공유를 하지 않을 수 있지만, 그 경우 파일을 하나하나 add 해줘야하는 불편함이 있는데 이를 편하게 하는 방법이 `.gitignore` 파일을 루트 디렉토리에 추가하면 된다.

[gitignore 생성 사이트](https://www.toptal.com/developers/gitignore/) - 사이트 생성물을 Base로 잡고, 본인 프로젝트에 맞게 추가

<br>

### *Commit*

우선, 작업 트리에서 버전 관리가 가능한(생성, 변경, 삭제된 파일)을 확인한다.

``` bash
git status
```

status 명령어로 확인된 파일들 중 버전 관리할 파일을 스테이징 영역에 추가(add)한다.

``` bash
git add {file1} {file2} ...
```

- file 이름 대신, `.` 을 넣으면 스테이징 가능한 모든 파일을 추가한다.

내가 원하는 파일이 제대로 스테이징 영역에 입력되었는지 확인하기 위해, 다시 한번 status 명령어를 사용하여 확인한다.

``` bash
git status
```

- 잘못된 파일이 커밋되었을 때

    ``` bash
    git restore --stated {file}
    ```

문제점이 없으면, commit을 통하여 버전 관리 명령을 시행한다.

``` bash
git commit -m "Message"
```

이 단계까지, 로컬에서의 버전 관리를 위한 작업이 완료되었다.

- 마지막(가장 최근) 커밋을 변경하고자 할 때
    
    ```bash
    git commit --amend
    ```

    파일 변경은 `add`를 통하여 변경할 파일을 추가하고 사용하면 되는데, 메시지까지 변경하고자 한다면 `-m "Message"`, 메시지는 유지하고 싶다면 `--no-edit`을 사용한다.

    만약 메시지만 변경하고자 한다면 add 없이 `-m "Message"`를 사용한다.

    **주의할 점**은, 이 명령어는 마지막 커밋에 대해 단순 변경이 아니라, 완전히 새로운 커밋으로 *대체*된다는 점이다. (이는 커밋 해쉬를 통해 확인 할 수 있다.)    
    따라서, 원격 레포지토리(Github)에 **Push한 이후**에는 사용하지 않아야 한다.
    
    > 원고를 작성(Commit)했을 때는 비교적 수정이 용이하지만, 출판사에 보내서 출판(Push)을 한 경우는 수정이 매우 어렵다.


<br>

#### *git status로 나오는 메시지의 의미*

> *Changes not staged for commit*    
이전 commit(=Head) 비교하여 추가, 변경, 삭제되었으나 스테이징 영역에 들어있지 않은 파일들을 나타낸다 

> *Untracked files*    
로컬 디렉토리에는 존재하나, 단 한번도 commit된 적 없는, 버전관리가 안된 파일을 의미한다.

> *Changes to be committed*    
스테이징 영역에 있는, 커밋 대기중인 파일을 의미한다.

> *nothing to commit, working tree clean*    
Head와 비교하여 추가, 변경, 삭제 등의 작업이 없음을 의미한다.

<br>

### *Branch, 브랜치*

나뭇가지라는 의미로, 독립된 작업을 만들고 관리하는데 용이하다.

Main(Master)의 버전은 유지한채, 다른 기능을 개발하고 관리하거나, 테스트, 수정 등의 작업을 시행하고자 할 때, 다른 브랜치를 생성하여 작업하고, 이를 병합하는 방식을 사용한다.

![Git Flow](https://nvie.com/img/git-model@2x.png)
Branch에 대한 개념을 가장 잘 설명한 그림, git flow(github에서 제안하는 브랜치 전략)

- Main(Master) Branch는 최종 버전, 실제 라이브 서버에 적용중인 브랜치

> 대학원 연구실이나 기업부설연구소 등 연구를 주로 하는 곳에 연구노트라는 것이 있는데, 이 연구노트는 지식보호 및 위변조방지 등의 이유로 반드시 볼펜으로 적어야 한다.    
연구원마다 차이는 있지만, 개인용과 공개용을 나누어 작성하는 경우에 개인용에는 메모나 아이디어, 계산등 정갈하지는 않아도 개발 과정(Time)중의 여러 시도(Test)와 수정사항(Hotfixes)들이 담기고(= Main외 Branch), 공개용에는 마구잡이로 작성된 개인 연구노트의 내용을 정리하여 작성(Main Branch)하고는 한다.

<br>

`git init`을 통하여 git과 local을 연동하면 git 설정 상 default branch가 자동으로 연동된다.

다른 브랜치를 생성할 때

``` bash
git branch Branch_name
```

다른 브랜치로 이동할 때

``` bash
git switch(or checkout) Branch_name
```

작업이 끝난 브랜치를 삭제하고자 할 때

``` bash
git branch -d Branch_name
```