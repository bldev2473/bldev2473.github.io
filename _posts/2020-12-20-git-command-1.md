---
title: "[Git] GitFlow"
date: 2020-12-20 00:10:00 -0000
categories: Git
---
https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow

#### 브랜치 종류
1\) master: 릴리즈 이력 관리 브랜치  
2\) develop: feature 브랜치의 통합을 위한 브랜치  
3\) feature: 실제 작업 영역이 되는 브랜치  
&#45; master 브랜치로부터 브랜치를 생성하는 것 대신 develop 브랜치를 부모 브랜치로 사용  
&#45; feature 브랜치에서 작업이 끝나면 develop 브랜치에 병합하여 작업 내역을 develop 브랜치에 반영  
&#45; feature 브랜치는 master 브랜치와는 직접적으로 상호작용하지 않아야 함

#### 브랜치 생성 과정
1\) develop 브랜치 생성  
  1. 로컬에서 빈 develop 브랜치 생성  
  ```
  git branch develop
  ```  
  2. develop 브랜치를 origin에 푸쉬  
  ```
  git push -u origin develop
  ```  
2\) feature 브랜치 생성  
  1. develop 브랜치 체크아웃  
  ```
  git checkout develop
  ```  
  2. feature 브랜치 생성 및 체크아웃  
  ```
  git checkout -b feature_branch
  ```  
3\) feature 브랜치 종료  
  1. develop 브랜치 체크아웃  
  ```
  git checkout develop
  ```  
  2. feature 브랜치를 develop 브랜치에 병합  
  ```
  git merge feature_branch
  ```

#### Eclipse GitFlow
1\) Feature 시작  
  1. develop 브랜치 체크아웃  
  2. develop 브랜치 우클릭 -> GitFlow -> Start Feature -> 브랜치명 입력 -> feature 브랜치로 체크아웃 됨  
  3. feature 브랜치 우클릭 -> Publish Feature (feature 브랜치가 원격에 생성됨)  
    - 다른 사람의 feature 브랜치를 내려받기 위해서는 fetch feature 실행

2\) Feature 작업 진행  
  1. 작업  
  2. feature 브랜치 체크아웃 상태에서 작업 내역 커밋 (푸쉬가 아닌 커밋까지만 수행)  
  3. 커밋 후 Publish Feature를 수행하고 다른 사용자가 원격 저장소에서 해당 브랜치를 페치 해보면 origin/develop으로부터 갈라진 origin/feature 브랜치가 표시됨  

3\) Feature 종료  
&#45; feature 브랜치 우클릭 -> GitFlow -> Finish Feature -> Squash 체크 -> Finish -> develop 브랜치로 체크아웃 됨 (develop에 feature가 병합됨)  
&#45; feature 브랜치에서 여러 개의 커밋을 수행한 경우 Publish Feature 시 Squash를 하여 여러 커밋을 하나의 커밋으로 합치고 develop에 병합시킴

4\) Push  
&#45; develop 브랜치 우클릭 -> Push Branch (develop 브랜치에서 origin 브랜치로 푸시됨)

#### SourceTree GitFlow
1\) Git Flow 저장소 초기화  
2\) 새 기능 시작: develop 브랜치 체크아웃 - 깃 플로우 - 다른 동작 - 새 기능 시작 - 기능명 입력  - 최근 개발 브랜치 선택 - 확인  
&#45; 'feature/기능명' 이름의 feature 브랜치가 생성되고 체크아웃 됨
3\) 작업: 작업 후 커밋  
4\) feature 브랜치 푸시  
5\) 기능 마무리: feature 브랜치 체크아웃 - 깃 플로우 - 기능 마무리 - 기능명(feature 브랜치명) - 옵션 선택 - 확인  
&#45; 기본값으로 병합 수행
&#45; 'develop 브랜치에 rebase 옵션' 체크 시 리베이스
&#45; feature 브랜치가 삭제되고(기본값) develop 브랜치로 체크아웃 됨
4\) develop 브랜치 푸시  

#### GitFlow 초기화
```
git config --remove-section "gitflow.path"
git config --remove-section "gitflow.prefix"
git config --remove-section "gitflow.branch"
git flow init
```

```
git config [key] [value]
gitflow.branch.master The name of the branch treated as master. Default: master.
gitflow.branch.develop The name of the branch treated as develop. Default: develop.
gitflow.prefix.feature The prefix for feature branches. Default: feature/.
gitflow.prefix.release The prefix for release branches. Default: release/.
gitflow.prefix.hotfix The prefix for hotfix branches. Default: hotfix/.
gitflow.prefix.support The prefix for support branches. Default: support/.
gitflow.prefix.versiontag The prefix for version tags. Default: empty.
gitflow.origin The name of the remote treated as origin. Default: origin.
gitflow.feature.start.fetch Always fetch from origin before certain operations. Default: false
```
