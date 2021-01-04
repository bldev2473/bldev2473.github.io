---
title: "[Docker] Mac OS에서 Docker를 통한 Oracle 11g 설치 및 Oracle SQL Developer 연결"
date: 2020-12-24 00:10:00 -0000
categories: [Mac, Docker, Oracle]
---

현재 Oracle에서는 Oracle 데이터베이스를 Mac OS 운영체제에 직접 설치하여 사용할 수 있는 방법을 지원하지 않습니다.
따라서 가상 머신이나 컨테이너 기반 Docker를 사용하는 방법을 사용하면 됩니다.

보다 빠르고 간편한 방법인 Docker를 사용하여
Oracle 데이터베이스 서비스를 설치하고 SQL 쿼리 작성 및 실행을 위한 클라이언트인 Oracle SQL Developer와 연결해보겠습니다.

## 1. Docker 설치 후 Docker CLI에 접속

## 2. Docker 이미지 검색 및 다운로드

Docker 이미지를 검색합니다.
```
docker search oracle-xe-11g
```

```
NAME                                DESCRIPTION                                     STARS     OFFICIAL   AUTOMATED
oracleinanutshell/oracle-xe-11g                                                     131                  
wnameless/oracle-xe-11g-r2          Oracle Express Edition 11g Release 2 on Ubun…   50                   
orangehrm/oracle-xe-11g              docker container with Oracle Express Editio…   14                   [OK]
christophesurmont/oracle-xe-11g     Clone of the wnameless/oracle-xe-11g.           6                    
ukhomeofficedigital/oracle-xe-11g   Oracle Database Express Edition 11g Container   4                    [OK]
thebookpeople/oracle-xe-11g                                                         3                    
jaspeen/oracle-xe-11g               Fork from sath89/docker-oracle-xe-11g - smal…   3                    [OK]
```

wnameless/oracle-xe-11g-r2 이미지를 다운로드해보겠습니다.

Oracle Express Edition 11g Release 2 on Ubuntu 18.04 LTS 이미지입니다.

```
docker pull wnameless/oracle-xe-11g-r2
```

```
Using default tag: latest
latest: Pulling from wnameless/oracle-xe-11g-r2
5667fdb72017: Pull complete 
d83811f270d5: Pull complete 
ee671aafb583: Pull complete 
7fc152dfb3a6: Pull complete 
51896e240a72: Pull complete 
64e16b57ee0a: Pull complete 
Digest: sha256:e8cfa3733a2c11b415fb94a9632424025d69165fb4903a22206f6073be30eeb9
Status: Downloaded newer image for wnameless/oracle-xe-11g-r2:latest
docker.io/wnameless/oracle-xe-11g-r2:latest
```

다운로드한 이미지를 확인해봅니다.
```
docker images
```

```
REPOSITORY                   TAG       IMAGE ID       CREATED         SIZE
wnameless/oracle-xe-11g-r2   latest    0d19fd2e072e   15 months ago   2.1GB
```

Docker Hub에서 실행에 대한 설명을 볼 수 있습니다.  
[Docker Hub](https://hub.docker.com/r/wnameless/oracle-xe-11g-r2)

GitHub Repository 주소도 공유되어 있습니다.  
[GitHub - wnameless/docker-oracle-xe-11g: Dockerfile of Oracle Database Express Edition 11g Release 2](https://github.com/wnameless/docker-oracle-xe-11g)

## 3. 컨테이너 실행
다운로드 한 이미지를 사용하여 컨테이너를 실행하기 위해 docker run 명령어를 사용합니다.

1521 포트로 컨테이너를 실행합니다. 이때 --name 옵션으로 컨테이너 이름을 지정합니다.
```
docker run --name oracle-xe-11g-r2 -d -p 49161:1521 wnameless/oracle-xe-11g-r2
```

컨테이너 목록을 확인해보겠습니다.
```
docker ps
```

```
CONTAINER ID   IMAGE                        COMMAND                  CREATED         STATUS         PORTS                                       NAMES
707defb0daba   wnameless/oracle-xe-11g-r2   "/bin/sh -c '/usr/sb…"   5 seconds ago   Up 4 seconds   22/tcp, 8080/tcp, 0.0.0.0:49161->1521/tcp   oracle-xe-11g-r2
```

컨테이너 내 Linux 환경에서 bash 쉘 명령어를 입력하기 위해서는 docker exec 명령어를 실행합니다.
```
docker exec -it oracle-xe-11g-r2 /bin/sh
```

다음과 같이 출력된다면 접속에 성공한 것입니다.
```
#
```

이제 Oracle에 접속하기 위해 다음 명령을 실행합니다.
```
# su - oracle
```

다음과 같이 출력된다면 접속에 성공한 것입니다.
```
oracle@a7b919d06019:~$ 
```

SQL Plus를 실행하기 위해 다음 명령을 실행합니다. 
```
sqlplus '/as sysdba'
```

```
SQL*Plus: Release 11.2.0.2.0 Production on Thu Dec 24 07:37:17 2020

Copyright (c) 1982, 2011, Oracle.  All rights reserved.


Connected to:
Oracle Database 11g Express Edition Release 11.2.0.2.0 - 64bit Production

SQL> 
```

## 4. Oracle SQL Developer 설치 및 데이터베이스 연결 후 접속
[https://www.oracle.com/tools/downloads/sqldev-downloads.html](https://www.oracle.com/tools/downloads/sqldev-downloads.html)

Mac OS 용 파일을 다운로드 합니다. (계정 로그인이 필요합니다.)

압푹을 풀고 실행합니다.

‘SQLDeveloper’은(는) Apple에서 악성 소프트웨어가 있는지 확인할 수 없기 때문에 열 수 없습니다.'라는 메시지가 출력되면
Finder에서 Control 키를 누른 상태에서 우클릭하여 '열기'를 클릭하여 실행합니다.

좌측 Connections 탭의 + 버튼을 누릅니다.

다음 정보로 연결 정보를 입력합니다.

> hostname: localhost  
port: 49161  
sid: xe  
username: system  
password: oracle  

연결 확인을 위해 'Test' 버튼을 클릭합니다.

최근 OS 업데이트를 해서인지 'Local not recognized' 오류가 발생했습니다.

SQL Developer 프로그램 종료 후 관련 정보를 추가하기 위해 실행 파일을 우클릭하여 '패키지 내용 보기'를 클릭합니다.

다음 경로
```
SQLDeveloper.app/Contents/Resources/sqldeveloper/sqldeveloper/bin
```
의 'sqldeveloper.conf' 파일을 텍스트 편집기로 열어 다음 옵션을 추가합니다.
```
AddVMOption -Duser.language=ko
AddVMOption -Duser.country=KR
```

SQL Developer 프로그램을 다시 실행한 후 접속 정보를 입력하고 '테스트' 버튼을 클릭합니다.

연결이 정상적으로 되었다면 '상태:성공' 메시지가 출력됩니다.

'접속' 버튼을 클릭하면 Docker 컨테이너가 제공하는 Oracle 데이터베이스에 접속할 수 있습니다.
