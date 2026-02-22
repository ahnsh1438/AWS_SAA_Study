# Placeholder
## Q1(pdf Q#15)
최근 AWS로 마이그레이션한 회사가 프로덕션 VPC로 들어오고 나가는 트래픽을 보호하기 위한 솔루션을 구현하려고 합니다.
이 회사는 온프레미스 데이터 센터에 검사 서버를 운영하며 트래픽 검사 및 필터링과 같은 특정 작업을 수행했습니다.
이 회사는 AWS 클라우드에서도 동일한 기능을 구현하고자 합니다.
다음 중 어떤 솔루션이 이러한 요구 사항을 충족할까요?

A. 프로덕션 VPC에서 Amazon GuardDuty를 사용하여 트래픽 검사 및 필터링을 수행합니다.
B. 트래픽 미러링을 사용하여 프로덕션 VPC의 트래픽을 미러링하고 트래픽 검사 및 필터링을 수행합니다.
C. AWS 네트워크 방화벽을 사용하여 프로덕션 VPC에 필요한 트래픽 검사 및 필터링 규칙을 생성합니다.
D. AWS 방화벽 관리자를 사용하여 프로덕션 VPC에 필요한 트래픽 검사 및 필터링 규칙을 생성합니다.

AWS Network Firewall
관리형 방화벽
VPC 레벨 트래픽 검사
인바운드/아웃바운드 검사
상태 저장 (stateful inspection)

온프레 inspection server 대체 가능

VPC 내 트래픽 검사 + 필터링
→ AWS Network Firewall

정답 : C

## Q2(pdf Q#36)
한 회사가 AWS 클라우드에서 애플리케이션을 개발하고 있습니다. 이 애플리케이션은 두 개의 AWS 리전에 있는 Amazon S3 버킷에 데이터를 저장합니다. 이 회사는
AWS KMS(AWS Key Management Service) 고객 관리형 키를 사용하여 S3 버킷에 저장된 모든 데이터를 암호화해야 합니다.
두 S3 버킷의 데이터는 모두 동일한 KMS 키로 암호화 및 복호화되어야 합니다. 데이터와 키는 각각 두 리전에 저장되어야 합니다.
이러한 요구 사항을 가장 적은 운영 오버헤드로 충족하는 솔루션은 무엇일까요?

A. 각 리전에 S3 버킷을 생성합니다. Amazon S3 관리형 암호화 키(SSE-S3)를 사용하여 서버 측 암호화를 사용하도록 S3 버킷을 구성합니다.
S3 버킷 간 복제를 구성합니다.
B. 고객 관리형 다중 리전 KMS 키를 생성합니다. 각 리전에 S3 버킷을 생성합니다. S3 버킷 간 복제를 구성합니다.
애플리케이션이 클라이언트 측 암호화를 사용하여 KMS 키를 사용하도록 구성합니다.
C. 각 리전에 고객 관리형 KMS 키와 S3 버킷을 생성합니다. Amazon S3 관리형 암호화 키(SSE-S3)를 사용하여 서버 측 암호화를 사용하도록 S3 버킷을 구성합니다.
S3 버킷 간 복제를 구성합니다.
D. 각 리전에 고객 관리형 KMS 키와 S3 버킷을 생성합니다. AWS KMS 키(SSE-KMS)를 사용하여 서버 측 암호화를 사용하도록 S3 버킷을 구성합니다.
S3 버킷 간 복제를 구성합니다.

AWS Key Management Service

하나의 KMS 키를 여러 Region에 복제
동일한 Key ID, 동일한 key material
논리적으로 같은 키로 동작

Customer managed Multi-Region KMS key 생성
각 Region에 S3 bucket 생성
replication 설정
application이 해당 KMS key로 암호화

정답 : B

## Q3(pdf Q#80)
최근 한 회사가 애플리케이션 마이그레이션 프로젝트 지원을 위해 AWS 관리형 서비스 제공업체(MSP) 파트너와 계약을 체결했습니다.
솔루션 아키텍트는 기존 AWS 계정의 Amazon Machine Image(AMI)를 MSP 파트너의 AWS 계정과 공유해야 합니다. 이 AMI는
Amazon Elastic Block Store(Amazon EBS)를 기반으로 하며, AWS Key Management Service(AWS KMS) 고객 관리 키를 사용하여
EBS 볼륨 스냅샷을 암호화합니다.
솔루션 아키텍트가 MSP 파트너의 AWS 계정과 AMI를 공유하는 가장 안전한 방법은 무엇일까요?

