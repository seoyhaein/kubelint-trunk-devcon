### 기억용.

- kubectl, helm 같은 경우는 별도의 컨테이너로 동작하게 하였다.
- ~/.kube/config 파일을 사용하도록 하였다. 향후 복잡해져서 지울려면 여기서 지우면된다. (context, user, cluster)

```bash
# 클러스터 만들어두기
kind create cluster --name demo-cluster --config infra/kind/kind-demo-cluster.yaml

# 클러스터 확인 
kind get clusters

# 클러스터의 노드 확인
kubectl get nodes

# 클러스터 삭제
kind delete cluster --name demo-cluster

# 네임스페이스 적용
kubectl apply -f k8s/namespace.yaml

# 네임스페이스 확인
kubectl get ns
# 또는
kubectl get namespace

# rq 적용, 여기서는 내부적으로 namespace 를 적용했다. namespace 이름은 'demo' 이다.
kubectl apply -f k8s/resourcequota.yaml
# 또는
#kubectl apply -f k8s/resourcequota.yaml -n namespace name

# 목록 조회
kubectl get resourcequota -n demo

# 상세 보기 rq-small 은 rq 의 이름이다.
kubectl describe resourcequota rq-small -n demo

# 만약 해당 네임스페이스에 여러 rq 가 적용되었다면 확인해볼 수 있다.
kubectl get resourcequota -n demo

# 사용량을 확인해볼 수 있는 명령어들이 있지만 이 부분은 Prometheus/Grafana 로 확인하는 것이 더 표준적인 방법일 것 같다.

# lr 적용하기
kubectl apply -f k8s/limitrange.yaml

# 또는
# kubectl apply -f k8s/limitrange.yaml -n demo

# 목록 조회
kubectl get limitrange -n demo

# 상세 보기
kubectl describe limitrange lr-defaults -n demo

# pod-stress.yaml 테스트 하기
kubectl apply -f k8s/pod-stress.yaml

# 확인
kubectl get pod stress-1 -n demo

# 삭제
kubectl delete pod stress-1 -n demo

# pod 내용 보기
kubectl describe pod stress-1 -n demo

# 향후 deployment 를 이용하는 것을 확장해나가자.
```
### TODO
- kubectl, helm 컨테이너 여기에 두자. 지금 에러 발생하는데, 일단 이거 해결하자. 이미지 업데이트 해서 에러난건지, 설정 문제인지 확인하자.