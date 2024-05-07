# 5-3, 4. 쿠버네티스 Pod - init container & infra container

### init container

본 컨테이너 실행 전에 초기화해주어야하는게 있으면 실행한느 컨테이너

실습파일: init-container-exam.yaml

### infra contatiner(pause) 이해하기

파드 안에 아무것도 하지 않는 pause가 생긴다. 파드마다 생기고 사라짐!

파드에 대한 infra를 관리하고 생성해주는 역할을 함.