A. 암호화된 AMI와 스냅샷을 공개적으로 사용할 수 있도록 설정합니다. 키 정책을 수정하여 MSP 파트너의 AWS 계정에서 키를 사용할 수 있도록 허용합니다.
B. AMI의 launchPermission 속성을 수정합니다. AMI를 MSP 파트너의 AWS 계정과만 공유합니다. 키 정책을 수정하여
MSP 파트너의 AWS 계정에서 키를 사용할 수 있도록 허용합니다.
C. AMI의 launchPermission 속성을 수정합니다. AMI를 MSP 파트너의 AWS 계정과만 공유합니다. 암호화를 위해 MSP 파트너가 소유한 새 KMS 키를 신뢰하도록 키 정책을 수정합니다.
D. 소스 계정에서 MSP 파트너의 AWS 계정에 있는 Amazon S3 버킷으로 AMI를 내보냅니다. MSP 파트너가 소유한 새 KMS 키로 S3 버킷을 암호화합니다.
MSP 파트너의 AWS 계정에 AMI를 복사하고 실행합니다.

AMI는:
launchPermission 수정해서
특정 AWS 계정에만 공유 가능

공개(public)로 만들 필요 없음.

암호화된 AMI 공유하려면:
스냅샷이 사용하는 KMS key에
대상 계정이 접근 가능해야 함

정답 : B

## Q4(pdf Q#100)
한 회사의 컨테이너화된 애플리케이션이 Amazon EC2 인스턴스에서 실행됩니다. 이 애플리케이션은 다른 비즈니스 애플리케이션과 통신하기 전에 보안 인증서를 다운로드해야 합니다.
이 회사는 인증서를 거의 실시간으로 암호화 및 복호화할 수 있는 매우 안전한 솔루션을 원합니다.
또한, 암호화된 데이터는 고가용성 스토리지에 저장해야 합니다.
다음 중 운영 오버헤드가 가장 적은 솔루션은 무엇입니까?

A. 암호화된 인증서용 AWS Secrets Manager 비밀 키를 생성합니다. 필요에 따라 인증서를 수동으로 업데이트합니다. 세분화된 IAM 액세스를 사용하여 데이터 액세스를 제어합니다.
B. Python 암호화 라이브러리를 사용하여 암호화 작업을 수신하고 수행하는 AWS Lambda 함수를 생성합니다. 이 함수를 Amazon S3 버킷에 저장합니다.
C. AWS Key Management Service(AWS KMS) 고객 관리형 키를 생성합니다. EC2 역할이 암호화 작업에 KMS 키를 사용할 수 있도록 허용합니다.
암호화된 데이터를 Amazon S3에 저장합니다.
D. AWS Key Management Service(AWS KMS) 고객 관리형 키를 생성합니다. EC2 역할이 암호화 작업에 KMS 키를 사용할 수 있도록 허용합니다.
암호화된 데이터는 Amazon Elastic Block Store(Amazon EBS) 볼륨에 저장합니다.

KMS customer managed key 생성
EC2 IAM Role에 KMS 사용 권한 부여
데이터 암호화/복호화
암호화된 데이터 S3 저장

정답 : C

## Q5(pdf Q#106)

한 회사가 기밀 데이터를 Amazon S3에 저장할 준비를 하고 있습니다. 규정 준수를 위해 데이터는 저장 시 암호화되어야 합니다. 암호화 키 사용 내역은 감사 목적으로 기록되어야 하며, 키는 매년 교체해야 합니다.
이러한 요구 사항을 충족하고 운영 효율성이 가장 높은 솔루션은 무엇입니까?

A. 고객 제공 키를 사용한 서버 측 암호화(SSE-C)
B. Amazon S3 관리형 키를 사용한 서버 측 암호화(SSE-S3)
C. AWS KMS 키를 사용한 서버 측 암호화(SSE-KMS) 및 수동 교체
D. AWS KMS 키를 사용한 서버 측 암호화(SSE-KMS) 및 자동 교체

