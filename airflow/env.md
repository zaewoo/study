작업 환경 설정
작업 환경으로 할 폴더를 생성한다.
다음으로 Visual Studio Code를 실행하고 작업 환경으로 할 폴더를 선택한다.
작업 시 모듈 간의 충돌을 방지하기 위해 해당 작업을 위한 가상 환경을 생성한다.
도커에 설치된 파이썬의 버전과 작업 환경에 설치된 파이썬의 버전이 일치해야 하므로 도커에 설치된 파이썬 버전을 확인한다.
대부분 최신 버전이 설치되므로 최신 버전으로 설치해야 하고, 다음으로는 가상 환경을 설정하기 위한 명령어다.
명령 프롬프트를 실행한 다음, "python -m venv ./venv"를 입력한다.
대개 글로벌 환경에 설치된 파이썬의 버전이 설치되는데, 글로벌 환경에 설치된 파이썬의 버전과 도커에 설치된 파이썬 버전이 일치하지 않을 때는 아래의 과정으로 설치한다.
[Help] - [Show All Commands] - [Python: Select Interpreter] - [버전 선택]
작업은 (1)로컬 컴퓨터에서 이용할 수 있는 로컬 리포지토리, (2)도커 컨테이너에서 이용할 수 있는 로컬 리포지토리, 그리고 (3) (1)과 (2)를 연결하여 주는 원격 리포지토리로 세 개의 리포지토리를 사용한다.
처음으로는 GitHub에 접속하여 작업 환경으로 할 (3)원격 리포지토리를 생성한다.
다음으로는 (1)로컬 컴퓨터에서 이용할 수 있는 로컬 리포지토리를 생성해야 하는데, 이는 명령 프롬프트 창에서 가상 환경을 설치한 폴더로 이동한다. 그리고 "git init"을 입력한다.
"Initialized empty Git repository in C:/Users/CI/Desktop/project/practice/.git/"와 같은 내용이 출력된다.
Git 명령어
새로운 리포지토리 생성: $ git init : .git 하위 디렉토리 생성한다.
변경 사항 추가: $ git add <파일명> / $ git add <.> : 커밋에 단일 혹은 전체 변경 사항을 포함한다.
변경 사항 확정: $ git commit -m "커밋 메시지" : 커밋 생성, 실제 변경 사항을 확정한다.
현재 상태 확인: $ git status : 현재 리포지토리 상태를 확인한다.
클라우드 주소 등록: $ git remote add origin <URL> : 새로운 원격 리포지토리 주소를 알려준다.
변경 사항 발행: $ git push -u origin master : 원격 리포지토리에 변경 사항을 반영한다.
마지막으로 (2)도커 컨테이너에서 이용할 수 있는 로컬 리포지토리를 생성한다. 이는 원격 리포지토리의 내용을 그대로 복제하여 로컬 리포지토리로 가져온다.
방법은 원하는 디렉토리로 이동한 다음 아래와 같은 명령어를 입력한다.
$ git clone <URL>
계정 정보 및 토큰을 입력하면 정상적으로 원격 리포지토리를 복제할 수 있다.
토큰은 [Settings] - [Developer settings] - [Personal access tokens] - [Tokens (classic)] 에서 발급 받을 수 있다.
마지막으로 에어플로우를 작업 환경에 설치하기 위해 명령 프롬프트에 아래의 명령어를 입력한다.
pip install "apache-airflow[celery]==2.9.3" --constraint "https://raw.githubusercontent.com/apache/airflow/constraints-2.9.3/constraints-3.8.txt"

작업
작업 시 작업 환경으로 할 폴더에 추가로 새로운 폴더를 생성하여 그 폴더 내에 필요한 워크 플로우를 작성해서 저장한다.
다음으로 도커는 기본 설정 상 작업 폴더를 인식할 수 없으므로 작업 폴더를 인식할 수 있게 경로를 설정해주어야 한다.
"Docker-Compose.yaml" 파일의 편집 기능을 이용해 "volumes" 항목을 찾는다.
"${AIRFLOW_PROJ_DIR:-.}/dags:/opt/airflow/dags" 는 ":"를 기준으로 해석하면 되는데, ":"을 기준으로 좌측의 경로는 리눅스의 볼륨이고, ":"을 기준으로 우측의 경로는 도커 컨테이너의 볼륨이다. 그리고 ":"를 기준으로 리눅스와 도커 컨테이너가 연결되어 있다.
추가적으로 "${AIRFLOW_PROJ_DIR:-.}/dags:/opt/airflow/dags" 에서 "${AIRFLOW_PROJ_DIR:-.}"는 쉘 스크립트의 문법으로 "AIRFLOW_PRJ_DIR"이 존재하면 그것을 출력하고, "AIRFLOW_PRJ_DIR"이 존재하지 않으면 "."을 출력한다는 의미다.
다시 돌아가 기본 설정은 홈 디렉토리의 "./dags" 폴더를 바라보고 있고, 우리의 작업 환경은 홈 디렉토리의 "./project/dags" 이므로 "Docker-Compose.yaml"의 "volumes"에서 경로를 수정해 도커 컨테이너가 작업 환경의 폴더를 바라보게 한다.
경로를 수정한 다음에는 도커를 내렸다가 다시 올려주어야 수정 내용이 반영된다. 다음의 명령어를 입력하면 된다.
$ sudo docker compose down
$ sudo docker compose up
데이터베이스 연결 시 "password authentication failed for user"와 같은 오류가 발생하면 도커 컨테이너의 볼륨을 초기화 후 재실행한다.
$ sudo docker compose down -v

