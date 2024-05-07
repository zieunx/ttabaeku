# 4-2. 쿠버네티스 아키텍처 - namespace

실행하는방법은 크게 두가지다.

1. CIL
2. yaml

nginx yaml 파일을 만들어서 실행할거다.

cat > nginx.yaml 해준 후 아래의 내용을 붙혀넣고 ctrl + d 해주면 저장이 된다.

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: mypod
spec:
  containers:
  - image: nginx:1.14
    name: nginx
    ports:
    - containerPort: 80
    - containerPort: 443

```

저장 후 해당 파일로 파드를 마든다.

```bash
kubectl create -f nginx.yaml

# 별도의 네임스페이스 지정을 안했기 때문에 default namespace 다.
kubectl get pods -n default

# controller, api 등 우리가 앞에서 배운 마스터의 정보들을 가진건 kube-system namespace로 확인 가능하다.
kubectl get pods -n kube-system
```

네임스페이스를 만든다

```bash
# CLI로 만들기
kubectl create namespace blue
# 만들기 드라이런 yaml로 확인하기 그리고 그거로 파일 만들기 
kubectl create namespace orange --dry-run -o yaml > orange-ns.yaml
# 이 파일로 namespace 만들기
kubectl create -f orange-ns.yaml
```

위에서 만든 네임스페이스에 nginx 를 만들어보자.

```bash
kubectl create -f nginx.yaml -n blue
```

아니면 실행파일 yaml에 네임스페이스를 지정할 수 있다.

```bash
# nginx.yaml
apiVersion: v1
kind: Pod
metadata:
  name: mypod
  **namespace: orange**
spec:
  containers:
  - image: nginx:1.14
    name: nginx
    ports:
    - containerPort: 80
    - containerPort: 443

# 위의 파일을 실행하면 바로 orange namespace 에 생긴다
kubectl create -f nginx.yaml
```

### 특정 네임스페이스를 base로 지정하기, 사용할 namespace switch

쿠버네티스 config 에 namespace 를 등록해줘야 한다.

등록하는 공간을 쿠버네티스의 ‘컨텍스트’ 라고 한다.

자세# 히 보려면 ‘kubectl config —help’

```bash
# config 보기
kubectl config view

# 조회 결과
apiVersion: v1
clusters:
- cluster:
    certificate-authority: /Users/zieunx/.minikube/ca.crt
    extensions:
    - extension:
        last-update: Fri, 01 Mar 2024 00:32:44 KST
        provider: minikube.sigs.k8s.io
        version: v1.32.0
      name: cluster_info
    server: https://192.168.64.2:8443
  name: minikube
contexts:
- **context:**
    **cluster**: **minikube**
    extensions:
    - extension:
        last-update: Fri, 01 Mar 2024 00:32:44 KST
        provider: minikube.sigs.k8s.io
        version: v1.32.0
      name: context_info
    namespace: default
    **user: minikube**
  name: minikube
current-context: minikube
kind: Config
preferences: {}
users:
- name: minikube
  user:
    client-certificate: /Users/zieunx/.minikube/profiles/minikube/client.crt
    client-key: /Users/zieunx/.minikube/profiles/minikube/client.key

# 위의 클러스터와 유저정보를 가지고 블루 컨텍스트를 만들거다.
# 컨텍스트 이름은 'blue@kubenetes'라고 지었는데, 마음대로 지어도 된다.
# namespace를 blue로 지정했다.
kubectl config set-context blue@kubenetes --cluster=minikube --user=minikube --namespace=blue

# 현재 컨텍스트 조회
kubectl config current-context

# 바꾼다 다른 네임스페이스로
kubectl config use-context blue@kubenetes

# 다른 네임스페이스의 파드를 지울수도 있다.
kubectl delete pods mypod -n default
```

### namespace 삭제하기

삭제하면 안에있는 파드들도 다 지워진다.