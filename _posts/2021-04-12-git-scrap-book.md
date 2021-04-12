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

