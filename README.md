**유튜브 무료 오픈 강의 [따배쿠 - 입문편](https://www.youtube.com/watch?v=6n5obRKsCRQ&list=PLApuRlvrZKohaBHvXAOhUD-RxD0uQ3z0c) 기록**

> 책을 기반으로 한 강의에  설도 너무 잘해주셔서 별다르게 정리할 사항은 없지만, 공부하기 위해 끄적였던 내용 입니다.

- 수강 목표는 k8s 생태계가 전혀 와닿지 않을만큼 어려웠기 때문에 굵직한 용어나 구조, 컨셉을 이해하는 것이었다.
- 서버를 동일한 환경으로 구축하는 것이 조금 피곤해서 minikube로 실습했으며, 환경차이로 인해 제한 사항이나 실습에 어려움이 있었음.
- 굵직한 실습을 하기에 괜찮았으며, 설치하는 과정에서 진입장벽을 느껴서 거부감을 느끼는 것 보다는 빠르게 환경을 구축해서 실습하는 것에 초점을 둠.

|이름|태그|
|--- |--- |
|1-1. 쿠버네티스 소개 ||
|1-2. 쿠버네티스 설치 / 설치 없이 웹에서 실습하기 ||
|2-2. 도커 쿠버네티스 설치 / PC에 직접 설치하기||
|3-2. kubectl command / pod 생성하기||
|4-1. 쿠버네티스 아키텍처 - Kubernetes 동작원리||
|4-2. 쿠버네티스 아키텍처 - namespace||
|4-3. 쿠버네티스 아키텍처 - yaml템플릿과 API||
|5-1-1. 쿠버네티스 Pod - Container 정리와 Single / Multi Container Pod 생성||
|5-1-2. 쿠버네티스 Pod - Pod 동작 flow||
|5-2. 쿠버네티스 Pod - livenessProbe를 이용해서 Self-healing Pod 만들기||
|5-3, 4. 쿠버네티스 Pod - init container & infra container||
|5-5 쿠버네티스 Pod - static Pod(feat. kubelet daemon)||
|5-6 쿠버네티스 Pod - Pod에 Resource 할당하기 (CPU/memory requests, limits)||
|5-7 쿠버네티스 Pod - Pod 환경변수 설정과 실행 패턴||
|6. Controller|`CronJob` `DaemonSet` `Deployment` `Job` `ReplicaSet` `RollingUpdate` `StatefulSet` |
|7. Service|`ClusterIP` `ExternalName` `Headless Service` `Kube Proxy` `LoadBalancer` `NodePort` `service`  |
|8. Ingress|`Ingress` `Ingress Controller` |
|9. Label|`Annotation` `Canary(카나리)` `Label` |
|10. ConfigMap|`ConfigMap` |
|11. Secret|`Secret` |
