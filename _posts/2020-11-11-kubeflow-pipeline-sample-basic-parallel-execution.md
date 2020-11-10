---
title: Kubeflow Pipeline - [Sample] Basic - Parallel execution
layout: single
author_profile: true
read_time: true
comments: true
share: true
related: true
tags:
- Kubeflow
- Pipeline
- Tutorial
toc: true
toc_sticky: true
markdown: kramdown
highlighter: rouge
---

# 들어가면서
Kubeflow Pipeline에 대한 이해를 위해 간단한 예제를 실행시켜봤다.

> 결론부터 이야기하면 Pipeline 실행 시 Pod와 관련한 에러 때문에 Pending 상태가 되는 상황이다..

# 실습
## Parallel Execution 예제 선택
Pipeline 대시보드를 확인해보면 간단한 Pipeline 예제들이 등록되어 있다. 그중 Parallel Execution 예제를 실행해보려고 했다.
<img width="1685" alt="Pipeline Samples" src="https://user-images.githubusercontent.com/6668548/98733435-d9968200-23e3-11eb-9bbf-51382f2c67e6.png">

## Experiemnt 생성 선택
해당 파이프라인을 선택하면 우측 상단에 `Create Experiment`를 확인할 수 있다. 

<img width="1700" alt="Parallel Exeuction Graph" src="https://user-images.githubusercontent.com/6668548/98733432-d8fdeb80-23e3-11eb-8661-2af81ac5ceac.png">

## Experiment 이름 지정
파이프라인 이름을 지어준다. 여기서는 `Hello Kubeflow Pipeline`이라고 이름을 지정했다.

<img width="660" alt="New Experiment" src="https://user-images.githubusercontent.com/6668548/98733430-d8655500-23e3-11eb-85a8-e23994d26e05.png">

## Experiemnt 상세 파라미터 설정
파이프라인 실행과 관련한 상세 파라미터를 설정할 수 있는데 특별하게 변경한 것은 없다.

<img width="660" alt="Start a run" src="https://user-images.githubusercontent.com/6668548/98733428-d7ccbe80-23e3-11eb-81c6-176a2e9a462d.png">

## Experiment 생성 완료
Experiemnt를 생성하면 해당 파이프라인에 대한 실행이 등록된 것을 확인할 수 있다.

<img width="1920" alt="Registered Experiment" src="https://user-images.githubusercontent.com/6668548/98733425-d7342800-23e3-11eb-8447-66773eba8716.png">

## Experiemnt 진행 상황 확인
공교롭게도 실행 중에 Pod를 초기화 하는 과정에서 에러가 발생한다.

> 에러를 해결할 방법을 찾아보고 있는 중...

<img width="1700" alt="Parallel Execution Error 1" src="https://user-images.githubusercontent.com/6668548/98733420-d69b9180-23e3-11eb-83e6-e6a53e4c6804.png">

<img width="1700" alt="Parallel Exeuciton Error 2" src="https://user-images.githubusercontent.com/6668548/98733408-d3080a80-23e3-11eb-9d3f-a32121684c8d.png">


# Reference
* [Pipelines Quickstart: Run a basic pipeline ](https://www.kubeflow.org/docs/pipelines/pipelines-quickstart/#run-a-basic-pipeline)