S3 → SSE-KMS 사용
KMS Customer Managed Key
Automatic Key Rotation 활성화

S3
→ SSE-KMS
→ KMS CMK
→ Automatic rotation ON
→ CloudTrail 로그 자동 기록

정답 : D

## Q6(pdf Q#119)
한 글로벌 기업이 Amazon API Gateway를 사용하여 us-east-1 리전과 ap-southeast-2 리전의 로열티 클럽 사용자를 위한 REST API를 설계하고 있습니다.
솔루션 아키텍트는 여러 계정에 걸쳐 있는 이러한 API Gateway 관리형 REST API를 SQL 인젝션 및 크로스 사이트 스크립팅 공격으로부터 보호하는 솔루션을 설계해야 합니다.
다음 중 관리 노력이 가장 적게 드는 솔루션은 무엇입니까?

A. 두 리전 모두에 AWS WAF를 설정하고, 리전별 웹 ACL을 API 스테이지와 연결합니다.
B. 두 리전 모두에 AWS Firewall Manager를 설정하고, AWS WAF 규칙을 중앙에서 구성합니다.
C. 두 리전 모두에 AWS Shield를 설정하고, 리전별 웹 ACL을 API 스테이지와 연결합니다.
D. 한 리전에만 AWS Shield를 설정하고, 리전별 웹 ACL을 API 스테이지와 연결합니다.

Firewall Manager 사용
중앙에서 WAF 정책 정의
모든 계정/리전에 자동 적용

AWS WAF는:
SQL injection rule
XSS rule
Managed rule group 제공
API Gateway와 직접 연결 가능

정답 : B

## Q7(pdf Q#121)
한 회사가 AWS에서 온라인 트랜잭션 처리(OLTP) 워크로드를 실행하고 있습니다. 이 워크로드는 다중 가용 영역(Multi-AZ) 배포 환경에서 암호화되지 않은 Amazon RDS DB 인스턴스를 사용합니다.
이 인스턴스에서 매일 데이터베이스 스냅샷이 생성됩니다.
향후 데이터베이스와 스냅샷이 항상 암호화되도록 하려면 솔루션 아키텍트는 어떻게 해야 할까요?

A. 최신 DB 스냅샷의 복사본을 암호화합니다. 암호화된 스냅샷을 복원하여 기존 DB 인스턴스를 교체합니다.
B. 새로운 암호화된 Amazon Elastic Block Store(Amazon EBS) 볼륨을 생성하고 스냅샷을 해당 볼륨에 복사합니다. DB 인스턴스에서 암호화를 활성화합니다.
C. 스냅샷을 복사하고 AWS Key Management Service(AWS KMS)를 사용하여 암호화를 활성화합니다. 암호화된 스냅샷을 기존 DB 인스턴스에 복원합니다.
D. AWS Key Management Service(AWS KMS) 관리 키(SSE-KMS)를 사용하여 서버 측 암호화로 암호화된 Amazon S3 버킷에 스냅샷을 복사합니다.

RDS 암호화는 생성 시에만 설정 가능

이미 생성된:

Unencrypted DB
→ Encryption 직접 활성화 불가

최신 스냅샷 복사
복사할 때 KMS로 암호화
암호화된 스냅샷으로 새 RDS 인스턴스 생성
기존 인스턴스 교체

결과:
새 DB 암호화됨
이후 스냅샷도 자동 암호화
Multi-AZ 그대로 가능

정답 : A

## Q8(pdf Q#165)
솔루션 아키텍트는 Amazon CloudFront와 Amazon S3 오리진을 사용하여 정적 웹사이트를 저장하는 솔루션을 설계해야 합니다. 회사의 보안 정책에 따라 모든 웹사이트 트래픽은 AWS WAF를 통해 검사되어야 합니다.
솔루션 아키텍트는 이러한 요구 사항을 어떻게 준수해야 할까요?

A. AWS WAF의 ARN(Amazon Resource Name)에서만 들어오는 요청을 허용하도록 S3 버킷 정책을 구성합니다.
B. Amazon CloudFront가 S3 오리진에서 콘텐츠를 요청하기 전에 모든 수신 요청을 AWS WAF로 전달하도록 구성합니다.
C. Amazon CloudFront IP 주소만 Amazon S3에 액세스할 수 있도록 보안 그룹을 구성하고 AWS WAF를 CloudFront에 연결합니다.
D. Amazon CloudFront와 Amazon S3가 OAI(Origin Access Identity)를 사용하여 S3 버킷에 대한 액세스를 제한하도록 구성하고 배포에서 AWS WAF를 활성화합니다.

