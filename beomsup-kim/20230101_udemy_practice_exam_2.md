

## 총평

문제 정답율 27% 문제 그냥 푸는 식으로 했는데 안되겠고 천천히 개념익히는데 포인트 맞추자

## 질문 1:

한 IT 회사가 공급망 관리 애플리케이션을 구축하는 고객 프로젝트를 진행 중입니다. 애플리케이션의 웹 티어는 Amazon EC2 인스턴스에서 실행되고 데이터베이스 티어는 Amazon RDS MySQL에서 실행됩니다. 베타 테스트를 위해 현재 모든 리소스는 단일 가용성 영역(AZ)에 배포되어 있습니다. 개발팀은 출시 전에 애플리케이션 가용성을 개선하고자 합니다.
웹 애플리케이션의 모든 최종 사용자가 미국에 있다고 가정할 때, 다음 중 가장 리소스 효율적인 솔루션은 무엇인가요?

- A. 웹 티어 Amazon EC2 인스턴스를 두 개의 가용성 영역(AZ)에 배포하고, 그 뒤에 Elastic Load Balancer를 배치합니다. 읽기 복제본 구성으로 Amazon RDS MySQL 데이터베이스를 배포합니다
- B. 웹 티어 Amazon EC2 인스턴스를 두 개의 가용성 영역(AZ)에 배포하고, 그 뒤에 Elastic Load Balancer를 배치합니다. 다중 AZ 구성으로 Amazon RDS MySQL 데이터베이스 배포
- C. 웹 티어 Amazon EC2 인스턴스를 두 개의 리전에 Elastic Load Balancer 뒤에 배포합니다. 읽기 복제본 구성으로 Amazon RDS MySQL 데이터베이스 배포
- D. 웹 티어 Amazon EC2 인스턴스를 두 개의 리전에 Elastic Load Balancer 뒤에 배포합니다. 다중 AZ 구성으로 Amazon RDS MySQL 데이터베이스 배포

정답: B

A: 읽기 복제본은 그말대로 읽기용이라 장애시 복구 안됨 = 고가용성 X, 확장성 O
C,D: Elastic Load Balancer 는 리전을 컨트롤 하지 못함

## 질문 3

회사에는 약 2시간 동안 실행되는 월별 빅데이터 워크로드가 있으며, 이 워크로드는 다양한 크기의 여러 서버에 다양한 수의 CPU로 효율적으로 분산될 수 있습니다. 이 워크로드를 위한 솔루션은 서버 장애를 견딜 수 있어야 합니다.
이 워크로드에 가장 비용 최적화된 솔루션은 무엇일까요?

- A. 예약 인스턴스(RI)에서 워크로드 실행
- B. 스팟 플릿(Fleet)에서 워크로드 실행
- C. 스팟 인스턴스에서 워크로드 실행
- D. 전용 호스트에서 워크로드 실행

정답: B

가격: 예약 인스턴스 < 스팟 인스턴스 (경매)
플릿: 스팟 인스턴스 관리 개념
전용 호스트: 전용 자리 = 비쌈

## 질문 4

개발자는 AWS 계정 A에서 AWS 람다 함수를 구현해야 하며, 이 함수는 AWS 계정 B의 Amazon S3(Amazon Simple Storage Service) 버킷에 액세스합니다.
솔루션 아키텍트로서 이 요구 사항을 충족하기 위해 다음 중 어떤 것을 권장하시겠습니까?

- A. Amazon S3 버킷에 대한 액세스 권한을 부여하는 AWS Lambda 함수에 대한 IAM 역할을 만듭니다. IAM 역할을 Lambda 함수의 실행 역할로 설정하면 AWS Lambda 함수에 Amazon S3 버킷에 대한 계정 간 액세스 권한이 부여됩니다
- B. AWS Lambda는 AWS 계정 전반의 리소스에 액세스할 수 없습니다. ID 페더레이션을 사용하여 Lambda의 이러한 제한을 해결하세요
- C. Amazon S3 버킷 소유자는 버킷을 공개로 설정하여 다른 AWS 계정의 AWS Lambda 함수에서 액세스할 수 있도록 해야 합니다
- D. Amazon S3 버킷에 대한 액세스 권한을 부여하는 AWS Lambda 함수에 대한 IAM 역할을 생성합니다. IAM 역할을 AWS Lambda 함수의 실행 역할로 설정합니다. 버킷 정책에서 AWS Lambda 함수의 실행 역할에 대한 액세스 권한도 부여하는지 확인하세요

