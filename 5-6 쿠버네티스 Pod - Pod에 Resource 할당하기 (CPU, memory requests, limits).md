# 5-6 쿠버네티스 Pod - Pod에 Resource 할당하기 (CPU/memory requests, limits)

### Pod에 리소스 (cpu, memory) 할당하기

한 워커노드 내에 설정된 cpu와 memory를 하나의 파드가 다 먹어버리면? 다른파드들도 많은데?

### Pod Resource 요청 및 제한

- 리소스 요청
    - 파드를 실행하기 위한 최소 리소스 양 요청
- 리소스 리밋
    - 파드가 사용할 수 있는 최대 리소스 양을 제한
    - 메모리리밋을 초과해서 사용되는 파드는 종료(OOM Kill) 되며 다시 스케줄링 된다.

(Scheduler가 request를 받아서 적절한 워커노드에 배치)

[https://kubernetes.io/ko/docs/tasks/configure-pod-container/assign-cpu-resource/](https://kubernetes.io/ko/docs/tasks/configure-pod-container/assign-cpu-resource/)

1MB = 1000KB

iMi = 1024Ki

```bash
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
    - name: MYVAR
      value: "testvalue"
    resources:
      requests:
        memory: 500Mi # Mi로 해주면 
        cpu: 200m # 용량으로 하거나
      limits:
        memory: 1Gi
        cpu: 1 # 갯수로 하거나
```