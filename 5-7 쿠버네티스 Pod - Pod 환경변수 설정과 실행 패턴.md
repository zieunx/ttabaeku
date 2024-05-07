# 5-7 쿠버네티스 Pod - Pod 환경변수 설정과 실행 패턴

### Pod의 환경변수 설정하기

```bash
# pod-nginx-resouces.yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginx-pod-env
spec:
  containers:
  - name: nginx-container
    image: nginx:1.14
    ports:
    - containerPort: 80
      protocol: TCP
    env:
    - name: MYVAR # 어떤 키
      value: "testvalue" # 어떤 값
```

위의 파일로 파드를 만들고 파드에 접속해본다.

```bash
kubectl exec nginx-pod-env -it -- /bin/bash
```

접속해서 env를 친다.

위에서 설정해준 env를 확인할 수 있다.

### 실행 패턴

- sidecar
- adapter
- embasder