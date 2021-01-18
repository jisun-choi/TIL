## Docker

### 가상화 (Virtualization)

- 한 서버에 하나의 OS 만 운영을 하는 경우 해당 OS 가 서버의 자원을 모두 사용하기 어렵다. 따라서 서버의 자원들이 idle 상태로 낭비되는 경우가 있을 수 있는데 가상화 기술을 사용하여 자원을 훨씬 효율적으로 사용할 수 있다.

#### Hypervisor vs Container

![](https://images.velog.io/images/wltjs10645/post/fcd0c0f4-9d9f-4a80-9bdb-3c269151da18/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-01-18%20%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB%2011.00.54.png)

- hypervisor
  : 물리적인 서버에서 하나 혹은 그 이상의 독립적인 운영체제가 돌아가는 구조<br>
  각각의 OS 는 서로에 대해서 알지 못하고 base OS 도 알지 못한다. (가상적으로 완전한 독립적 OS 로서 운영되는 것)

  > 하이퍼바이저는 가상 머신(Virtual Machine, VM)을 생성하고 구동하는 소프트웨어입니다. 가상 머신 모니터(Virtual Machine Monitor, VMM)라고도 불리는 하이퍼바이저는 하이퍼바이저 운영 체제와 가상 머신의 리소스를 분리해 VM의 생성과 관리를 지원합니다.
  > 하이퍼바이저로 사용되는 물리 하드웨어를 호스트라고 하며 리소스를 사용하는 여러 VM을 게스트라고 합니다.
  > 하이퍼바이저는 CPU, 메모리, 스토리지 등의 리소스를 처리하는 풀로, 기존 게스트 간 또는 새로운 가상 머신에 쉽게 재배치할 수 있습니다.
  > [Hypervisor](https://www.redhat.com/ko/topics/virtualization/what-is-a-hypervisor)

- container
  : 완전히 독립적인 OS 를 가상화 하는 것이 아니고 하나의 프로세스를 격리시키는 방식으로 운영체제가 전혀 다른 호스트에서는 실행을 시킬 수 없다. 보안적인 측면에서 hypervisor 보다 취약함.
  container 1 - process 1
- 차이점!? <br>
  hypervisor 는 OS 위에 또 OS 를 설치하기 때문에 상대적으로 무겁고 느리다. 하나의 OS 를 띄울 떄마다 시간이 많이 들고 많은 자원을 써야함. 반면에 container는 프로세스만 격리해서 사용하기 때문에 가볍고 빠르다. (MSA에 부합하는 가상화 기술)

```
#실행중인 컨테이너 보기
docker ps

#실행이 종료된 것을 포함한 모든 컨테이너 보기
docker ps -a

#생성 혹은 다운로드 된 이미지 보기
docker images

#모든 이미지 보기
docker images -a

#도커 이미지 빌드
docker build -t '도커허브 계정명'/'이미지명':'버전'

#도커 컨테이너 실행
docker run --name '컨테이너명''이미지명'

#도커 컨테이너 실행 & 컨테이너에 접속해서 쉘 실행
docker run -it '이미지명'/bin/bash
```
