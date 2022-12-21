## Install Docker Engine on Rockey

### OS requirements

centos-extras 리포지토리가 활성화되어 있어야 한다.

overlay2 스토리지 드라이버를 권장한다.

### 이전 버전 제거

이전 버전의 docker 또는 docker-engine 이 설치된 경우 관련 종속성과 함께 제거한다.

```
 sudo yum remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-engine
```

### 설치 방법

> **Set up the repository**

yum-utils 유틸리티를 제공하는 패키지를 설치하고 레포지토리를 설정한다.

```
sudo yum install -y yum-utils
```

```
sudo yum-config-manager \
    --add-repo \
    https://download.docker.com/linux/centos/docker-ce.repo
```

> **Install Docker Engine**

```
sudo yum install docker-ce docker-ce-cli containerd.io docker-compose-plugin
```

특정 버전의 Docker 엔진을 설치하려면 리포지토리에서 사용 가능한 버전을 나열한 다음 선택하여 설치한다.

> **버전 확인**

```
yum list docker-ce --showduplicates | sort -r
```

> **특정 버전 도커 설치**

```
sudo yum install docker-ce-<VERSION_STRING> docker-ce-cli <VERSION_STRING> containerd.io docker-compose-plugin
```

> **도커 시작**

```
sudo systemctl enable --now docker
```

> **도커 테스트**

```
sudo docker run hello-world
```

### Uninstall Docker Engine

**1. Docker Engine, CLI, Containerd 및 Docker Compose 패키지 제거**

```
yum remove docker-ce docker-ce-cli containerd.io docker-compose-plugin
```

**2. 호스트의 이미지, 컨테이너, 볼륨 또는 사용자 지정 구성 파일은 자동으로 제거되지 않는다. 모든 이미지, 컨테이너 및 볼륨 삭제**

```
sudo rm -rf /var/lib/docker
sudo rm -rf /var/lib/containerd
```

> 출처

[docker docs](https://docs.docker.com/engine/install/centos/#install-using-the-repository)






