정답: D

Lambda 함수 생성 IAM 역할이 동일한 AWS 계정에 있는 경우 Amazon S3 권한이 묵시적으로 부여됨 하지만 차단이 되어 있을 수 있음으로 확인이 필요, A는 권한 확인을 넘겼음으로 오답

B, C: 대놓고 말이 안됨, 권한은 아주 중요한데 쉽게 오픈 해줘서는 안됨

## 질문 5: 
```
{
    "Version":"2012-10-17",
    "Id":"EC2TerminationPolicy",
    "Statement":[{
            "Effect":"Deny",
            "Action":"ec2:*",
            "Resource":"*",
            "Condition":{
                "StringNotEquals":{
                    "ec2:Region":"us-west-1"
                }}},{
            "Effect":"허용",
            "Action":"ec2:TerminateInstances",
            "Resource":"*",
            "Condition":{
                "IpAddress":{
                    "aws:SourceIp":"10.200.200.0/24"
                }}}]}
```

다음 중 올바른 옵션은 무엇인가요? IAM 사용자 그룹에 속한~

- A. 사용자는 EC2 인스턴스의 IP 주소가 10.200.200.200인 경우 us-west-1 리전에서 Amazon EC2 인스턴스를 종료할 수 있습니다
- B. 사용자는 사용자의 소스 IP가 10.200.200.200인 경우 us-west-1 리전을 제외한 모든 리전에 속한 Amazon EC2 인스턴스를 종료할 수 있습니다
- C. 사용자는 사용자의 소스 IP가 10.200.200.200인 경우 us-west-1 리전의 Amazon EC2 인스턴스를 종료할 수 없습니다
- D. 사용자는 사용자의 소스 IP가 10.200.200.200인 경우 us-west-1 리전에서 Amazon EC2 인스턴스를 종료할 수 있습니다


정답: D

Deny - StringNotEquals - us-west-1 = us-west-1 이 아니면 거부됨

## 질문 6:

애플리케이션의 성능과 보안을 개선하기 위해 한 회사의 엔지니어링 팀은 애플리케이션 로드 밸런서를 사용자 정의 오리진으로 사용하여 Amazon CloudFront 배포를 생성했습니다. 또한 이 팀은 Amazon CloudFront 배포와 함께 AWS 웹 애플리케이션 방화벽(AWS WAF)을 설정했습니다. 이 회사의 보안팀은 특정 IP 주소에서 Amazon EC2 인스턴스에 저장된 중요한 데이터를 훔치기 위한 악성 공격이 급증하는 것을 발견했습니다.
솔루션 설계자로서 공격을 막기 위해 다음 중 어떤 조치를 권장하시겠습니까?

- A. AWS 지원팀에 티켓을 생성하여 악성 IP에 대한 조치를 취하세요
- B. AWS WAF에서 IP 일치 조건을 생성하여 악성 IP 주소를 차단합니다
- C. 각 인스턴스와 연결된 보안 그룹에서 악성 IP에 대한 거부 규칙을 만듭니다
- D. 각 인스턴스와 연결된 네트워크 액세스 제어 목록(네트워크 ACL)에서 악성 IP에 대한 거부 규칙을 만듭니다

정답: B

Amazon CloudFront: CDN

WAF(Web Application Firewall)

## 질문 7

한 IT 회사는 프로젝트별 작업을 완료하기 위해 동일한 계정 내의 특정 사용자에게 Amazon S3(Amazon Simple Storage Service) 버킷 액세스를 제공합니다. 비즈니스 요구 사항이 변화함에 따라 계정 간 S3 액세스 요청도 매달 증가하고 있습니다. 이 회사는 Amazon S3 버킷에 저장된 데이터에 대해 사용자 수준은 물론 계정 수준의 액세스 권한도 제공할 수 있는 솔루션을 찾고 있습니다.

솔루션 아키텍트로서 다음 중 이 사용 사례에 가장 최적화된 액세스 제어 방법으로 제안하고 싶은 것은 무엇인가요?

- A. Amazon S3 버킷 정책 사용
- B. 보안 그룹 사용
- C. ID 및 액세스 관리(IAM) 정책 사용
- D. ACL(액세스 제어 목록) 사용

