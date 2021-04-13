---
title: Git Scrapbook
layout: single
author_profile: true
read_time: true
comments: true
share: true
related: true
tags:
- Git
- Scrapbook
toc: true
toc_sticky: true
markdown: kramdown
highlighter: rouge
categories:
- Scrapbook
---

# [github 잘못 올라간 파일 히스토리까지 삭제하기](https://donologue.tistory.com/373)
```shell
$ git filter-branch -f --index-filter 'git rm --cached --ignore-unmatch [파일 경로와 이름]' --prune-empty -- --all
$ git push origin [브랜치 명] --fore
```

# [github 하나로 1인 개발 워크플로우 완성하기](https://www.huskyhoochu.com/issue-based-version-control-201/)

### 이슈 만들기

### 로컬 저장소에 브랜치 생성
```shell
$ git checkout -b [issue number]-[issue summary]
$ git push --set-upstream origin [issue number]-[issue summary]
```

### 목표 해결 && 테스트 

### 커밋과 푸시
```shell
$ git commit -m "#[issue number] commit contents" 
$ git commit --amend
...
Resolves #[issue number]
$ git push
```

### 메인 브랜치에 병합
```shell
$ git rebase dev
$ git checkout dev
$ git pull --rebase=preserve
$ git merge [issue number]-[issue summary]
```
* rebase: 현재 브랜치의 커밋 히스토리에 병합할 브랜치의 히스토리를 합쳐서 두 브랜치의 루트를 하나로 재정립
* `git pull --rebase=preserve`: 원격 브랜치의 최신 사본을 업데이트 받는 명령어

### 이슈 닫기
```shell
$ git push origin -d [issue number]-[issue summary] && git branch -d [issue number]-[issue summary]
```
