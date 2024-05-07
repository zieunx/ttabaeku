# 5-5 쿠버네티스 Pod - static Pod(feat. kubelet daemon)

### static Pod

kubelet demon 으로 만들어지는 Pod

cat /var/lib/kubectl/config.yaml

여기에 staticPodPAth? 이런거 있음! 여기 위치에 만들어진 yaml기준으로 생성된다.

minikube로는 다음의 과정으로 확인 가능

- minikube ssh

접속 후 위의 위치에서.

static pod 경로 변경도 이 파일의 속성에서 해주면 됨