정답 : D

## Q9(pdf Q#180)
한 회사가 API 기반의 클라우드 통신 플랫폼을 설계하고 있습니다. 이 애플리케이션은 네트워크 로드 밸런서(NLB) 뒤의 Amazon EC2 인스턴스에 호스팅됩니다.
이 회사는 Amazon API Gateway를 사용하여 외부 사용자가 API를 통해 애플리케이션에 액세스할 수 있도록 합니다.
이 회사는 SQL 인젝션과 같은 웹 공격으로부터 플랫폼을 보호하고, 대규모의 정교한 DDoS 공격을 탐지하고 완화하고자 합니다.
다음 중 가장 강력한 보호 기능을 제공하는 솔루션 조합은 무엇입니까? (두 가지를 선택하십시오.)

A. AWS WAF를 사용하여 NLB를 보호합니다.
B. AWS Shield Advanced를 NLB와 함께 사용합니다.
C. AWS WAF를 사용하여 Amazon API Gateway를 보호합니다.
D. Amazon GuardDuty와 AWS Shield Standard를 함께 사용합니다.
E. AWS Shield Standard와 Amazon API Gateway를 함께 사용합니다.

Shield Advanced는:
L3/L4 보호
정교한 DDoS 방어
비용 보호
24/7 DRT 지원

대규모 정교한 DDoS → Advanced 필요

API Gateway는:
L7 레벨
SQL injection 방어 필요

WAF는:
Managed rule group 제공
SQLi, XSS 방어

정답 : B , C

## Q10(pdf Q#189)
한 회사가 계약 문서를 보관해야 합니다. 계약 기간은 5년입니다. 이 5년 동안 회사는 문서가 덮어쓰이거나 삭제되지 않도록 해야 합니다.
또한, 저장된 문서는 암호화하고 암호화 키는 매년 자동으로 교체해야 합니다.
솔루션 아키텍트는 운영 오버헤드를 최소화하면서 이러한 요구 사항을 충족하기 위해 어떤 조치를 취해야 할까요? (두 가지를 선택하세요.)

A. 문서를 Amazon S3에 저장하고, S3 Object Lock을 거버넌스 모드로 사용합니다.
B. 문서를 Amazon S3에 저장하고, S3 Object Lock을 규정 준수 모드로 사용합니다.
C. Amazon S3 관리형 암호화 키(SSE-S3)를 사용하여 서버 측 암호화를 수행하고, 키 교체를 구성합니다.
D. AWS Key Management Service(AWS KMS) 고객 관리형 키를 사용하여 서버 측 암호화를 수행하고, 키 교체를 구성합니다.
E. AWS Key Management Service(AWS KMS) 고객 제공(가져온) 키를 사용하여 서버 측 암호화를 수행하고, 키 교체를 구성합니다.

Compliance
루트 계정도 삭제 불가
법적 보관 요구 충족
WORM (Write Once Read Many)

AWS Key Management Service
SSE-KMS + Customer Managed Key:

암호화 가능
CloudTrail로 키 사용 로그
Automatic rotation 지원
연 1회 자동 회전

정답 : B , D

## Q11(pdf Q#202)
한 회사가 데이터를 Amazon S3 버킷으로 이전할 계획입니다. 데이터는 S3 버킷에 저장될 때 암호화되어야 합니다. 또한,
암호화 키는 매년 자동으로 교체되어야 합니다.
다음 중 운영 오버헤드가 가장 적은 솔루션은 무엇일까요?

