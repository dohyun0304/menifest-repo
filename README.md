### 1. step_menifest => 기본적인 yaml 파일(deployment, svc, ingress) 을 통한 배포

### 2. step_menifest => 1번의 파일을 helm_chart로 변경하여 배포

### 3. EKS에 helm_Chart로 ArgoCD 서비스 구동 및 CD
- 설치 방법 및 셋팅은 notion 참고

### 4. git action을 통한 build 연동
  1. menifest-repo에서 automerge.yaml 워크플로우가 해당 Pull Request를 감지하고, automerge 라벨이 있을 경우 자동으로 병합
  2. app-repo의 변경사항을 자동으로 menifest-repo와 동기화하고, 관련 Pull Request를 자동으로 병합하는 과정
