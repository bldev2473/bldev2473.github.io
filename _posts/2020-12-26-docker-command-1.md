---
title: "[Docker] Docker CLI 명령어 정리"
date: 2020-12-26 00:10:00 -0000
categories: Docker
---

## Docker 명령어

#### Docker Hub에서 이미지 검색
```
docker search 이미지명
```

#### 이미지 확인
```
docker images
```

#### 이미지 삭제
```
docker rmi 이미지ID
```

#### 이미지 강제 삭제 (컨테이너 삭제 전)
```
docker rmi -f 이미지ID
```

#### 모든 이미지 삭제
```
docker rmi $(docker images -q)
```

#### 컨테이너 확인
```
docker ps
```

#### 컨테이너 중지
```
docker stop 컨테이너ID
```

#### 모든 컨테이너 중지
```
docker stop $(docker ps -aq)
```

#### 컨테이너 삭제
```
docker rm 컨테이너ID
```

#### 모든 컨테이너 삭제
```
docker rm $(docker ps -aq)
```

## Docker Compose 명령어
컨테이너 구성 정보인 docker-compose.yml 파일이 위치한 경로에서 다음 CLI 명령어를 실행합니다.

#### 컨테이너 실행
```
docker-compose up
```

#### 컨테이너 실행 (docker-compose.yml 파일 경로를 직접 지정하는 경우)
```
docker-compose -f 파일경로 up
```

#### 컨테이너 백그라운드 실행
```
docker-compose up -d
```

#### 가동 중인 컨테이너 확인
```
docker-compose ps
```

#### 컨테이너 정지
```
docker-compose stop
```

#### 리소스 삭제
```
docker-compose down
```
