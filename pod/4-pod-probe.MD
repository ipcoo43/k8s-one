# 컨테이너 진단하기
  - livenessProbe: 컨테이너가 실행됐는지 확인 한다. 이 진단이 실패하면 kebelet은 컨테이너를 종료 시키고, 컨테이너를 재 시작 한다.
  - readinessProbe: 컨테이너가 실행된 후 실제로 서비스 요청에 등답할 수 있는지 진단 한다. 이 진단이 실패하면 endpoint controller은 해당 파등에 연결된 모든 서비스를 대상으로 endpoint 정보를 제거 한다. 

# handler
  - ExecAction: container안에 지정된 명령을 실행하고 종료 코드 0일때 Success라고 진단 한다.
  - TCPSocketAction: container 안에 지정된 IP와 port로 TCP 상태를 확인하고 port가 열려 있으면 success라고 진단 한다. 
  - HTTPGetAction: container안에 지정된 IP, port, path로 HTTP GET 요청을 보낸다.
  
# 진단 결과
  - Success: container가 진단 성공
  - Failure: container가 진단 실패
  - Unknown: 진단 자체가 실패해서 container 상태를 알 수 없음