정답: A

  Amazon S3의 버킷 정책을 사용하여 단일 버킷 내의 일부 또는 모든 개체에 대한 권한을 추가하거나 거부할 수 있습니다. 정책을 사용자, 그룹 또는 Amazon S3 버킷에 연결하여 중앙 집중식으로 권한을 관리할 수 있습니다. 버킷 정책을 통해 AWS 계정 또는 다른 AWS 계정 내의 사용자에게 Amazon S3 리소스에 대한 액세스 권한을 부여할 수 있습니다.

  특정 조건에 따라 특정 리소스에 대한 액세스를 추가로 제한할 수 있습니다. 예를 들어 요청 시간(날짜 조건), 요청이 SSL을 사용하여 전송되었는지 여부(부울 조건), 요청자의 IP 주소(IP 주소 조건) 또는 요청자의 클라이언트 애플리케이션(문자열 조건)에 따라 액세스를 제한할 수 있습니다. 이러한 조건을 식별하기 위해 정책 키를 사용합니다

  ID 및 액세스 관리(IAM) 정책 사용 - AWS IAM을 사용하면 많은 직원이 있는 조직에서 단일 AWS 계정으로 여러 사용자를 생성하고 관리할 수 있습니다. IAM 정책은 사용자에게 연결되므로 AWS 계정 아래 사용자의 버킷 또는 오브젝트 액세스 권한을 중앙에서 제어할 수 있습니다. IAM 정책을 사용하면 자신의 AWS 계정 내의 사용자에게만 Amazon S3 리소스에 액세스할 수 있는 권한을 부여할 수 있습니다. 따라서 현재 요구 사항에 적합한 선택이 아닙니다.

  ACL(Network Access Control List) 사용 - Amazon S3 내에서 ACL을 사용하여 버킷 또는 개체에 대한 읽기 또는 쓰기 액세스 권한을 사용자 그룹에 부여할 수 있습니다. ACL을 사용하면 특정 사용자가 아닌 다른 AWS 계정에만 Amazon S3 리소스에 대한 액세스 권한을 부여할 수 있습니다. 따라서 현재 요구 사항에 적합한 선택이 아닙니다.

  보안 그룹 사용 - 보안 그룹은 Amazon EC2 인스턴스에 대한 가상 방화벽 역할을 하여 수신 및 발신 트래픽을 제어합니다. Amazon S3는 보안 그룹을 지원하지 않으며, 이 옵션은 단지 방해 요소로 작용할 뿐입니다.









## 질문 8

AWS 스노우볼을 사용하여 온프레미스 백업을 AWS의 장기 아카이브 계층으로 옮기고자 합니다. 어떤 솔루션이 가장 큰 비용 절감 효과를 제공하나요?

AWS 스노우볼 작업을 생성하고 Amazon S3~

- A. 버킷을 대상으로 합니다. 라이프사이클 정책을 생성하여 이 데이터를 같은 날에 Amazon S3     
       Glacier 딥 아카이브로 전환합니다
- B. 버킷을 대상으로 합니다. 라이프사이클 정책을 생성하여 이 데이터를 같은 날에 Amazon S3 
       Glacier로 전환합니다
- C. 글래시어 볼트를 타겟팅하세요
- D. Glacier 딥 아카이브 볼트를 타겟팅하세요









정답: A

스노우볼 작업 = 큰데이터(페타바이트 수준) AWS로 보내는 최고의 선택, S3 Glacier로 직접 전송 불가

Amazon S3 Glacier, Amazon S3 Glacier 딥 아카이브 = 저장 최고로 좋음

Amazon S3 Glacier < Amazon S3 Glacier 딥 아카이브 = 더 쌈














## 질문 9

한 금융 서비스 회사는 서버리스 방식으로 처리한 다음 다운스트림 분석을 위해 내구성 있게 저장할 수 있는 모든 로그 파일(시스템 로그, 애플리케이션 로그, 데이터베이스 로그 등으로 구성)에 대한 단일 로그 처리 모델을 원합니다. 로그 데이터의 처리량에 맞춰 자동으로 확장되고 지속적인 관리가 필요 없는 AWS 관리형 서비스를 사용하고자 합니다.

솔루션 설계자로서 이 문제를 해결하기 위해 다음 중 어떤 AWS 서비스를 추천하시겠습니까?

- A. AWS 람다
- B. 아마존 키네시스 데이터 스트림
- C. Amazon EMR
- D. 아마존 키네시스 데이터 파이어호스

