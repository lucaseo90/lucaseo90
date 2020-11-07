---
title: Kubeflow 환경구성 (MacOS)
layout: single
author_profile: true
read_time: true
comments: true
share: true
related: true
tags:
- Kubeflow
- MiniKF
- Vagrant
toc: true
toc_sticky: true
markdown: kramdown
highlighter: rouge
---

# 들어가면서
`Kubeflow`의 `pipeline`에 대해 알기 위해서 환경 구성을 진행했다. 원래는 `minikube` 이용해서 진행했는데 1.0과 1.1 둘 다 순조롭게 진행되지 않아서 최종적으로 `Vagrant`를 이용해서 환경을 구성했다.  설치 당시 기준으로 `Kubeflow 1.1`이 최신인 것으로 알고 있는데 `Kubeflow 1.0`이 설치된 것을 확인했으며,  `pipeline` 개념 및 기능을 파악하는 것이 목적이기 때문에 버전은 큰 영향이 없을 것으로 판단한다.
# 설치

## Vagrant 설치
```
brew cask install virtualbox
brew cask install vagrant
brew cask install vagrant-manager  
```

## MiniKF 설치
```
vagrant init arrikto/minikf
vagrant up
```

## MiniKF 업그레이드
```
vagrant box update
vagrant box list
vagrant plugin update vagrant-persistent-storage  
vagrant destroy
-- 모든 로컬 상태를 삭제하는 명령은 수행하지 않음  
vagrant up
```

# 실행
`vagrant up`이 완료되면 `http://10.10.10.10/`에 접속하여 진행하면 최종적으로 아래와 같은 화면을 확인할 수 있다. 

![http://10.10.10.10/](https://user-images.githubusercontent.com/6668548/98359276-4e2b9280-206b-11eb-929c-d25eab46d1f7.png)

`Connect to Kubeflow` 버튼을 클릭하면 로그인 화면을 확인할 수 있고 `Credentials`에 명시된 계정과 비밀번호로 접속하면 `Kubeflow`의 대시보드를 확인할 수 있다.

![Kubeflow Dashboard](https://user-images.githubusercontent.com/6668548/98359743-06593b00-206c-11eb-9b39-8f94ee698734.png)

# 참고자료
* [Vagrant](https://sourabhbajaj.com/mac-setup/Vagrant/README.html)
* [MiniKF](https://www.kubeflow.org/docs/started/workstation/getting-started-minikf/)
