#### Airflow
데이터 추출, 가공, 저장, 그리고 분석 등 파이프라인을 구성하고 관리할 수 있는 도구다.\
파이썬을 이용해 워크플로우를 만들고 관리할 수 있는 오픈소스 기반 워크플로우 관리 도구다.\
파이썬으로 제작된 도구이며 이용자가 워크플로우 생성 시에도 파이썬으로 구현해야 한다.\
하나의 워크플로우는 댁(Directed Acyclic Graph, DAG)이라 부르며, 댁 안에는 한 개 이상의 태스크가 존재한다.\
태스크 간 선후행 연결이 가능하되 순환되지 않고 방향성을 가진다.\
크론론 기반의 스케줄링, 태스크가 시작되어야 하는 시간, 그리고 주기 등을 설정하는 데 쓰인다.\
모니터링 및 실패 작업에 대한 재실행 기능이 간편하다.

#### WSL
Windows Subsystem for Linux의 약자로 윈도우에서 리눅스 실행 환경을 지원하는 윈도우의 확장 기능이다.\
윈도우에서 리눅스 명령어를 실행할 수 있어 윈도우와 리눅스를 함께 사용하는 개발자들에게 편리하다.\
이 확장 기능이 있기 전까지는 가상 머신(Virtual Machine, VM)을 많이 사용했다.\
가상 머신은 컴퓨터 안에 구축된 가상 컴퓨터로 CPU, 메모리, 네트워크 인터페이스 및 스토리지까지 갖춘 온전한 컴퓨터 시스템으로 작동하는 가상 환경을 일컫는다.\
오버헤드는 어떤 처리를 하기 위해 들어가는 간접적인 처리 시간 및 메모리 등을 말하는데, 가상 머신에는 오버헤드 현상이 자주 발생하는 문제가 있다.\
그렇다면, 에어플로우를 사용하기 위해 이 확장 기능을 반드시 사용해야 하는가? 에어플로우는 윈도우에서 직접 설치할 수 없다.\
그러므로 윈도우에서 리눅스 작업 환경을 만들기 위해 확장 기능을 반드시 설치해야 한다.\
추가적으로 가상 머신 또는 퍼블릭 클라우드의 컴퓨팅 서비스에서도 에어플로우를 설치할 수 있다.

설치: Windows search - (Run as Administrator) Windows PowerShell - 'wsl --install'\
확인: Windows search - (Run as Administrator) Windows PowerShell - 'wsl -l -v'\
실행: Windows search - WSL - +Ubuntu\
참고: https://learn.microsoft.com/ko-kr/windows/wsl/install

#### Linux Command
- pwd: 현재 디렉토리 경로 출력
- ls: 현재 디렉토리의 파일 목록 출력
- ls -al: 현재 디렉토리의 전체 파일 목록 출력
- cd: 디렉토리 변경
  - cd ..: 이전 디렉토리로 이동
  - cd directory name: 특정 디렉토리로 이동
  - cd /: 루트 디렉토리로 이동
  - cd: 홈 디렉토리로 이동
- mkdir: 디렉토리 생성
  - 파일 및 디렉토리를 구분하는 방법은 콘솔 창에 'ls -al'를 입력할 시,   파일은 가장 앞에 '-'가 표기되어 있고, 디렉토리는 가장 앞에 'd'가 표기되어 있다.
  - 추가적으로 명령어 창에서는 색깔로도 구분할 수 있다.
- rm: 파일 삭제
  - rm filename: 디렉토리 제외 삭제
  - rm -r directory name: 디렉토리 포함 삭제
- cp: 파일 복사
  - cp file1 file2: 파일 복사
  - cp -r dir1 dir2: 디렉토리 포함 복사
- mv: 파일 이동/변경
  - mv filename directory name: 디렉토리 존재 시 파일 이동
  - mv file1 file2: 디렉토리 부재 시 이름 변경
- touch: 새로운 파일 생성
- tar: 파일/디렉토리 압축 및 압축 해제
  - tar cvf tarname objectname: 파일/디렉토리 압축
  - tar xvf objectname: 파일/디렉토리 압축 해제
- cat: 파일 읽기
- sudo service docker start: 도커 데몬 실행
- sudo docker compose up: 도커에 정의되어 있는 모든 서비스 컨테이너 생성 및 실행
- sudo docker ps: 도커에 정의되어 있는 모든 서비스 컨테이너 목록 보기
- sudo docker exec -it container name or container id bash: 도커에 정의되어 있는 서비스 컨테이너 접근 (-it는 세션이 끊어지지 않도록 하는 명령어다.)
- python -V: 사용 파이썬 버전 확인

#### Introduction to Docker
리눅스 내 가상화 관련 커널을 활용하여 어플리케이션을 독립 환경에서 실행시키는 기술이다.\
이는 가상화 서버(VM)와 다르게 Guest OS가 없어 경량화된 가상화 서버로 볼 수 있다.\
가상화 서버(VM)은 Host OS 위에 HyperVisor를 설치하고 나서야 독립된 가상 환경을 구축할 수 있다.\
그리고 이는 모든 가상화 서버에 Guest OS를 설치해야 하므로 CPU, 메모리 등을 불필요하게 할애해야 한다.\
반면에 Host OS 위에 HyperVisor 대신 Docker를 설치하면, Guest OS를 설치하지 않아도 되므로 불필요한 CPU, 메모리 낭비를 줄일 수 있다.\
또한, Host OS 위에 곧바로 Application을 실행시킬 수 있다.\
우리는 이 각각의 Application을 Container, 즉 경량화된 가상화 서버라고 한다.

