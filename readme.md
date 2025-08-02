### 기억용.

- kubectl, helm 같은 경우는 별도의 컨테이너로 동작하게 하였다.  
- ~/.kube/config 파일을 사용하도록 하였다. 향후 복잡해져서 지울려면 여기서 지우면된다. (context, user, cluster)  

```bash
# 클러스터 만들어두기
kind create cluster --name demo-cluster --config infra/kind/kind-demo-cluster.yaml 

# 클러스터 확인
kubectl get nodes

# 네임스페이스 적용
kubectl apply -f k8s/namespace.yaml

# 네임스페이스 확인
kubectl get ns 
# 또는
kubectl get namespace
```