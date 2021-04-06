---
title: "[Docker] Docker 실행 시 operation not permitted 문제 해결 방법"
date: 2021-04-05 00:10:00 -0000
categories: [Docker, Mac]
---

최근 작업 도중 docker-compose로 구성한 이미지 파일을 실행하려고 하니 ```operation not permitted``` 오류가 발생했습니다.

최근 Mac OS를 Catalina로 업그레이드 했고 Transcend JetDrive를 장착하여 제거 가능한 볼륨에서 실행했는데 원인을 찾아보니...

Docker 앱이 docker-compose 파일이 위치한 폴더에 대한 접근 권한이 없기 때문인 것으로 보입니다.

```시스템 환경설정 > 보안 및 개인 정보 보호 > 파일 및 폴더```에 들어가면 특정 앱이 폴더 및 파일에 접근하는 것을 허용하게 만들 수 있는데

Docker 앱이 보이지 않거나 특정 폴더에 대한 체크 박스(예: 제거 가능한 볼륨, 문서 폴더 등)가 보이지 않는다면

```전체 디스크 접근 권한```에서 + 버튼을 눌러 Docker 앱을 추가해줍니다.

Catalina 부터 OS가 각각의 앱에 대해 디렉토리(문서 폴더, 데스크탑 폴더, 외부 볼륨 등) 별 권한 요청을 필요로 하는 것으로 정책이 변경되어 이와 같은 문제가 발생한 것 같습니다.

<https://apple.stackexchange.com/questions/376907/add-apps-to-files-and-folders-permissions>