#### Introduction to Docker Compose
여러 개의 도커 컨테이너 설정을 한번에 관리하기 위한 도커 확장 기술이다.\
데이터베이스를 위한 컨테이너가 여러 개 있을 수 있고, 웹 서버를 위한 컨테이너가 여러 개 있을 수 있다.\
에어플로우를 설치하기 위한 도커 컨테이너 세팅 내용이 들어 있다.

#### Installation of Docker
참고: https://docs.docker.com/engine/install/ubuntu/

#### Installation of Airflow
참고: https://airflow.apache.org/docs/apache-airflow/stable/howto/docker-compose/index.html

#### Access the Airflow UI
주소: localhost:8080\
아이디: airflow\
패스워드: airflow

Airflow DAGs에 있는 각각의 목록이 댁, 즉 워크플로우다.\
Pause/Unpause: 댁을 실행시키려면 좌측 상단에 있는 토글 옵션을 클릭해서 상태를 설정할 수 있다.\
Details: 실행 이력을 확인할 수 있고, 그 좌측에서도 실행 이력을 확인할 수 있다.\
Auto-refresh: 우측 상단에 있고, 이는 정보를 자동으로 갱신하게 할 수 있다.\
Graph: 해당 댁을 구성하고 있는 태스크를 보여주고, 그 연결 관계 및 상태를 알려준다.\
Code: 이 댁을 구성하고 있는 파이썬 코드가 있다. GUI 환경에서 마우스 드래그 앤 드롭이 아니다. 댁을 만들 때는 파이썬 코드가 필요하다. 

#### Development Environment Flow
초기 환경에서는 컨테이너 여섯 개가 띄워져 있고, 3개의 디렉토리(Dags, Logs, Plugins)를 생성하여 컨테이너와 연결시킨다.\
따라서 3개의 디렉토리에는 파일을 추가하면 컨테이너에서도 그 파일을 인식할 수 있다.\
우리가 만든 댁을 세 개의 디렉토리 중 하나인 DAGs Directory에 넣으면, 에어플로우 컨테이너가 이 댁을 인식하고 띄워주게 된다.\
그러므로 우리가 만든 댁을 DAGs Directory에 배포하는 것이 개발 환경의 목적이다.

Python Interpreter (단, Python Interpreter 설치 시 Container와 동일한 버전을 설치해야 한다.)\
Visual Studio Code\
Python Airflow Library

#### Python Virtual Environment
라이브러리 버전 충돌 방지를 위해 설치/사용되는  파이썬 인터프리터  환경을 격리시키는 기술이다.\
파이썬은 라이브러리 설치 시점에 따라서도 설치되는 버전이 상이한 경우가 많다.\
O: Open Editor - F1 - Create Virtual Environment - Venv - Python: Select Interpreter - Docker에 띄어져 있는 컨테이너 환경과 동일한 버전의 파이썬 인터프리터를 설치한다. - 다시 한번 F1 을 눌러서 venv python interpreter..

#### Git vs. Github
Git: 오픈소스 분산형 버전 관리 시스템 또는 프로그램\
Github: Git을 기반으로 소스를 공유할 수 있도록 만들어진 웹 서비스

#### 버전 관리
중앙형(SVN): 여러 개발자가 한 레포지토리에 모두 커밋을 하여 배포하는 형태다. 중앙형은 충돌 및 해결을 중앙 레포지토리에서 해야 한다.\
분산형(Git): 여러 개발자가 각 로컬 환경에 커밋을 하고, 배포하기 위해 공통의 레포지토리에 푸시하여 배포하는 형태다. 분산형은 충돌 및 해결을 로컬에서 해야 한다.

#### 프로세스
로컬 컴퓨터의 로컬 레포지토리에 지속적으로 코드를 업데이트하고 커밋을 한다.\
다음으로 업데이트된 코드를 원격 레포지토리에 반영하기 위해 푸시를 한다.\
업데이트된 코드를 리눅스 개발 환경의 로컬 레포지토리에 불러오기 위해 풀하고, 컨테이너로 옮긴다.

#### Installation of Git
참고: https://git-scm.com/book/ko/v2/%EC%8B%9C%EC%9E%91%ED%95%98%EA%B8%B0-Git-%EC%84%A4%EC%B9%98

#### Remote Repository
참고: https://github.com/

#### Local Repository
참고: https://github.com/ - …or create a new repository on the command line

- git init: 로컬 레포지토리 생성
- git status: 로컬 환경에서 변경된 사항 확인
- git add 'file name' / git add .: 로컬 환경에서 변경된 사항 반영
- git commit -m '내용': 로컬 환경에서 개발된 코드를 로컬 레포지토리에 배포
- git log: 로컬 레포지토리에 배포된 이력 확인
- git remote add origin https://github.com/zaewoo/airflow.git: 로컬 레포지토리와 원격 레포지토리를 연결
- git clone https://github.com/zaewoo/airflow.git: 로컬 레포지토리와 원격 레포지토리를 연결

#### Branch
로컬 레포지토리에 두 개 이상의 브랜치를 둘 수 있는데, 일반적으로 한 개의 브랜치를 개발 용 브랜치, 다른 한 개의 브랜치를 운영 용 브랜치로 둔다.\
초기 변경 사항은 모두 로컬 레포지토리의 개발 용 브랜치에 커밋을 하여 변경 사항을 반영한다.\
다음으로 이 변경 사항을 테스트하기 위해 원격 레포지토리의 개발 용 브랜치에 푸시하고, 원격 레포지토리에서 이를 테스트한다.\
이상이 없을 시 로컬 레포지토리의 개발 용 브랜치 정보를 모두 운영 용 브랜치에 병합하고, 원격 레포지토리의 운영 용 브랜치에 배포한다. 
