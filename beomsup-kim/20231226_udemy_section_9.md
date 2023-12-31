# 총평

examtopic 문제는 모르는 개념, 단어가 너무 많이 나와서 익숙해 지기 위해서 유데미 퀴즈들을 풀어야겠다고 판단

# 질문 1:

아마존 RDS가 지원하지 않는 데이터베이스를 고르세요.

A. MongoDB
B. MySQL
C. MariaDB
D. Microsoft SQL 서버

정답 1: A

RDS는 MySQL, PostgreSQL, MariaDB, Oracle, MS SQL Server, Amazon Aurora를 지원합니다.


# 질문 2:

한 가용 영역에 재해 상황이 발생하더라도 반드시 MySQL 데이터베이스을 사용할 수 있도록 만들기 위한 새로운 솔루션을 계획하고 있습니다. 무엇을 사용해야 할까요?

A. 읽기 전용 복제본 생성
B. 암호화 활성화
C. 다중 AZ 활성화

정답 2: C

다중 AZ는 전체 AZ가 차단되었을 경우의 재해 복구를 계획하는 데에 도움이 됩니다. 전체 AWS 리전이 차단될 경우에 대비해 계획을 세울 때에는, AWS 리전에 걸친 백업과 복제본을 사용해야 합니다.

A. 읽기 전용 복제본은 재해 복구에 도움이 되지 않으며, AZ에 걸친 읽기 스케일링에 사용됩니다.


# 질문 3:

RDS 데이터베이스가 웹사이트에서 들어오는 요청량을 처리하는 데에 어려움을 겪고 있습니다. 백만 명의 사용자들은 대부분 뉴스를 읽고 있으며, 뉴스가 자주 포스팅되는 편은 아닙니다. 이 문제를 해결하기 위해 사용해서는 안 되는 솔루션은 무엇인가요?

A. ElastiCache 클러스터
B. RDS 다중 AZ
C. RDS 읽기 전용 복제본

정답 3: B

시험 문제를 읽을 때는 주의하시기 바랍니다. 이 문제에서는, 이런 문제점을 해결하기 위해 사용해서는 "안 되는" 솔루션이 무엇인지 묻고 있습니다. ElastiCache와 RDS 읽기 전용 복제본은 읽기 스케일링에 도움이 됩니다.


# 질문 4:

RDS 데이터베이스에 읽기 전용 복제본을 설정해 두었지만, 소셜 미디어 포스트를 업데이트할 시 업데이트가 바로 이루어지지 않는다는 점에 대해 사용자들이 불만을 토로하고 있습니다. 이 경우, 가능성이 있는 원인은 무엇일까요?

1. 애플리케이션에 버그가 존재함
2. 읽기 전용 복제본은 비동기 복제를 지니므로, 사용자들은 최종 일관성만을 읽게 됨
3. 그 대신 다중 AZ를 설정했었어야 함
정답 4: B


# 질문 5:

다음 RDS (Aurora 아님) 기능들 중, 사용 시 SQL 연결 문자열을 변경하지 않아도 되는 것은 무엇인가요?

A. 다중 AZ
B. 읽기 전용 복제본

정답 5: A

다중 AZ는 활성화 상태의 데이터베이스 종류와 상관 없이 동일한 연결 문자열을 유지합니다.


# 질문 6:

이 애플리케이션은 Application Load Balancer가 관리하는 오토 스케일링 그룹에서 관리 중인 EC2 인스턴스 플릿에서 실행되고 있습니다. 사용자들이 계속 재로그인을 해야 하는 상황이지만, 일부 EC2 인스턴스에 과부하를 일으킬 수도 있다는 생각에 고정 세션은 활성화하지 않으려 합니다. 어떻게 해야 할까요?

A. EC2 인스턴스에 ALB가 아닌 자체 커스텀 로드 밸런서 사용하기
B. 세션 데이터를 RDS에 저장하기
C. 세션 데이터를 ElastiCache에 저장하기
D. 세션 데이터를 공유 EBS 볼륨에 저장하기
정답 6: C

