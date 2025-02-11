# 파드 생명 주기
  - Pending: 쿠버네티스 시스템에 파드를 생성하는 중임을 뜻 한다. 이 상태는 컨테이너 이미지를 다운로드한 후 전체 컨테이너를 실행하는 도중이므로 파드 안의 전체 컨테이너가 실행될 때까지 시간이 걸린다.
  - Running: 파드 안 모든 컨테이너가 실행 중인 상태 이다. 1개 이상의 컨테이너가 실행 중이거나 시작 또는 재시작 상태일 수 있다.
  - Succeeded: 파드 안 모든 컨테이너가 정상 실행 종료된 상태로 재시작되지 않는다.
  - Failed: 파드 안의 모든 컨테이너 중 정상적으로 실행 종료되지 않은 컨테이너가 있는 상태 이다. 
  - Unknow: 파드의 상태를 확인할 수 없는 상태 이다. 보통 파드가 있는 노드와 통신할 수 없을 때 이다.

### 현재 파드 생명 주기 확인 방법
 - kubectl describe pod pod_name
   - Conditions:
     - Type:           Status
     - Initialized:    True  # 모든 초기화 컨테이너가 성공적으로 시작 완료
     - Ready:          True  # 파드는 요청들을 실행할 수 있고 연결된 모든 서비스에 추가
     - ContainerReady: True  # 파드 안의 모든 컨테이너 준비 상태
     - PodScheduled:   True  # 파드가 하나의 노드로 스케줄을 완료