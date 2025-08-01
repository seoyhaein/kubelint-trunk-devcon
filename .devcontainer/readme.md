### Prerequisites

- trucnk cli 는 git 이 없으면 동작을 하지 않음으로 사전에 git 설정을 해두어야 한다.

```bash
git init
git config --global --add safe.directory "$(pwd)"

# dev container 들어와서. 커밋을 해줘야 함. 그래야 trunk 가 동작을 한다.
git add .
git commit -m "chore: initial commit"

trunk init
# 그 후 로그인 하라고 하면 spacebar 를 눌러서 건너뛴다.
# 만약 로그인해서 클라우드 기능을 이용할 수도 있다고 한다. 나는 건너 뛰었다.
```

- trunk 설정 필요.

```bash
# 커밋할때 마다 린팅 해줄지 물어봄. 나는 no 함.
Would you like Trunk to manage your git hooks and enable some built-in hooks?
# 나의 repo 를 일단 scan 해줄까 물어몸. 나는 no 함. 지금은 아무것도 없으니.
Would you like Trunk to scan your repo for issues?

# 이제 설정이 완료되면 .trunk 폴더 아래에 여러 파일들이 생성이됨.
# kube-linter 적용해줘야 함.
trunk check enable kube-linter

# trunk.yaml 보면 kube-linter 가 추가된것을 확인 할 수 있음.
# 이후 린팅을 하면 됨.
trunk check

# 테스트로 kind-demo-cluster.yaml 을 넣어두었는데 

→ Apply formatting (Y/n/all/none): all

 - hostPath: /mnt/kind-demo      # 호스트 디렉터리
   7 |         containerPath: /mnt/kind-demo  # 노드 컨테이너 안 경로
     |       - hostPath: /mnt/kind-demo # 호스트 디렉터리
     |         containerPath: /mnt/kind-demo # 노드 컨테이너 안 경로

# 위와 같이 주석에 대한 조정을 해주었다.     

```

### TODO
- 최적화 필요.