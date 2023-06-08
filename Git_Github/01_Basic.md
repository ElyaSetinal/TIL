# Git, Github

## What is different git and github?

### *Git*

- 분산 버전 관리 시스템(DVCS; Distribute Version Control System)
- 로컬에서 버전 관리
- 개발 및 소스 코드 관리에 사용

본인의 코드와 수정내역을 기록하고 관리하도록 돕는 버전 관리 **프로그램**    
로컬에서 프로젝트의 기록을 스스로 관리할 수 있도록 함    
로컬 저장소에서 사용하기 때문에, 실시간 공유 불가능    
Local Git, 로컬에서 사용    

### *Github*

- Git Repository를 위한 웹 기반 호스팅
- 클라우드 서버를 이용하여 로컬에서 버전 관리한 소스코드를 업로드하여 공유
- 분산 버전 제어, 엑세스 제어, 코드 관리, 버그 추적 등 여러가지 기능 및 작업 관리를 제공

git 저장소를 관리하는 클라우드 기반 호스팅 **서비스**    
다른 사람과 소스 코드 공유가 가능하며, git의 기본 기능을 확장하여 제공    
Remote git, 원격 저장소

### *Summary*

git : 로컬에서 작업하는 버전 관리 프로그램    
github : git을 지원하는 원격 저장소 서비스

<br>

## How to use git

### *Pre: CLI, Linux*

리눅스 커널(linux kernel)을 위한 도구로 개발된 git이다 보니, CLI 기반

> CLI(Command Line Interface) : 명령어를 사용하고, 텍스트 터미널을 통하여 User와 PC가 상호 작용하는 방식. MS-DOS, Linux 등이 있다.

리눅스 명령어 모음
|Command|Action|Full Name|
|:---:|:---:|:---:|
|ls|현재 디렉토리의 파일 및 디렉터리 목록|list|
|touch|현재 디렉토리에 0 byte 파일 생성<br>파일의 날짜와 시간 수정|touch|
|rm|삭제, rm {file or directory name} 으로 사용<br>하위 디렉토리 존재시 -r 추가|remove|
|mkdir|현재 디렉토리 내부에 하위 디렉토리를 생성|make directory|
|cd|디렉토리 이동<br> cd .. 을 사용하여 상위 디렉토리로 이동|change directory|


### *git command*

|Command|Action|
|:---:|:---:|
|git init|깃 초기화, 로컬 폴더와 깃의 브랜치(Branch) 연결 <br>로컬에 .git 폴더를 생성하여 git 정보를 추가|
|git status|깃 상태 표시. 브랜치, 스테이징(Staging) 파일, non-commit 파일 등<br>마지막 commit을 기준으로 상태 비교하여 표기|
|git add {file name}|작업 트리에서 수정한 파일을 스테이징 영역에 추가<br>file name에 `.` 을 사용하면 모든 파일이 추가됨|
|git commit -m "message"|버전 생성(commit), 스테이지에서 저장소로 저장<br>메세지를 통하여 수정 내역 혹은 버전 정보를 추가|
|git log|Commit 작업 내역 표시. 커밋 해시, 메시지, 작성자 등|

> Staging Area?    
Commit을 하기 위해 $git add 명령어로 추가한 파일들이 모여있는 공간    
작업 트리가 결재 서류고, 커밋이 결재가 완료 된 것이라면, 스테이징 공간은 결재를 위해 대기하는 서류함 같은 개념

<br>

#### *Addition.* (수업 기록 및 개인 의견)

Commit 시기 : '버전'이라 불릴 수 있는 시기? 중요한 변경 이후나 신규 생성 등 기존과 다르다는 느낌일 때..

Commit Message 기록 요령 : 작업한 내용을 잘 담는 문장.

- 나중에 돌아봤을 때나 타인이 봤을 때, 한눈에 알아볼 수 있는게 최상이지 않을까