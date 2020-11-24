---
title: Docker 환경에서 KONG 설치
layout: single
author_profile: true
read_time: true
comments: true
share: true
related: true
tags:
- KONG
- API Gateway
- Docker
toc: true
toc_sticky: true
markdown: kramdown
highlighter: rouge
categories:
- Practice
---

# 들어가면서
gRPC 게이트와 관련해서 Kong을 사용해볼 필요가 생겼다.


# Docker 환경에서 KONX 설치

## 네트워크 생성
```shell
$ docker network create kong-net
```
## 디스크 볼륨 생성
```
$ docker volume create kong-vol
```
## 설정 파일 작성
```
$ docker volume inspect kong-vol
```

명령을 수행하면 아래와 같이 터미널에 출력되는데 Ubuntu 18.04에서 설치할 때는 해당 경로에 디렉토리가 미리 구성되어 있었는데 MacOS의 경우 `/docker/` 부터 디렉토리가 없었다.

> 디렉토리 구성해주고 권한 설정이 필요하다.

```
[
    {
        "CreatedAt": "2020-11-24T10:11:22Z",
        "Driver": "local",
        "Labels": {},
        "Mountpoint": "/var/lib/docker/volumes/kong-vol/_data",
        "Name": "kong-vol",
        "Options": {},
        "Scope": "local"
    }
]
```

`kong.yml` 파일을 vim으로 열어서 아래와 같이 설정해줬다.

```yaml
_format_version: "1.1"
 
services:
- name: my-service
  url: https://example.com
  plugins:
  - name: key-auth
  routes:
  - name: my-route
    paths:
    - /
 
consumers:
- username: my-user
  keyauth_credentials:
  - key: my-key
```

## 데이터베이스 컨테이너 생성
처음에는 데이터베이스를 제외하고 환경 구성을 했는데, 이러한 경우 Kong의 플러그인 사용에 제약이 있고, 테스트 해봐야 하는 gRPC관련 플러그인도 동작하지 않아서 데이터베이스도 컨테이너로 구성해줬다. 

카산드라 또는 데이터베이스를 사용할 수 있는데 익숙한 데이터베이스로 환경 구성을 진행했다.

```shell
$ docker run -d --name kong-database \
    --network=kong-net \
    -p 5432:5432 \
    -e "POSTGRES_USER=kong" \
    -e "POSTGRES_DB=kong" \
    -e "POSTGRES_PASSWORD=kong" \
    -e "POSTGRES_HOST_AUTH_METHOD=trust" \
    postgres:latest
```

## Kong 데이터베이스 구성
데이터베이스 컨테이너를 생성하고 해당 컨테이너에 Kong과 관련하여 필요한 구성을 해주기 위해 아래 명령을 수행해야 한다.

```shell
$ docker run --rm \
    --network=kong-net \
    --link kong-database:kong-database \
    -e "KONG_DATABASE=postgres" \
    -e "KONG_PG_HOST=kong-database" \
    -e "KONG_CASSANDRA_CONTACT_POINTS=kong-database" \
    kong kong migrations bootstrap
```

## Kong 컨테이너 생성
Kong 컨테이너를 생성한다.

```shell
$ docker run -d --name kong \
    --network=kong-net \
    --link kong-database:kong-database \
    -e "KONG_DATABASE=postgres" \
    -e "KONG_PG_HOST=kong-database" \
    -e "KONG_CASSANDRA_CONTACT_POINTS=kong-database" \
    -e "KONG_PROXY_ACCESS_LOG=/dev/stdout" \
    -e "KONG_ADMIN_ACCESS_LOG=/dev/stdout" \
    -e "KONG_PROXY_ERROR_LOG=/dev/stderr" \
    -e "KONG_ADMIN_ERROR_LOG=/dev/stderr" \
    -e "KONG_ADMIN_LISTEN=0.0.0.0:8001, 0.0.0.0:8444 ssl" \
    -p 8000:8000 \
    -p 8443:8443 \
    -p 8001:8001 \
    -p 8444:8444 \
    kong
```

## Konga 컨테이너 생성
Kong에 대한 대시보드 기능을 하는 Konga 컨테이너를 생성한다. 

```shell
$ docker run -d -p 1337:1337 --name konga \
    --network=kong-net \
    -v /var/data/kongadata:/app/kongadata \
    -e "NODE_ENV=production" \
    pantsel/konga
```

## Konga 설정
Konga 까지 설치된 후 `http://localhost:1337/`로 접근하면 관리자 계정을 생성하는 화면이 뜨고, 연결을 위한 KONG에 대한 접근 정보를 입력하는 화면이 나타난다. 

이름은 `local-kong` Kong의 Admin URL은 `http://kong:8001`로 했는데 여기서 `kong`은 컨테이너 이름이다. 

![Setting Kong Connection](https://user-images.githubusercontent.com/6668548/100094839-f7142300-2e9c-11eb-950d-7095b966a87e.png)

Kong과 연결을 해주면 다음과 같은 화면을 확인할 수 있다.

![Konga Dashboard](https://user-images.githubusercontent.com/6668548/100094868-01ceb800-2e9d-11eb-9323-8f1fa2a2b5f5.png)
# Reference
* [오픈소스 API 게이트웨이 Kong](https://bcho.tistory.com/1361)
* dockerhub - [kong](https://hub.docker.com/_/kong)