정답: D
Amazon Kinesis Data Firehose는 스트리밍 데이터를 데이터 레이크, 데이터 저장소 및 분석 도구에 안정적으로 로드하는 가장 쉬운 방법입니다. 스트리밍 데이터를 캡처, 변환, Amazon S3, Amazon Redshift, Amazon Elasticsearch Service, Splunk로 로드할 수 있어 현재 사용 중인 기존 비즈니스 인텔리전스 도구와 대시보드로 실시간에 가까운 분석을 할 수 있습니다. 데이터 처리량에 맞춰 자동으로 확장되는 완전 관리형 서비스로, 지속적인 관리가 필요하지 않습니다. 따라서 이것이 올바른 옵션입니다.
 
경유 - https://aws.amazon.com/kinesis/data-firehose/


A: 람다는 서버리스 코드 실행용, 단위가 크면 할 수 없음
B: 데이터 스트림 서비스 이나 지속적 관리가 필요함 지문에 자동이라는 말이 붙어 오답
C. 빅 데이터 처리, 분석용이나 지속적으로 인프라 관리가 필요함





# 문제 11

한 전자상거래 애플리케이션은 데이터베이스에 Amazon Aurora Multi-AZ 배포를 사용합니다. 엔지니어링 팀은 성능 메트릭을 분석하는 동안 데이터베이스 읽기가 높은 입출력(I/O)을 유발하고 데이터베이스에 대한 쓰기 요청에 지연 시간을 추가한다는 사실을 발견했습니다. AWS 공인 솔루션 아키텍트 어소시에이트로서 읽기 요청과 쓰기 요청을 분리하려면 어떻게 해야 하나요?

- A. Amazon Aurora 데이터베이스에서 읽기 캐싱 활성화
- B. Multi-AZ 대기 인스턴스에서 읽도록 애플리케이션을 구성합니다
- C. 읽기 복제본을 설정하고 적절한 엔드포인트를 사용하도록 애플리케이션을 수정합니다
- D. 다른 Amazon Aurora 데이터베이스를 프로비저닝하고 읽기 복제본으로 기본 데이터베이스에 연결합니다

정답: C

A, B. 읽기 캐싱, 대기 인스턴스는 존재하는 개념이 아님
C. 다른 Amazon Aurora 데이터베이스를 프로비저닝 후 읽기 복제본으로 연결 불가



## 질문 12

HTTP 애플리케이션은 자동 확장 그룹에 배포되고, HTTPS 엔드포인트를 제공하는 애플리케이션 로드 밸런서(ALB)에서 액세스할 수 있으며, Amazon RDS에서 관리하는 PostgreSQL 데이터베이스에 액세스합니다.
보안 그룹을 어떻게 구성해야 하나요?

- A. Amazon EC2 인스턴스의 보안 그룹에는 포트 5432에 있는 Amazon RDS 데이터베이스의 보안 그룹으로부터의 인바운드 규칙이 있어야 합니다
- B. Amazon EC2 인스턴스의 보안 그룹에는 포트 80에 있는 애플리케이션 로드 밸런서의 보안 그룹으로부터의 인바운드 규칙이 있어야 합니다
- C. Amazon RDS의 보안 그룹에는 포트 5432의 자동 확장 그룹에 있는 Amazon EC2 인스턴스의 보안 그룹에서 인바운드 규칙이 있어야 합니다
- D. 애플리케이션 로드 밸런서의 보안 그룹에는 포트 443의 어느 곳에서든 인바운드 규칙이 있어야 합니다
- E. 애플리케이션 로드 밸런서의 보안 그룹에는 포트 80의 어느 곳에서든 인바운드 규칙이 있어야 합니다
- F. Amazon RDS의 보안 그룹에는 포트 80의 자동 확장 그룹에 있는 Amazon EC2 인스턴스의 보안 그룹으로부터의 인바운드 규칙이 있어야 합니다

정답: B,C,D



## 질문 13

