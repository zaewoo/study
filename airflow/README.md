
Airflow 특징
파이썬으로 제작된 도구이며 이용자가 워크플로우 생성시에도 파이썬으로 구현해야 한다.
하나의 워크플로우는 DAG(Directed Acyclic Graph)이라 부르며, DAG 안에는 1개 이상의 Task가 존재한다.
Task간 선후행 연결이 가능하되 순환되지 않고 방향성을 가진다.
Cron 기반의 스케줄링, Task들이 시작되어야 하는 시간, 주기 등을 설정하는 데 쓰인다.
모니터링 및 실패 작업에 대한 재실행 기능이 간편하다.

WSL이란?
Windows Subsystem for Linux로 Windows에서 리눅스 실행환경을 지원하는 Windows의 확장 기능이다.
Windows에서 바로 리눅스 명령어를 실행할 수 있어서 Windows와 리눅스를 함께 사용하는 개발자들에게 편리하다.
WSL이 있기 전까지는 가상 머신(Virtual Machine, VM)을 많이 썼다. 
	컴퓨터 안에 구축된 가상 컴퓨터로 CPU, 메모리, 네트워크 인터페이스 및 스토리지까지 갖춘 온전한 컴퓨터 시스템으로 작동하는 가상 환경을 일컫는다.
	오버헤드(Overhead)는 어떤 처리를 하기 위해 들어가는 간접적인 처리 시간 및 메모리 등을 말하는데, 가상 머신에는 오버헤드 현상이 자주 발생하는 문제가 있다.
수업에서 반드시 WSL을 설치해야 하는가?
	Airflow는 Windows에 직접 설치가 불가능하다.
	Windows에서 리눅스 작업 환경을 만들기 위해서 WSL 설치가 필수다.
	여유가 된다면 가상화 VM 또는 Public Cloud의 컴퓨팅 서비스에서 Airflow 설치 가능하다.
WSL 설치: Windows Search - (Run as Administrator) Windows PowerShell - "wsl --install"
Ubuntu 설치 확인: "wsl -l -v", Version:2인지 확인해야 한다.
WSL 실행: Windows Search - WSL - +Ubuntu

간단한 리눅스 명령어들
ls: 현재 디렉토리의 파일 목록 출력 (숨겨진 파일 확인: "ls -al") 
cd(change directory): 디렉토리 변경 
	 이전 디렉토리로 이동하는 방법: "cd ..", 
	 특정 디렉토리로 이동하는 방법: "cd directory name", 
	 루트 디렉토리로 이동하는 방법: "cd /", 
	 홈 디렉토리로 이동하는 방법: "cd"
mkdir: 디렉토리 생성
	파일은 콘솔 창에 "ls -al"을 입력하면, "-"가 붙어 있고,
	디렉토리는 "-"가 붙어 있지 않다. 
	윈도우 WSL ㅇ명령어 창에서는 색깔로도 구분이 가능하다. 
rm: 파일 삭제 (디렉토리 포함: 옵션 -r, 강제: 옵션 -rf)
	디렉토리 미포함 삭제 시: "rm file1"
	디렉토리 포함 삭제 시: "rm -r dir1"
cp: 파일 복사 (디렉토리 포함: 옵션 r)
	디렉토리 미포함 복사 시: "cp file1 file2"
	디렉토리 포함 복사 시: "cp dir1 dir2"
mv: 파일 이동/이름 변경
	디렉토리 존재 시 파일 이동: mv file1 dir1
	디렉토리 부재 시 이름 변경: mv file1 file2 
touch: 새로운 파일 생성
tar: 파일/디렉토리를 압축 해제
	압축 시: tar cvf tarname objectname
	압축 해제 시: tar xvf objectname
pwd: 현재 디렉토리 경로 출력

