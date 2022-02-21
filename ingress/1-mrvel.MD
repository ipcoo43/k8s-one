# marvel-service Service
  - marvel collection

# pay-service Service
  - pay Pod 
  - pay Pod
  - pay Pod

# pod Ingress Controller : nginx Ingress
  - Ingress Rules
    - http://xx.xx.xx.xx/ -> svc marvel-service
    - http://xx.xx.xx.xx/pay -> svc pay-service

# ingress-nginx download
  - 사이트 : https://kubernetes.github.io/ingress-nginx/deploy/#bare-metal-clusters
  - wget https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.1.1/deploy/static/provider/baremetal/deploy.yaml

# deploy.yaml 수정
  - vim deploy.yaml
  - nodePort: 30100  # http의 286 line에 추가
  - nodePort: 30200  # https의 291 line에 추가

# deploy.yaml 실행
  - kubectl creat -f deploy.yaml
  - kubectl get namespaces
    - ingress-nginx   # 확인
  - kubectl get all -n ingress-nginx

# Default namespace 를 ingress-nginx로 치환
  - kubectl get namespace
  - kubectl config view
  - kubectl config set-context Ingress-admin@kubernetes --cluster=kubernetes --user=kubernetes-admin --namespace=ingress-nginx
  - kubectl config view
  - kubectl config use-context ingress-admin@kubernetes
  - kubectl get all
  - kubectl get svc -n default