## Introduction to Airflow
파이썬으로 제작된 도구이며, 이용자가 워크플로우 생성 시에도 파이썬으로 구현해야 한다.\
하나의 워크플로우는 댁(DAG, Directed Acyclic Graph)이라 부르며, 댁 안에는 한 개 이상의 태스크가 존재한다.\
태스크 간 선후행 연결이 가능하되 순환되지 않고 방향성을 가진다.\
크론 기반의 스케줄링, 태스크가 시작되어야 하는 시간, 그리고 주기 등을 설정하는 데 쓰인다.\
모니터링 및 실패 작업에 대한 재실행 기능이 간편하다.

## Introduction to WSL
Windows Subsystem for Linux로 윈도우에서 리눅스 실행 환경을 지원하는 윈도우의 확장 기능이다.\
윈도우에서 리눅스 명령어를 실행할 수 있어 윈도우와 리눅스를 함께 사용하는 개발자들에게 편리하다.\
이 확장 기능이 있기 전까지는 가상 머신(VM, Virtual Machine)을 많이 사용했다.\
가상 머신은 컴퓨터 안에 구축된 가상 컴퓨터로 CPU, 메모리, 네트워크 인터페이스 및 스토리지까지 갖춘 온전한 컴퓨터 시스템으로 작동하는 가상 환경을 일컫는다.\
오버헤드는 어떤 처리를 하기 위해 들어가는 간접적인 처리 시간 및 메모리 등을 말하는데, 가상 머신에는 오버헤드 현상이 자주 발생하는 문제가 있다.\
그렇다면, 에어플로우를 사용하기 위해 이 확장 기능을 반드시 사용해야 하는가?\
에어플로우는 윈도우에서 직접 설치할 수 없다. 그러므로 리눅스 작업 환경을 만들기 위해 확장 기능 설치가 필수다.\
추가적으로 가상 머신 또는 퍼블릭 클라우드의 컴퓨팅 서비스에서도 에어플로우 설치가 가능하다.\

설치: Windows search - (Run as Administrator) Windows PowerShell - 'wsl --install\
확인: Windows search - (Run as Administrator) Windows PowerShell - 'wsl -l -v'\
실행: Windows search - WSL - +Ubuntu

## Linux Command
- ls: 현재 디렉토리의 파일 목록 출력
- ls -al: 현재 디렉토리의 전체 파일 목록 출력
- cd: 디렉토리 변경
- cd ..: 이전 디렉토리로 이동
- cd directory name: 특정 디렉토리로 이동
- cd /: 루트 디렉토리로 이동
- cd: 홈 디렉토리로 이동
- mkdir: 디렉토리 생성
- rm: 파일 삭제
- rm filename: 디렉토리 제외 삭제
- rm -r directory name: 디렉토리 포함 삭제
- cp: 파일 복사
- cp file1 file2: 디렉토리 제외 복사
- cp dir1 dir2: 디렉토리 포함 복사
- mv: 파일 이동/변경
- mv filename directory name: 디렉토리 존재 시 파일 이동
- mv file1 file2: 디렉토리 부재 시 이름 변경
- touch: 새로운 파일 생성
- tar: 파일/디렉토리 압축 및 압축 해제
- tar cvf tarname objectname: 파일/디렉토리 압축
- tar xvf objectname: 파일/디렉토리 압축 해제
- pwd: 현재 디렉토리 경로 출력

## Introduction to Docker
리눅스 내 가상화 관련 커널을 활용하여 어플리케이션을 독립적 환경에서 실행시키는 기술이다.\
가상화 서버(VM) 대비 Guest OS가 없어 경량화된 가상화 서버로 볼 수 있다.\
가상화 서버(VM)은 Host OS 위에 HyperVisor를 설치하고 나서야 독립된 가상 환경을 구축할 수 있는데, 매 환경에 Guest OS를 설치해야 하므로 CPU, 메모리 등을 불필요하게 할애해야 한다.\
반면에 Host OS 위에 HyperVisor 대신 Docker를 설치하면, Guest OS를 설치하지 않아도 되므로 불필요한 CPU, 메모리 낭비를 줄일 수 있고, Host OS 위에 곧바로 Application을 실행시킬 수 있다.\
우리는 이 각각의 Application을 Container, 즉 경량화된 가상화 서버라고 한다.