한 빅 데이터 컨설팅 회사가 의료 서비스 고객을 위해 Amazon S3에 데이터 레이크를 설정해야 합니다. 데이터 레이크는 원시 영역과 정제된 영역으로 나뉩니다. 규정 준수를 위해 원본 데이터는 최소 5년 동안 보관해야 합니다. 원본 데이터는 원시 영역에 도착한 다음 AWS Glue 기반 추출, 변환, 로드(ETL) 작업을 통해 정제된 영역으로 처리됩니다. 비즈니스 분석가는 Amazon Athena를 사용하여 정제된 영역의 데이터에 대해서만 애드혹 쿼리를 실행합니다. 이 팀은 각 영역에서 매일 1테라바이트의 속도로 데이터가 증가함에 따라 원시 영역과 정제된 영역 모두의 데이터 저장 비용에 대해 우려하고 있습니다.
솔루션 설계자로서 다음 중 가장 비용 최적화된 솔루션으로 추천하고 싶은 것은 무엇인가요? (두 가지 선택)

- A. 1일 후에 원시 영역 데이터를 삭제하는 AWS 람다 함수 기반 작업을 생성합니다
- B. 오브젝트 생성 후 1일이 지나면 정제된 영역 데이터를 Amazon S3 Glacier 딥 아카이브로 전환하도록 수명 주기 정책을 설정합니다
- C. 오브젝트 생성 후 1일이 지나면 원시 영역 데이터를 Amazon S3 Glacier 딥 아카이브로 전환하도록 수명 주기 정책을 설정합니다
- D. AWS Glue ETL 작업을 사용하여 압축된 파일 형식을 사용하여 정제된 영역에 변환된 데이터를 작성합니다
- E. AWS Glue ETL 작업을 사용하여 CSV 형식을 사용하여 정제된 영역에 변환된 데이터를 작성합니다


정답: C,D

C: 원시데이터는 이미 사용했으나 보관해야함, 딥 아카이브로 전환하면 좋음
D: 정제된 영역에 압축된 파일로 저장하겠다는 말

오답:

A: 원시 영역 데이터는 지우면 안됨, 규정 준수상의 이유로 5년 보관필요
B: 정제 = 사용하려고 만든 데이터, S3 Glacier 딥 아카이브 검색시간 12~48시간 걸림
E: CSV는 원 데이터로 저장하겠다는 말과 같음 = 변화 없음

AWS Athena: AWS Athena는 표준 SQL을 사용하여 AWS S3에 저장된 데이터를 분석할 수 있는 대화형 쿼리 서비스입니다, 이 서비스를 사용하면 페타바이트 규모의 데이터를 데이터가 있는 위치에서 간편하고 유연한 방법으로 분석할 수 있습니다,

AWS Glue: AWS Glue는 완전히 관리되는 ETL (추출, 변환, 로드) 서비스로, 데이터를 변환하고 통합하는 데 사용됩니다. Glue는 데이터 카탈로그를 제공하여 다양한 데이터 소스, 테이블, 그리고 그들의 스키마에 대한 메타데이터 정보를 저장하고 관리할 수 있습니다.

AWS Kinesis Data Firehose: Kinesis Data Firehose는 실시간 스트리밍 데이터를 쉽게 로드하고 분석할 수 있도록 설계되었습니다. 이 서비스는 대량의 데이터를 실시간으로 처리하고 분석하는 데 사용됩니다.

데이터 레이크: 데이터 레이크는 조직에서 수집한 정형*·반정형**·비정형*** 데이터를 원시 형태(raw data)로 저장하는 단일한 데이터 저장소


## 질문 14

한 회사가 여러 계정에 여러 개의 Amazon 가상 프라이빗 클라우드(Amazon VPC)를 보유하고 있는데, 이 클라우드들은 스타 네트워크에서 서로 연결되고 AWS 다이렉트 커넥트를 통해 온프레미스 네트워크와 연결되어야 합니다.
어떤 방법을 추천하시나요?

- A. VPC 피어링 연결
- B. 가상 사설 게이트웨이(VGW)
- C. 프라이빗 링크
- D. 트랜짓 게이트웨이

정답: D

트랜짓 게이트웨이: AWS 트랜짓 게이트웨이는 고객이 Amazon VPC(가상 프라이빗 클라우드)와 온프레미스 네트워크를 단일 게이트웨이에 연결할 수 있는 서비스입니다

A: VPC 피어링은 VPC - VPC 끼리 연결하는 것 온프레미스와 연결이 지문에 있으니 오답
B: VGW = *Virtual Private Network  *Gate *Way의 약자로 지문에 VPN에 대한 내용이 없음
C: 프라이빗 링크는 그말대로 비공개임 비공개에 대한 내용이 없음으로 오답