도커란?
리눅스 내 가상화 관련 커널을 활용하여 어플리케이션을 독립적 환경에서 실행시키는 기술이다.
가상화 서버(VM) 대비 Guest OS가 없어 경량화된 가상화 서버로  볼 수 있다.
가상화 서버(VM)은 Host OS 위에 HyperVisor를 설치하고 나서야 독립된 가상 환경을 구축할 수 있는데, 매 환경에 Guest OS를 설치해야 하므로 CPU, 메모리 등을 불필요하게 할애해야 한다.
반면에 Host OS 위에 HyperVisor 대신 Docker를 설치하면 Guest OS를 설치하지 않아도 되므로 불필요한 CPU, 메모리 낭비를 줄일 수 있고, Host OS 위에 곧바로 Application을 실행시킬 수 있다.
우리는 이 각각의 Application을 Container, 즉 경량화된 가상화 서버라고 한다.

Docker 설치
Docker 실행 시: "sudo service docker start"

Airflow 설치
Airflow 설치 방법은 여러 가지가 존재하며 그  중 하나가 도커 설치이다.
Docker Compose를 이용하여 한번에 쉽게 설치 가능하다.
Docker Compose란?
	여러 개의 도커 컨테이너 설정을 한번에 관리하기 위한 도커 확장 기술이다.
	데이터베이스를 위한 컨테이너가  여러 개 있을 수 있고,
	웹 서버를 위한 컨테이너가 여러 개 있을 수 있다.
	에어플로우를 설치하기 위한 도커 컨테이너 세팅 내용이 들어 있다.

Airflow 접속
URL: localhost:8080
ID: airflow
PW: airflow
Airflow DAGs에 있는 각각의 목록이 DAG, 즉 워크플로우다.
실행: DAG를 실행시키려면 좌측 상단에 있는 토글 옵션을 클릭해서 Pause/Unpause를 설정할 수 있다. 
Details: 실행 이력을 확인할 수 있고, 그 좌측에서도 실행 이력을 확인할 수 있다. 
Auto-refresh: 우측 상단에 있고, 이는 정보를 자동으로 갱신하게 할 수 있다.
Graph: 해당 DAG를 구성하고 있는 Task을 보여주고, 그 연결 관계 및 상태를 알려준다.
각각의 Task는 상태를 갖고 있다.
Code: 이 DAG를 구성하고  있는 Python Code가 있다. GUI 환경에서 마우스 드래그 앤 드롭이 아니다. DAG를 만들 때는 Python Code가 필요하다.

개발 환경 플로우 이해
초기 환경에서는 컨테이너 여섯 개가 띄워져 있고, 3개의 디렉토리를 생성하여 컨테이너와 연결시킨다.
따라서 3개의 디렉토리에는 파일을 추가하면 컨테이너에서도 그 파일을 인식할 수 있다.
우리가 만든 DAG을 3개의 디렉토리 중 하나인 DAGs 디렉토리에 넣으면 에어플로우 컨테이너가 이 DAG을 인식하고 띄워주게 된다.
그러므로 우리가 만든 DAG을 DAGs 디렉토리에 배포하는 것이 개발 환경의 목적이다.
Python Interpreter 설치  (단, Python Interpreter 설치 시 Container와 동일한 버전을 설치해야 한다.)
Visual Studio Code 설치
Python Airflow Library 설치
IDE에서 DAG을 개발하고, Git push를 통해 Git Repository에 넣는다.
WSL에서 Git pull을 통해 Git Repository에 저장된 코드를 다운로드 받는다.
그리고 그 코드를 다시 컨테이너와 연결되어 있는 DAGs Directory에 옮겨준다.

명령어
Docker 실행: "sudo service docker start"
Airflow 실행: "sudo docker compose up"
도커에 띄워져 있는 컨테이너 목록 보기: "sudo docker ps"
도커에 띄워져 있는 컨테이너 들어가기: "sudo docker exec -it <container name or container id>" bash (! -it는 세션이 끊어지지 않도록 하는 명령어다.)
	도커에 띄워져 있는 컨테이너는 일종의 가상 환경이고, 이 가상 환경에 설치된 파이썬 인터프리터의 버전을 확인하기 위해서는 "python -V"를 입력한다. 
