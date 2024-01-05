### 1. step_menifest => 기본적인 yaml 파일(deployment, svc, ingress) 을 통한 배포

### 2. step_menifest => 1번의 파일을 helm_chart로 변경하여 배포

### 3. EKS에 helm_Chart로 ArgoCD 서비스 구동 및 CD
- 설치 방법 및 셋팅은 notion 참고

### 4. git action을 통한 build 연동
  1. menifest-repo에서 automerge.yaml 워크플로우가 해당 Pull Request를 감지하고, automerge 라벨이 있을 경우 자동으로 병합
  2. app-repo의 변경사항을 자동으로 menifest-repo와 동기화하고, 관련 Pull Request를 자동으로 병합하는 과정
     
### 5. ingress는 AWS LB Controller 사용
- game2048: game2048.dohyun0304.shop
- argocd: argocd.dohyun0304.shop

### 6. Prometheus 설정
  1. https://majjangjjang.tistory.com/191?category=929057
  2. persistentVolume: #동적 binding
     enabled: true
     storageClassName: "gp2"
  3. Cluster csi driver 추가: https://docs.aws.amazon.com/ko_kr/eks/latest/userguide/ebs-csi.html
  4. node group role에 AmazonEBSCSIDriverPolicy 권한 AmazonEBSCSIDriverPolicy 부여 및 신뢰관계 수정
     (https://velog.io/@lijahong/0%EB%B6%80%ED%84%B0-%EC%8B%9C%EC%9E%91%ED%95%98%EB%8A%94-AWS-%EA%B3%B5%EB%B6%80-EKS-%ED%99%9C%EC%9A%A9%ED%95%98%EA%B8%B0-EBS-CSI-%EB%93%9C%EB%9D%BC%EC%9D%B4%EB%B2%84%EB%A5%BC-%EC%9D%B4%EC%9A%A9%ED%95%9C-%EB%8F%99%EC%A0%81-%ED%94%84%EB%A1%9C%EB%B9%84%EC%A0%80%EB%8B%9D)
  5. ingress 추가 및 dns 할당

