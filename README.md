# AWS 및 GitHub Actions를 활용한 CI/CD 파이프라인

## AWS 서비스

### EC2 (Elastic Compute Cloud)

- **기능**: 가상 서버 인스턴스를 제공합니다.
- **사용법**: 서버를 생성하고 웹 서버, 데이터베이스 서버 등으로 활용합니다.

### CodeDeploy

- **기능**: 소프트웨어 배포 자동화 서비스입니다.
- **사용법**: 애플리케이션과 배포 그룹을 정의하여 자동 배포를 구성합니다.

### S3 (Simple Storage Service)

- **기능**: 객체 스토리지 서비스입니다.
- **사용법**: 파일을 업로드하여 데이터를 저장하고 관리합니다.

### IAM (Identity and Access Management)

- **기능**: 액세스 관리 서비스입니다.
- **사용법**: 사용자, 그룹, 역할을 생성하고 정책으로 권한을 관리합니다.

### RDS (Relational Database Service)

- **기능**: 관계형 데이터베이스 관리 서비스입니다.
- **사용법**: RDS 인스턴스를 생성하고 데이터베이스를 운영합니다.

## GitHub Actions 워크플로우 (`deploy.yaml`)

### 환경 변수

- `S3_BUCKET_NAME`: S3 버킷 이름
- `CODE_DEPLOY_APPLICATION_NAME`: CodeDeploy 애플리케이션 이름
- `CODE_DEPLOY_DEPLOYMENT_GROUP_NAME`: CodeDeploy 배포 그룹 이름

### 작업

1. **Checkout**: 소스 코드를 가져옵니다.
2. **Set up JDK 21**: Java 21을 설정합니다.
3. **Build with Gradle**: Gradle을 사용하여 애플리케이션을 빌드합니다.
4. **Make zip file**: 빌드 결과물을 zip 파일로 만듭니다.
5. **Configure AWS credentials**: AWS 자격 증명을 설정합니다.
6. **Upload to S3**: zip 파일을 S3 버킷에 업로드합니다.
7. **CodeDeploy**: CodeDeploy를 사용하여 애플리케이션을 배포합니다.