세션 데이터를 ElastiCache에 저장하는 방법은 서로 다른 EC2 인스턴스들이 필요 시 사용자의 상태를 회수할 수 있게끔 하기 위해 흔히 사용됩니다.


# 질문 7:

현재 어떤 분석 애플리케이션이 주요 프로덕션 RDS 데이터베이스에 대한 쿼리를 수행하고 있습니다. 이러한 쿼리들은 언제든 실행되어, RDS 데이터베이스의 성능을 낮추고 사용자 경험에 영향을 미치게 됩니다. 사용자 경험을 증진시키기 위해서는 어떻게 해야 할까요?

A. 읽기 전용 복제본 설정
B. 다중 AZ 설정
C. 밤에 분석 쿼리 실행

정답 7: A

읽기 전용 복제본을 설정하면 분석 애플리케이션이 쿼리를 수행할 수는 있으나, 이 쿼리들이 주요 프로덕션 RDS 데이터베이스에는 영향을 미치지 않게 되므로 도움이 됩니다.

B. 다중 AZ는 고가용성을 위해 사용됩니다. 다시 말해, 애플리케이션이 스탠바이 DB 인스턴스를 사용할 수 없다는 뜻입니다.

C. 문제에서 쿼리가 언제든지 실행될 수 있다고 언급했으므로, 문제에서 제시한 상황과는 맞지 않는 답변입니다.


# 질문 8:

주 AWS 리전에 재해가 발생했을 때에 대비하여 다른 AWS 리전에 데이터베이스의 복제본을 만들어 두려 합니다. 이런 작업을 쉽게 구현하기 위해서는 어떤 데이터베이스의 사용을 추천할 수 있을까요?

A. RDS 읽기 전용 복제본
B. RDS 다중 AZ
C. Aurora 읽기 전용 복제본
D. Aurora 글로벌 데이터베이스

정답 8: D

Aurora 글로벌 데이터베이스를 사용하면 최대 5개의 2차 리전까지 Aurora 복제본을 가질 수 있습니다.

A, C. 읽기 전용 복제본은 재해 복구에 도움이 되지 않습니다.

B. 다중 AZ는 AWS 리전 수준의 재해가 발생할 경우에는 도움이 되지 않습니다. 다중 AZ는 AZ 수준의 재해 발생 시에는 도움이 됩니다.


# 질문 9:

사용자들이 연결되었을 때, 비밀번호를 입력하도록 하여 ElastiCache Redis 클러스터의 보안을 높이기 위해서는 어떻게 해야 할까요?

A. Redis Auth 사용하기
B. IAM 인증 사용하기
C. 보안 그룹 사용하기

정답 9: A

B. ElastiCache Redis는 IAM 인증을 지원하지 않습니다. 이는 RDS MySQL과 RDS PostgreSQL 모두에 사용 가능합니다.

C. 보안 그룹을 사용하면 ElastiCache Redis 클러스터 인스턴스로 들어가는 트래픽을 필터링하는 데에는 도움이 되겠지만, 애플리케이션 레벨의 인증에는 도움이 되지 않습니다.


# 질문 10:

여러분이 근무 중인 기업은 RDS MySQL 5.6을 데이터베이스로 사용하는 프로덕션 Node.js 애플리케이션을 가지고 있습니다. Java로 프로그래밍된 새로운 애플리케이션은 정기적인 대시보드 생성을 위해 많은 양의 분석 워크로드를 수행할 예정입니다. 이 경우, 주요 애플리케이션에 발생하는 지장을 최소화하기 위해 구현할 수 있는 방법 중 가장 비용 효율적인 솔루션은 무엇인가요?

A. RDS 데이터베이스에 다중 AZ를 활성화하고 대기 데이터베이스에서 분석 워크로드 실행하기
B. 다른 AZ에 읽기 전용 복제본을 생성하고 데이터베이스의 복제본에 분석 워크로드 실행하기
C. 다른 AZ에 읽기 전용 복제본을 생성하고 소스 데이터베이스에 분석 워크로드 실행하기
정답 10: B


# 질문 11:

RDS PostgreSQL 데이터베이스의 특정 리전에서 정전이 발생했을 때 데이터베이스가 신속하게 다른 AWS 리전에서 읽고 쓰는 작업을 할 수 있도록 재해 복구 전략을 수립하려고 합니다. DR 데이터베이스는 가용성이 매우 높아야 합니다. 가장 적합한 방식은 무엇입니까?

A. 동일한 리전에 읽기 전용 복제본를 만들고 메인 데이터베이스에서 다중 AZ를 활성화한다.
B. 다른 리전에 읽기 전용 복제본를 만들고 해당 읽기 전용 복제본에서 다중 AZ를 활성화한다.
C. 동일한 리전에 읽기 전용 복제본를 만들고 해당 읽기 전용 복제본에서 다중 AZ를 활성화한다.
D. 메인 데이터베이스에서 멀티 리전(Multi-Region) 설정을 활성화한다.

정답 11: B


# 질문 12:

사내(On-premise)에서 관리하던 MySQL 데이터베이스를 RDS로 옮겼습니다. 데이터베이스와 상호 작용하는 애플리케이션과 개발자가 아주 많은 상태입니다. 모든 개발자는 회사의 AWS 계정에 IAM 사용자로 등록되어 있습니다. 모든 개발자에 대해 DB 사용자를 생성하지 않고 MySQL RDS DB 인스턴스에 액세스할 수 있게 하려면 가장 적절한 방법은 무엇입니까?

A. IAM 사용자는 기본적으로 RDS 데이터베이스에 접근할 수 있다.
B. Amazon Cognito 사용한다.
C. IAM 데이터베이스 인증 활성화한다.
정답 12: C


# 질문 13:

다음 중 RDS 읽기 전용 복제본과 다중 AZ로의 복제 작업을 적절하게 묘사한 설명은 무엇인가요?

A. 읽기 전용 복제본은 비동기 복제를 사용하고, 다중 AZ도 비동기 복제를 사용함
B. 읽기 전용 복제본은 비동기 복제를 사용하고, 다중 AZ는 동기 복제를 사용함
C. 읽기 전용 복제본은 동기 복제를 사용하고, 다중 AZ도 동기 복제를 사용함
D. 읽기 전용 복제본은 동기 복제를 사용하고, 다중 AZ는 비동기 복제를 사용함
정답 13: B


# 질문 14:

암호화되지 않은 RDS DB 인스턴스를 암호화하는 방법은 무엇인가요?

A. AWS 콘솔에서 RDS DB 인스턴스를 고른 후, Actions를 선택하면, 바로 KMS를 통한 암호화가 가능
B. RDS DB 인스턴스를 중단 후, AWS 콘솔에서 바로 가능
C. 암호화되지 않은 RDS DB 인스턴스의 스냅샷을 생성하고, 스냅샷을 복사해 ‘암호화 활성화하기' 박스를 체크한 뒤, RDS DB 인스턴스를 암호화되지 않은 스냅샷에서 복구하기
정답 14: C


# 질문 15:

RDS 데이터베이스를 위해 최대 ............개의 읽기 전용 복제본을 가질 수 있습니다.

A. 3
B. 7
C. 15
정답 15: C


# 질문 16:

다음 중 IAM을 이용한 웹 서버 인증을 지원하지 않는 RDS 데이터베이스 기술은 무엇인가요?

A. Oracle
B. PostgreSQL
C. MySQL

정답 16: A


# 질문 17:

암호화되지 않은 RDS DB 인스턴스가 있는 상태에서 읽기 전용 복제본을 생성하려 합니다. RDS 읽기 전용 복제본이 암호화되도록 구성할 수 있을까요?

A. 아니오
B. 예

정답 17: A

암호화되지 않은 RDS DB 인스턴스로는 암호화된 읽기 전용 복제본을 생성할 수 없습니다.


# 질문 18:

프로덕션에서 실행 중인 한 애플리케이션이 Aurora 클러스터를 데이터베이스로 사용하고 있습니다. 여러분의 개발 팀은 필요할 경우 많은 양의 워크로드를 수행할 수 있는, 스케일이 축소된 애플리케이션에서 애플리케이션의 버전을 실행하려 합니다. 애플리케이션은 대부분의 시간 동안 사용되지 않습니다. CIO는 여러분에게 팀을 도와 비용을 최소화하는 동시에 이를 달성해 줄 것을 요청했습니다. 어떤 방법을 사용해야 할까요?

A. Aurora 글로벌 데이터베이스 사용하기
B. RDS 데이터베이스 사용하기
C. Aurora 서버리스 사용하기
D. EC2에 Aurora를 실행하고, EC2 인스턴스가 밤에는 차단되도록 하는 스크립트 작성하기

정답 18: C

*워크로드:
작업을 완료하거나 성과를 창출하는 데 소요되는 컴퓨팅 리소스와 시간의 양

*Aurora 클러스터: https://docs.aws.amazon.com/ko_kr/AmazonRDS/latest/AuroraUserGuide/Aurora.Overview.html

*Aurora 서버리스:
https://aws.amazon.com/ko/rds/aurora/serverless/


# 질문 19:

하나의 Aurora DB 클러스터는 몇 개의 Aurora 읽기 전용 복제본을 가질 수 있을까요?

A. 5
B. 10
C. 15
정답 19: C


# 질문 20:

Amazon Aurora는 .......................... 데이터베이스를 모두 지원합니다.

A. MySQL 과 MariaDB
B. MySQL 과 PostgreSQL
C. Oracle 과 MariaDB
D. Oracle 과 MS SQL Server

정답 20: B


# 질문 21:

여러분은 게임 개발 업체에서 솔루션 아키텍트로 근무하고 있습니다. 하나의 게임에서, 실시간 점수를 기반으로 플레이어들의 랭킹을 매겨야 합니다. 여러분의 상사가 게임 리더보드 생성을 위해 효율적이고 고가용적인 솔루션을 설계해 구현해 줄 것을 요청했습니다. 무엇을 사용해야 할까요?

A. MySQL에 RDS 사용
B. Amazon Aurora 사용
C. 멤캐시트에 ElastiCache 사용
D. Redis에 ElastiCache 사용 - 정렬된 세트
정답 21: D

맴캐시트 vs Redis:

https://chrisjune-13837.medium.com/redis-vs-memcached-10e796ddd717


# 질문 22:

AWS 기반 오라클 데이터베이스의 완전한 커스터마이징이 필요합니다. AWS 서비스 사용의 이점을 누리고 싶습니다. 어떤 것을 추천하시나요?

A. 오라클용 RDS
B. 오라클용 RDS 커스텀
C. EC2에 오라클 배포

정답 22: B


# 질문 23:

재해 복구 및 감사 목적으로 Aurora 데이터베이스에 대한 장기 백업을 저장해야 합니다. 어떤 것을 추천하시나요?

A. 자동 백업 활성화
B. 온디맨드 백업 수행
C. Aurora 데이터베이스 복제 사용

정답 23: C


# 질문 24:

여러분의 개발팀은 프로덕션 데이터에 최대한 빨리 액세스해야 하기 때문에 프로덕션 Aurora 데이터베이스에 대해 읽기 및 쓰기 테스트를 수행하고자 합니다. 어떤 조언을 해주시겠습니까?

A. 이를 위한 Aurora 읽기 복제본 만들기
B. 프로덕션 데이터베이스에 대해 테스트 수행
C. DB 스냅샷을 만들어 새 데이터베이스로 복원하기
D. 오로라 복제 기능 사용

정답 24: D


# 질문 25:

RDS 데이터베이스에 100개의 EC2 인스턴스가 연결되어 있는데, 데이터베이스 유지 관리 시 애플리케이션 로직이 좋지 않아 모든 애플리케이션이 RDS에 다시 연결하는 데 많은 시간이 걸리는 것을 확인했습니다. 이 문제를 어떻게 개선할 수 있을까요?

A. 모든 애플리케이션 수정
B. 다중 AZ 비활성화
C. 다중 AZ 활성화
D. RDS Proxy 사용

정답 25: D