A. 데이터를 S3 버킷으로 이동합니다. Amazon S3 관리형 암호화 키(SSE-S3)를 사용하여 서버 측 암호화를 사용합니다. SSE-S3 암호화 키의 내장 키
교체 동작을 사용합니다.
B. AWS Key Management Service(AWS KMS) 고객 관리형 키를 생성합니다. 자동 키 교체를 활성화합니다. S3 버킷의 기본
암호화 동작을 고객 관리형 KMS 키를 사용하도록 설정합니다. 데이터를 S3 버킷으로 이동합니다.
C. AWS Key Management Service(AWS KMS) 고객 관리형 키를 생성합니다. S3 버킷의 기본 암호화 동작을 고객 관리형 KMS 키를 사용하도록 설정합니다.
데이터를 S3 버킷으로 이동합니다. 매년 수동으로 KMS 키를 교체합니다.
D. 데이터를 S3 버킷으로 이동하기 전에 고객 키 자료로 데이터를 암호화합니다. AWS 키 관리 서비스(AWS KMS) 키를 키 자료 없이 생성합니다.
고객 키 자료를 KMS 키로 가져옵니다. 자동 키 순환을 활성화합니다.

KMS Customer Managed Key 생성
Automatic Key Rotation 활성화
S3 bucket default encryption을 해당 KMS 키로 설정
데이터 업로드

결과:

저장 시 자동 암호화
매년 자동 회전
CloudTrail 로깅
운영 부담 최소

정답 : B

## Q12(pdf Q#234)
한 회사가 새로운 웹 기반 고객 관계 관리(CRM) 애플리케이션을 구축하고 있습니다. 이 애플리케이션은 Amazon EBS(Amazon Elastic Block Store) 볼륨을 기반으로 하는 여러 Amazon EC2 인스턴스를 사용하며, 이 인스턴스들은 Application Load Balancer(ALB)에 의해 지원됩니다. 또한 Amazon Aurora 데이터베이스도 사용합니다. 애플리케이션에 사용되는 모든 데이터는 저장 시와 전송 시 모두 암호화되어야 합니다.
이러한 요구 사항을 충족하는 솔루션은 무엇일까요?

A. ALB에서 AWS KMS(AWS Key Management Service) 인증서를 사용하여 전송 중인 데이터를 암호화합니다. AWS ACM(AWS Certificate Manager)을 사용하여 EBS 볼륨과 Aurora 데이터베이스 스토리지를 저장 시 암호화합니다.
B. AWS 루트 계정으로 AWS Management Console에 로그인합니다. 회사 암호화 인증서를 업로드합니다. 루트 계정에서
계정의 모든 저장 및 전송 데이터에 대한 암호화를 활성화하는 옵션을 선택합니다.
C. AWS KMS(AWS Key Management Service)를 사용하여 EBS 볼륨과 Aurora 데이터베이스 스토리지를 저장 시 암호화합니다. AWS 인증서 관리자(ACM) 인증서를 ALB에 연결하여 전송 중인 데이터를 암호화합니다.
D. BitLocker를 사용하여 저장된 모든 데이터를 암호화합니다. 회사 TLS 인증서 키를 AWS 키 관리 서비스(AWS KMS)로 가져옵니다.
KMS 키를 ALB에 연결하여 전송 중인 데이터를 암호화합니다.

AWS Key Management Service
KMS 사용:
EBS 암호화
Aurora 암호화
Customer Managed Key 사용 가능
자동 키 회전 가능

정답 : C

## Q13(pdf Q#336)
한 회사가 Amazon Aurora MySQL DB 클러스터를 스토리지로 사용하는 다계층 웹 애플리케이션을 호스팅하고 있습니다. 애플리케이션 계층은
Amazon EC2 인스턴스에서 호스팅됩니다. 회사의 IT 보안 지침에 따라 데이터베이스 자격 증명은 암호화되어야 하며 14일마다 갱신되어야 합니다.
솔루션 아키텍트는 최소한의 운영 노력으로 이 요구 사항을 충족하기 위해 무엇을 해야 할까요?

