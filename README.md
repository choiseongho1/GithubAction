# AWS 및 GitHub Actions를 활용한 CI/CD 파이프라인

## ### AWS 서비스 간의 관계
#### EC2 (Elastic Compute Cloud)
- **기능**: 가상 서버 인스턴스 제공.
- **연관성**: 애플리케이션 실행 환경. RDS와 연결되어 데이터베이스 서비스를 이용하고, CodeDeploy를 통해 애플리케이션 배포를 자동화합니다.

#### RDS (Relational Database Service)
- **기능**: 관리형 관계형 데이터베이스 서비스 제공.
- **연관성**: EC2 인스턴스에서 실행되는 애플리케이션에 데이터베이스 기능 제공. 애플리케이션 데이터를 저장하고 관리합니다.

#### S3 (Simple Storage Service)
- **기능**: 객체 스토리지 서비스 제공.
- **연관성**: 애플리케이션의 아티팩트, 로그 등을 저장. CodeDeploy가 S3에서 아티팩트를 가져와 EC2 인스턴스에 배포합니다.

#### CodeDeploy
- **기능**: 애플리케이션 배포 자동화.
- **연관성**: S3에 저장된 애플리케이션 아티팩트를 EC2 인스턴스에 배포. 배포 프로세스의 자동화와 표준화를 담당합니다.

#### IAM (Identity and Access Management)
- **기능**: 액세스 및 권한 관리.
- **연관성**: EC2, RDS, S3 등 모든 AWS 서비스에 대한 액세스 제어. 사용자와 서비스의 권한을 관리하여 보안을 유지합니다.

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
