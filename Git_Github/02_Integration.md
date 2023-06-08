# Git, Github #2

## Integrating git and github(연동)

### Account Integration(계정 연동)

> git은 로컬에서 작업하는 것이기 때문에, 공유나 제어등을 위하여 github의 원격 저장소에 업로드를 해야한다.

깃허브를 가입해도, 로컬에 내 깃허브 계정의 정보는 없다. 따라서, git을 사용하여 원격 저장소에 접근하기 위해서는 git에 내 정보를 제공해야 한다.

``` bash
git config --global user.name "User Name"
git config --global user.email "User Email"
```

각각 User Name과 User Email에 github 가입시 작성했던 이름과 이메일을 작성하여 연동시킨다.

제대로 연동이 되었는지 확인하고 싶으면 아래의 명령어를 사용한다.

``` bash
git config user.name    #User Name
git config user.email   #User Email
```

<br>

### Repository Integration (내 레포지토리 연동)

작업 트리, 내가 사용할 로컬 폴더에 git bash를 열고 `git init` 명령어를 사용한다.

- git bash에서 로컬 주소를 잘 확인 할 것

- 성공적으로 시행되면 branch명이 주소 옆에 표시된다.

<br>

저장소에 내가 작업한 내용을 저장하기 위해서, 저장할 주소를 지정해주어야 한다.

``` bash
git remote add {name} {Repository Address}
```

- remote는 원격저장소를 의미한다고 생각하면 될 듯

- 보통 github에서 신규 레포지토리를 생성하면 Repository Address를 제공하고, 이 주소를 연동하면 작업 트리와 원격 저장소 레포지토리가 연동된다.

- {name}은 별칭으로, 긴 주소대신 사용할 이름을 지정한다. 보통 origin

<br>

저장소에 잘 연결되었는지 확인하고자 한다면

``` bash
git remote -v
```

<br>

#### Address를 잘못했을 때

Name을 잘못 지정했을때는, 재지정 후 삭제

``` bash
git remote rm {name}
# git remote remove {name}
```

<br>

Address를 잘못 지정한 경우에는 두가지가 있는데

1. 기존 연결 삭제 후 재지정 : name 삭제와 동일하게 삭제하고, 다시 지정

    - 단, 이 경우는 무조건 삭제를 먼저해야한다. 동일 이름으로 지정할 수 없다.

2. 변경

    ``` bash
    git remote set-url {name} {address}
    ```
    
    name에는 기존에 지정했던 이름을, address에는 변경하고자 하는 주소를 입력한다.


