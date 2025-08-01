# .devcontainer/Dockerfile
FROM mcr.microsoft.com/devcontainers/base:ubuntu-22.04

# non-interactive 모드
ENV DEBIAN_FRONTEND=noninteractive

# 최소 의존만 설치
RUN apt-get update \
 && apt-get install -y --no-install-recommends \
      curl \
      ca-certificates \
      git \
      tar \
 && rm -rf /var/lib/apt/lists/*

# 여기서 이걸 해줄 필요는 없지만, 이미 devcontainer.json 에 정의되어 있고 먼저 devcontainer.json 을 먼저보고 들어오기때문에 상관없지만
# 개발자에게 명확하게 보여주기 위해서 이렇게 작성했으며, devcontainer.json 에서 설정이 없을때를 대비한 방어적 코드로 인식하면된다.
WORKDIR /app