도커에 띄워져 있는 컨테이너에서 나가기: Ctrl+D

파이썬 가상 환경
라이브러리 버전 충돌 방지를 위해 설치/사용되는  파이썬 인터프리터  환경을 격리시키는 기술이다.
파이썬은 라이브러리 설치 시점에 따라서도 설치되는 버전이 상이한 경우가 많다.
X: Open Editor > Terminal > cmd > "python -m venv v <virtual environment name> 
O: Open Editor > F1 > Create Virtual Environment > Venv > Python: Select Interpreter > Docker에 띄어져 있는 컨테이너 환경과 동일한 버전의 파이썬 인터프리터를 설치한다. > 다시 한번 F1 을 눌러서 venv python interpreter.. > cmd 상 확인

Github Repository
Git vs Github
Git: 오픈 소스 분산형 버전 관리 시스템 또는 프로그램
Github: Git을 기반으로 소스를 공유할 수 있도록 만들어진 웹 서비스
버전 관리
	중앙형(SVN): 여러 개발자가 한 레포지토리에 모두 커밋을 하여 배포하는 형태다. 중앙형은 충돌 및 해결을 중앙 레포지토리에서 해야 한다.
	분산형(Git): 여러 개발자가 각 로컬 환경경에 커밋을 하고, 배포하기 위해 공통의 레포지토리에 푸시하여 배포하는 형태다. 분산형은 충돌 및 해결을 로컬에서 해야 한다. 그럼 왜 필요한가? 공유의 목적이다.
Git Push & Pull
	Local Computer의 Local Repo에 지속적으로 코드를 업데이트하고 커밋을 한다.
	그리고 어느 정도 되면 Remote Repo에 Local Repo의 코드를 Push한다.
	Remote Repo에 있는 코드는 WSL의 Local Repo로 Pull하고, 컨테이너에 옮긴다.
Git 설치 - Local Repo 및 Github Repository - Remote Repo 만들기

Create Local Repository
cmd -> dir -> cd Desktop -> cd project -> git init (로컬 레포지토리 생성)
git status (변경 사항을 인식한 현황을 나타낸다.) 
불필요한 정보를 변경 사항으로 인식할 때, 이를 방지하기 위해 텍스트 파일을 생성하여 ".gitignore"로 파일명을 변경한다.
변경 사항으로 인식시키기  위해 명령 프롬프트에 "git add <filename>" / "git add ." (모든 수정 내용을 반영) 을 입력한다.
변경 사항을 로컬 레포에 배포하기 위해 "git commit -m "내용"을 입력한다.
변경 이력을 확인할 때는 "git log"를 입력한다. 

Create Remote Repository
github.com 

Branch
Local Repository에 두 개 이상의 Branch를 둘 수 있는데, 일반적으로 한 개의 Branch를 Develop Branch, 다른 한 개의 Branch를 Operate Branch로 둔다.
그리고 변경 사항은 모두 Local Repository의 Develop Branch에 Commit을 하여 정보를 반영한다.
다음으로 이 변경 사항을 테스트하기 위해 Remote Repository의 Develop Branch에 Push하고, Remote Repository에서 테스트를 한다.
이상이 없을 시 Local Repository의 Develop Branch 정보를 모두 Operate Branch에 Merge하고,  Remote Repository의 Operate Branch에 배포한다.

배포
현재 브랜치 확인: "git branch"
원격 레포 연결: "git remote add origin https://github.com/zaewoo/airflow.git"
원격 레포 확인: "git remote"
원격 레포로 배포: "git push -u origin master"

WSL에서 Remote Repository에 있는 Code를 Pull 

위의 방법 외에 다른 방법으로는 복제가 있다.
Remote Repo에 있는 내용물을 그대로 Local Repo, 그 중에서도 WSL의 Local Repo에 그대로 Clone을 가져온다. git 의 clone
git clone https://github.com/zaewoo/airflow.git







