# 3-2. kubectl command / pod 생성하기

```bash
kubectl api-resources
```

쿠버네티스가 제공하는 여러가지 오브젝트들을 볼 수 있다.

나오는 NAME 혹은 SHORTNAME로 사용할 수 있다.

```bash
kubectl 오브젝트명 --help
```

특정 오브젝트가 어떤건지, 어떻게 활용하면 좋을지는 특정 오브젝트 뒤에 ‘—help’붙히면 나온다.

```bash
kubectl get nodes (-o wide)자세히보기옵션
```

모든 노드들을 조회한다.

```bash
kubectl describe node 노드명
kubectl describe pod 파드명
```

특정 오브젝트를 자세히 볼 수 있다.

```bash
kubectl run
kubectl create deployment

# example
kubectl run webserver --image=nginx:1.14 --port 80
pod/webserver created
```

컨테이너 파드 만들기