A. 새로운 AWS Key Management Service(AWS KMS) 암호화 키를 생성합니다. AWS Secrets Manager를 사용하여 KMS 키와 적절한 자격 증명을 사용하는 새 시크릿을 생성합니다.
이 시크릿을 Aurora DB 클러스터와 연결합니다. 14일의 사용자 지정 갱신 주기를 구성합니다.
B. AWS Systems Manager 파라미터 스토어에 두 개의 파라미터를 생성합니다. 하나는 문자열 파라미터로 사용자 이름을 저장하고, 다른 하나는 SecureString 유형을 사용하는 암호 파라미터입니다.
암호 파라미터에 AWS Key Management Service(AWS KMS) 암호화를 선택하고 이러한 파라미터를
애플리케이션 계층에 로드합니다. 14일마다 암호를 갱신하는 AWS Lambda 함수를 구현합니다.
C. 자격 증명이 포함된 파일을 AWS Key Management Service(AWS KMS)로 암호화된 Amazon Elastic File System(Amazon EFS) 파일 시스템에 저장합니다.
EFS 파일 시스템을 애플리케이션 계층의 모든 EC2 인스턴스에 마운트합니다. 파일 시스템의 파일에 대한 액세스를 제한하여
애플리케이션은 파일을 읽을 수 있고, 슈퍼 사용자만 파일을 수정할 수 있도록 합니다. 14일마다 Aurora의 키를 갱신하고 새 자격 증명을 파일에 기록하는 AWS Lambda 함수를 구현합니다.
D. 자격 증명이 포함된 파일을 AWS Key Management Service(AWS KMS)로 암호화된 Amazon S3 버킷에 저장하고, 애플리케이션은 이 버킷에서 자격 증명을 로드합니다.
올바른 자격 증명이 사용되도록 정기적으로 파일을 애플리케이션에 다운로드합니다. 14일마다 Aurora 자격 증명을 갱신하고 이 자격 증명을 S3 버킷의 파일에 업로드하는 AWS Lambda 함수를 구현합니다.

구성:

KMS 키 생성
Secrets Manager에 DB 자격 증명 저장
Aurora DB 클러스터와 연결
Rotation 주기 14일 설정

결과:
암호화
자동 회전
Aurora 네이티브 통합
운영 최소

정답 : A

## Q14(pdf Q#349)
한 회사가 ap-southeast-3 리전의 Amazon Aurora PostgreSQL 데이터베이스에 기밀 데이터를 저장합니다. 이 데이터베이스는 AWS KMS(AWS Key Management Service) 고객 관리 키로 암호화되어 있습니다.
이 회사는 최근 인수되었으며, 인수 회사의 ap-southeast-3 리전에 있는 AWS 계정과 데이터베이스 백업을 안전하게 공유해야 합니다.
솔루션 아키텍트는 이러한 요구 사항을 충족하기 위해 무엇을 해야 할까요?

A. 데이터베이스 스냅샷을 생성합니다. 스냅샷을 암호화되지 않은 새 스냅샷으로 복사합니다. 새 스냅샷을 인수 회사의
AWS 계정과 공유합니다.
B. 데이터베이스 스냅샷을 생성합니다. 인수 회사의 AWS 계정을 KMS 키 정책에 추가합니다. 스냅샷을 인수 회사의
AWS 계정과 공유합니다.
C. 다른 AWS 관리형 KMS 키를 사용하는 데이터베이스 스냅샷을 생성합니다. 인수 회사의 AWS 계정을 KMS 키 별칭에 추가합니다.
스냅샷을 인수 회사의 AWS 계정과 공유합니다.
D. 데이터베이스 스냅샷을 생성합니다. 데이터베이스 스냅샷을 다운로드합니다. 다운로드한 데이터베이스 스냅샷을 Amazon S3 버킷에 업로드합니다. S3 버킷 정책을 업데이트하여 인수 회사의 AWS 계정에서 접근할 수 있도록 허용합니다.

절차:
DB snapshot 생성
KMS key policy 수정 → 대상 계정 허용
Snapshot 공유

결과:
암호화 유지
안전한 계정 간 공유
같은 리전이므로 복잡한 복사 필요 없음

정답 : B

## Q15(pdf Q#359)
병원에서 환자 기록을 Amazon S3 버킷에 저장해야 합니다. 병원의 규정 준수 팀은 모든 보호 대상 의료 정보(PHI)가 전송 중 및 저장 시 암호화되도록 해야 합니다. 또한 규정 준수 팀은 저장 데이터에 대한 암호화 키를 관리해야 합니다.
이러한 요구 사항을 충족하는 솔루션은 무엇입니까?

