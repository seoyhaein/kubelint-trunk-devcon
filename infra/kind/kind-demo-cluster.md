## 보안 사항

- hostPath 를 사용하여서 호스트의 디렉토리를 잡아주었는데, 이것은 선행적으로 호스트에 디렉토리가 있어야 문제없이 동작한다.
- 그리고, 컨테이너에서도 해당 호스트의 디렉토리를 마운트 잡아서 사용하고 있는데,
- 이때 보안문제가 발생하는데, 이 컨테이너의 디렉토리를 벗어나서 (샌드박스를 벗어나서) 보안문제를 일으킬수 있다. 만약 해커가 이렇게 샌드박스를 벗어나서 다른짓을 한다면??

### 오류 대응
- kind 안될때

```bash
 kind create cluster --name demo-cluster --config infra/kind/kind-demo-cluster.yaml --image kindest/node:v1.31.9 --wait 5m --retain

 # 안될때, context 가 해당 클러스터에 세팅되어 있어야 함. 확인해줌. kind-demo-cluster 라고 이름을 명명함.
 kubectl config use-context kind-demo-cluster

 # 지금 문제는 context 가 해당 클러스터에 설정이 안되어 있었다. kubectl 컨테이너를 사용하고 있는데 설정의 문제가 있었다. 일단 해당 컨테이너는 수정하지 않음.
 # 신기한데 잘되다가 갑자기 이런는데, 이건 나중에 보자. 시간날때 왜 그랬는지...
 kind export kubeconfig --name kind-demo-cluster --kubeconfig ~/.kube/config
```