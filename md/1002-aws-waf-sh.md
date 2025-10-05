# AWS WAF

`AWS Web Application Firewall`

AWS WAF의 설명은 공식 사이트에 잘 설명되어있습니다.

`AWS WAF` is a **web application firewall service** that lets you 
**monitor web requests** that are **forwarded to an Amazon API Gateway API**,
 an Amazon CloudFront distribution, or an Application Load Balancer.
 This Get protect those resources based on **conditions that you specify**,
 such as the **IP addresses that the requests originate from**.

제가 이해한 바는 AWS WAF는 웹앱 방화벽 서비스이고, **웹 요청**을 모니터링합니다.
다음 대상의 AWS 웹앱을 보호할 수 있습니다:
- **Amazon CloudFront distributions**
-  Application **Load Balancers**
-  **Amazon API Gateway stages**  

## Web ACLs

- **Web ACLs / Web Access Control List**
  - 웹 접근 제어 목록: 앞선 글에서도 살펴본 내용이라 익숙해졌습니다.
  - 웹 애플리케이션으로 들어오는 **HTTP(S) 요청**을 검사하고 **허용, 차단, 카운트**하는 **규칙 집합**
- **SQL Injection, XSS 차단**
- **IP / 국가 단위 차단**
- 속도 제한 (Rate Limiting)
- **국가별 공인 IP 기준 트래픽 차단**
- **User-Agent 헤더 기준으로 트래픽 차단**
- `Amazon Kinesis Firehose`를 사용하여 로그를 저장
- `Amazon Redshift`, `Amazon Elastic Search` **로그 분석** 가능

추가적으로 아래 3 AWS 용어를 간략히 살펴봅니다.

`AWS Firehose`: 스트리밍 데이터 수집/저장, 중앙화 서비스 + 파이프라인
`Amazon Redshift`: 빅데이터 분석용 DB
`Amazon Elastic Search`: 검색 + 로그/메트릭 분석 서비스

---

## Amazon Kinesis Firehose

- AWS에서 제공하는 실시간 스트리밍 데이터를 자동으로 수집$\cdot$ 변환$\cdot$저장하는 완전관리형 서비스
- S3, Redshift 등으로 보내주는 **파이프라인**

**파이프라인 Pipeline**: 데이터를 **연속적인 단계(단계별 처리 흐름)**로 자동 전달·가공·저장하는 데이터 처리 경로

### Firehose

- **AWS Kinesis Data Firehose**는 실시간 스트리밍 데이터를 자동으로 수집, 변환, **저장하는 완전관리형(Managed) 서비스**입니다.
- **데이터 파이프라인 역할**을 하며, 데이터 생산자로부터 데이터를 받아 지정된 대상(S3, Redshift, OpenSearch, Splunk 등)에 전달합니다.
- **서버 관리 불필요**: 인프라를 직접 구성하거나 확장할 필요 없이 A**WS가 자동으로 처리**합니다.
- **실시간 변환 지원**: **Lambda 함수**를 사용해 데이터가 전송되기 전에 **JSON, CSV 등 원하는 형식으로 가공**할 수 있습니다.
- **자동 버퍼링 및 압축**: 데이터 전송 전 일정 시간 또는 용량 단위로 버퍼링 후 압축하여 저장합니다.
- **활용 예시**
  - 로그 및 메트릭 수집 후 **S3/Redshift로 적재**
  - 보안 로그를 실시간 분석용 OpenSearch로 전달

---

## Amazon Redshift

- 완전관리형(Managed) 클라우드 **데이터 웨어하우스**(Data Warehouse)
  - **빅데이터 분석용 데이터베이스**: 모델 학습을 위한 DB로 이해했습니다.
- 다양한 출처의 **데이터를 통합하고 정제하여 중앙 집중식 저장소에 보관**하는 시스템 / 데이터 분석 관련 용어
- MySQL 같은 RDB는 “`실시간 트랜잭션(OLTP)`”에 강하고, `Redshift`는 대규모 분석(OLAP)에 적합
  - `peta` 단위의 대규모 트래픽이라고 합니다.

---

## Amazon Elastic Search

- **기본 개념**: Amazon Elastic Search(현 OpenSearch)는 대량의 텍스트·로그 데이터를 색인(Indexing)하여 **검색, 시각화, 분석**을 빠르게 수행할 수 있는 **검색 엔진**입니다.
- **대규모 텍스트 데이터를 빠르게 검색**하고, **로그나 메트릭을 실시간 분석할 수 있는 클라우드 서비스**
- Amazon Elastic Search = Amazon **OpenSearch** Service

OpenSearch로 전환하는 단계로 이해했습니다.
https://aws.amazon.com/ko/opensearch-service/

---

## AWS ACL 설정

### ACL

Access Control List 접근 제어 목록

- 요청이 허용(Allow) 또는 차단(Deny)될지 판단
- 사용자, IP, 포트, 프로토콜 등 조건별로 접근 제어
- 보안 정책 구현에 활용 (예: AWS WAF, 네트워크 장비, 파일 시스템 등)

- Web ACLs / Web Access Control List
- AWS Web ACLs 설정할 수 있습니다. 미국 서비스라 미국 서버가 많습니다:

|  **AWS WAF > Web ACLs** |  |  |  |  |  |   |
|  Web ACLs that you have defined in the selected region. |  |  |  |  |  |   |
|  ☐ Find web ACLs |  |  |  |  |  |   |
|  **Name** | **Description** | **ARN** |  |  |  |   |
|   |  |  |  |  | **US East (Ohio)** | **Delete**  |
|   |  |  |  |  | **Global (Cloudfront)** |   |
|   |  |  |  |  | US East (N. Virginia) |   |
|   |  |  |  |  | US West (N. California) |   |
|   |  |  |  |  | US West (Oregon) |   |
|   |  |  |  |  | Asia Pacific (Osaka) |   |
|   |  |  |  |  | Asia Pacific (Seoul) |  *한국은 서울만*  |
|   |  |  |  |  | Asia Pacific (Tokyo) |   |
...
|   |  |  |  |  | South America (San Paulo) |   |

### ACL 설정

AWS에서 ACL을 설정하는 방법을 간략히 다루었습니다.
- 보통은 **Load Balancer**에 설정한다고 합니다.


| AWS WAF > Web ACLs > Create web ACL |  |
| ----------------------------------- | - |
| Step 1                              |  |
| Describe web ACL and                |  |
| associate it to AWS resources       |  |
| Step 2                              |  |
| Add rules and rule groups           |  |
| Step 3                              |  |
| Set rule priority                   |  |
| Step 4                              |  |
| Configure metrics                   |  |
| Step 5                              |  |
| Review and create web ACL           |  |

## Describe web ACL and associate it to AWS resources Info

### Web ACL details

- **Resource type**:
  - 이 **웹 ACL에 연결할 리소스 유형**을 선택합니다. 이 설정을 변경하면 페이지가 초기화됩니다.
    - **전역 리소스** (CloudFront 배포, CloudFront Distribution Tenants, AWS Amplify 애플리케이션)
    - 리전별 리소스 (Application Load Balancer, Amazon API Gateway REST API, Amazon App Runner 서비스, AWS AppSync API, Amazon Cognito 사용자 풀, AWS Verified Access 인스턴스)
- **Region**:  AWS 리젼 별로 ACL을 설정할 수 있습니다.
- **Name**: ACL 이름
- **Description - optional**
- CloudWatch metric name

## Load Balancer (중요)

- 용도: **부하를 분산하는 장치**(Load + Balancer)
  - 여러 대의 서버에 트래픽을 고르게 분산시켜 웹 서비스의 성능, 안전성, 확장성을 향상
  - 하나의 서버에 트래픽이 몰리는 것을 실시간으로 여러 서버에 고르게 배분

### 로드 밸런서 주요 기능

- 트래픽 분산
  - 요청을 여러 서버(백엔드)에 고르게 나눔
  - 도메인 단일화: 여러 서버가 있어도 로드 밸런서를 통해 **하나의 도메인(URL)** 로 접근할 수 있도록 함  
    - 사용자는 서버 분산 구조를 인식하지 못하고 동일한 주소로 접속 가능  
    - 로드 밸런서가 **내부적으로 각 서버에 요청을 자동 분배**하여 처리
- 헬스 체크
  - 서버 상태를 주기적으로 확인하고, 문제 있는 서버는 제외
- 장애 대응
  - 특정 서버 다운 시 자동으로 다른 서버로 트래픽 우회
- 확장성 향상
  - 서버를 추가/삭제해도 트래픽 분배 자동 조정
  - 여러 서버를 단일 도메인(URL)로 묶어 서비스 가능
- 보안 기능: SSL 인증서 관리, DDoS 방어, 요청 필터링 등으로 애플리케이션 트래픽을 보호
  - SSL 종료(HTTPS 처리) 기능 제공

### Load Balancer 동작 구조

$$
\begin{aligned}
& \text { 클라이언트 } \longrightarrow \text { 로드-밸런서 } \longrightarrow \text { 서버1 } \\
& \longleftarrow \text { 서버 } 2 \\
& \longleftarrow \text { 서버3 }
\end{aligned}
$$

- 클라이언트는 항상 로드 밸런서 한 곳에만 요청
- 로드 밸런서가 트래픽을 **분배 규칙(알고리즘)**에 따라 서버로 전달
- 서버가 응답율 로드 밸런서를 통해 다시 클라이언트에게 반환

---

### Load Balancer 분산 알고리즘

각 알고리즘에 대해 상세히 알지는 않지만, 추후 더 알아보겠습니다.

- `Round Robin`
  - 서버 순서대로 요청 분배 (가장 일반적)
  - 모든 서버의 성능이 유사할 때 효율적이며, 단순한 구조로 가장 널리 사용됨
- `Weighted Round Robin`
  - 서버 성능에 따라 가중치 부여 후 분배
  - CPU나 메모리 자원이 높은 서버에 더 많은 요청을 분배해 부하 균형 유지
- `Least Connections`
  - 연결 수가 가장 적은 서버에 전달
  - 실시간 트래픽 변동이 큰 환경에서 균형 있는 처리 성능 제공

### Load Balancer 종류

간략히 알아봤습니다. 관심이 많은데, 추후 천천히 알아보겠습니다.

- ALB (Application Load Balancer)
- 7계층 (HTTP/HTTPS)
- URL$\cdot$헤더$\cdot$쿠키 기반 라우팅 가능
- NLB (Network Load Balancer)
- 4계층 (TCP/UDP)
- 초고속 트래픽 처리, 지연 최소화