A. AWS Certificate Manager(ACM)에서 공개 SSL/TLS 인증서를 생성합니다. 해당 인증서를 Amazon S3와 연결합니다. 각 S3 버킷의 기본 암호화를 AWS KMS 키(SSE-KMS)를 사용한 서버 측 암호화로 구성합니다. 규정 준수 팀에 KMS 키 관리 권한을 부여합니다.
B. S3 버킷 정책에 aws:SecureTransport 조건을 사용하여 HTTPS(TLS)를 통한 암호화된 연결만 허용합니다. 각 S3 버킷의 기본 암호화를 S3 관리형 암호화 키(SSE-S3)를 사용한 서버 측 암호화로 구성합니다. 규정 준수 팀에 SSE-S3 키 관리 권한을 부여합니다.
C. S3 버킷 정책에 aws:SecureTransport 조건을 사용하여 HTTPS(TLS)를 통한 암호화된 연결만 허용합니다. 각 S3 버킷의 기본 암호화를 AWS KMS 키(SSE-KMS)를 사용한 서버 측 암호화로 구성합니다. 규정 준수 팀에 KMS 키 관리를 할당합니다.
D. S3 버킷 정책에 aws:SecureTransport 조건을 사용하여 HTTPS(TLS)를 통한 암호화된 연결만 허용합니다. Amazon Macie를 사용하여
Amazon S3에 저장된 민감한 데이터를 보호합니다. 규정 준수 팀에 Macie 관리를 할당합니다.

정답 : C


## Q16(pdf Q#396)
한 회사가 AWS에 자체 관리형 DNS 서비스를 구축했습니다. 이 솔루션은 다음과 같은 요소로 구성됩니다.
• 여러 AWS 리전에 분산된 Amazon EC2 인스턴스
• AWS 글로벌 액셀러레이터의 표준 액셀러레이터 엔드포인트
이 회사는 DDoS 공격으로부터 솔루션을 보호하고자 합니다.
솔루션 아키텍트는 이 요구 사항을 충족하기 위해 무엇을 해야 할까요?

A. AWS Shield Advanced를 구독하고, 액셀러레이터를 보호 대상 리소스로 추가합니다.
B. AWS Shield Advanced를 구독하고, EC2 인스턴스를 보호 대상 리소스로 추가합니다.
C. 속도 기반 규칙이 포함된 AWS WAF 웹 ACL을 생성하고, 해당 웹 ACL을 액셀러레이터와 연결합니다.
D. 속도 기반 규칙이 포함된 AWS WAF 웹 ACL을 생성하고, 해당 웹 ACL을 EC2 인스턴스와 연결합니다.

Shield 종류:

종류	             특징
Shield Standard	    기본 보호 (자동)
Shield Advanced	    정교한 대규모 DDoS 보호

Self-managed DNS → 공격 표적 가능성 높음
→ Advanced가 적절

Global Accelerator:
Anycast IP 사용
AWS Edge 네트워크 진입점
-> Accelerator 자체를 보호해야 함

정답 : A

## Q17(pdf Q#535)
한 회사가 워크로드를 위해 Amazon Elastic Kubernetes Service(Amazon EKS) 클러스터를 구축하고 있습니다. Amazon EKS에 저장되는 모든 시크릿은 Kubernetes etcd 키-값 저장소에서 암호화되어야 합니다.
이러한 요구 사항을 충족하는 솔루션은 무엇입니까?

A. 새 AWS Key Management Service(AWS KMS) 키를 생성합니다. AWS Secrets Manager를 사용하여 Amazon EKS의 모든 시크릿을 관리, 순환 및 저장합니다.
EKS
B. 새 AWS Key Management Service(AWS KMS) 키를 생성합니다. Amazon EKS 클러스터에서 Amazon EKS KMS 시크릿 암호화를 활성화합니다.
C. 기본 옵션으로 Amazon EKS 클러스터를 생성합니다. Amazon Elastic Block Store(Amazon EBS) 컨테이너 스토리지 인터페이스(CSI) 드라이버를 추가 기능으로 사용합니다.
D. /aws/ebs 별칭으로 새 AWS Key Management Service(AWS KMS) 키를 생성합니다. 계정에 대해 기본 Amazon Elastic Block Store(Amazon EBS) 볼륨 암호화를 활성화합니다.

AWS Key Management Service

구성:
KMS key 생성
EKS cluster에 KMS encryption 활성화

결과:
Kubernetes Secret이 etcd에 저장될 때 암호화
AWS KMS 기반 envelope encryption
완전 관리형

정답 : B