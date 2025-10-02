
# AWS WAF

## AWS WAF

Web Application Firewall

- (WAF 기본 개념 간략히 설명 작성)
- (AWS WAF 기본 개념 간략히 설명 작성)


#### WAFs WAF

- **Getting started**: 2019 WAFs WAF
- **Web ACLs**: 2019 WAFs WAF
- **Bot control**: 2019 WAFs WAF
- **Application integration**: 2019 WAFs WAF
- **IP sets**: 2019 WAFs WAF
- **Reges pattern sets**: 2019 WAFs WAF
- **Rule groups**: 2019 WAFs WAF
- **Add-on protections**: 2019 WAFs WAF
- **Switch to AWS WAF Classic**: 2019 WAFs WAF
- **WAFs Shield**: 2019 WAFs WAF
- **Getting started**: 2019 WAFs WAF
- **Overview**: 2019 WAFs WAF
- **Protected resources**: 2019 WAFs WAF
- **Events**: 2019 Global threat dashboard
- **WAFs Shield network security director**: 2019 WAFs WAF
- **Getting started**: 2019 WAFs WAF
- **Benefits and features**: 2019 WAFs WAF
- **Agile protection against web attacks**: 2019 WAFs WAF
- **AWS WAF rule propagation and updates**: 2019 WAFs WAF
- **Web WAF rule propagation and updates take just under a minute, enabling you to react faster when you are under an attack or when security issues arise**: 2019 WAFs WAF
- **WAF supports hundreds of rules that can inspect any part of the web**: 2019 WAFs WAF
- **WAFs WAF request with minimal latency**: 2019 WAFs WAF
- **Impact to incoming traffic**: 2019 WAFs WAF
- **Improved web traffic visibility**: 2019 WAFs WAF
- **Ease of deployment and** 2019 WAFs WAF

### WAFs WAF Protect your web applications from common web exploits

AWS WAF is a web application firewall service that lets you monitor web requests that are forwarded to an Amazon API Gateway API, an Amazon CloudFront distribution, or an Application Load Balancer. This Get protect those resources based on conditions that you specify, such as the IP addresses that the requests originate from.

### Get started with AWS WAF

Get up protection for your Amazon CloudFront distributions, Application Load Balancers, and/or Amazon API Gateway stages in just under 5 minutes.

### Privacy

- **Privacy with ACL**: 2019 WAFs WAF
- **Privacy with ACL**: 2019 WAFs WAF


---

# AWS WAF 

- Web ACLs / Web Access Control List
- 웹 접근 제어 목록
- 웹 애플리케이션으로 들어오는 HTTP(S) 요청을 검사하고 허용, 차단, 카운트하는 규칙 집합
- SQL Injection, XSS 차단
- IP / 국가 단위 차단
- 속도 제한 (Rate Limiting)

---



AWS WAF

- 국가별 공인 IP 기준 트래픽 차단
- User-Agent 헤더 기준으로 트래픽 차단
- Amazon Kinesis Firehose를 사용하여 로그를 저장
- Amazon Redshift, Amazon Elastic Search 로그 분석 가능

---

# Amazon Kinesis Firehose 

- AWS에서 제공하는 실시간 스트리밍 데이터를 자동으로 수집$\cdot$ 변환$\cdot$저장하는 완전관리형 서비스
- S3, Redshift 등으로 보내주는 파이프라인

### Firehose

(기본 개념 리스트로 설명 작성)

---



## Amazon Redshift

- 완전관리형(Managed) 클라우드 데이터 웨어하우스(Data Warehouse)
- 빅데이터 분석용 데이터베이스
- 다양한 출처의 데이터를 통합하고 정제하여 중앙 집중식 저장소에 보관하는 시스템 / 데이터 분석 관련 용어
- MySQL 같은 RDB는 “`실시간 트랜잭션(OLTP)`”에 강하고, `Redshift`는 대규모 분석(OLAP)에 적합
  - `peta` 단위의 대규모 트래픽이라고 합니다.


---

## Amazon Elastic Search 

- Amazon Elastic Search = Amazon OpenSearch Service
- 대규모 텍스트 데이터를 빠르게 검색하고, 로그나 메트릭을 실시간 분석할 수 있는 클라우드 서비스
- ( 기본 개념 간략히 설명 작성)
- (이외로 비슷한 경쟁 제품 간략 설명 추가)
실제로 많이 사용합니다.

---

## AWS ACL 설정

### ACL
(약어 설명)
(리스트로 간략 설명 추가)


- Web ACLs / Web Access Control List
- 웹 접근 제어 목록
미국 서비스라 미국 서버가 많습니다:

|  **AWS WAF > Web ACLs** |  |  |  |  |  |   |
| --- | --- | --- | --- | --- | --- | --- |
|  **Web ACLs (0)** |  |  |  |  |  |   |
|  Web ACLs that you have defined in the selected region. |  |  |  |  |  |   |
|  ☐ Find web ACLs |  |  |  |  |  |   |
|  **Name** | **Description** | **ARN** |  |  |  |   |
|   |  |  |  |  | **US East (Ohio)** | **Delete**  |
|   |  |  |  |  | **Global (Cloudfront)** |   |
|   |  |  |  |  | US East (N. Virginia) |   |
|   |  |  |  |  | US West (N. California) |   |
|   |  |  |  |  | US West (Oregon) |   |
|   |  |  |  |  | Asia Pacific (Osaka) |   |
|   |  |  |  |  | Asia Pacific (Seoul) |  한국은 서울만  |
|   |  |  |  |  | Asia Pacific (Tokyo) |   |
...
|   |  |  |  |  | South America (San Paulo) |   |


### ACL 설정

AWS에서 ACL을 설정하는 방법입니다.

- Web ACLs
  - Step 1

|  AWS WAF > Web ACLs > Create web ACL | |
| --- | --- |
|  Step 1 | |
|  Describe web ACL and | |
|  associate it to AWS resources | |
|  Step 2 | |
|  Add rules and rule groups | |
|  Step 3 | |
|  Set rule priority | |
|  Step 4 | |
|  Configure metrics | |
|  Step 5 | |
|  Review and create web ACL | |

## Describe web ACL and associate it to AWS resources Info

### Web ACL details
- **Resource type**: 
  - Choose the type of resource to associate with this web ACL. Changing this setting will reset the page.
  - Global resources (CloudFront Distributions, CloudFront Distribution Tenants and AWS Amplify Applications)
  - Regional resources (Application Load Balancers, Amazon API Gateway REST APIs, Amazon App Runner services, AWS AppSync APIs, Amazon Cognito user pools and AWS Verified Access Instances)
- **Region**: Choose the AWS Region to create this web ACL in. Changing this setting will reset the page.
- **Name**
- **Description - optional**
The description can have 1-256 characters.

- **CloudWatch metric name**

---

# AWS WAF

## Web ACLs

### • Step 1 / Add AWS resources

**Region** Choose the AWS Region to create this web ACL in. Changing this setting will reset the page.

**US Cent (Ohio)**

**Name**

251001_web_act

The name must have 1-100 characters. Valid characters: A-Z, a-z, 0-5, - (hypheti), and _ (undercore).

**Description - optional**

The description can have 1-250 characters.

**CloudWatch metric name**

251001_web_act

The name must have 1-100 characters. Valid characters: A-Z, a-z, 0-5, - (hypheti), and _ (undercore).

**Associated AWS resources - optional (0)**

|  Remove | Add AWS resources  |
| --- | --- |
|  ☐ Find associated AWS resources | ☐ 1  |
|  **Name** | **Resource type**  |
|  ☐ No items |   |
|  ☐ No items to display |   |

**Add AWS resources**

**Resource type** Select the resource type and then select the resource you want to associate with this web ACL.

**Application Load Balancer** (중요)

- ☐ Amazon API Gateway REST API
- ☐ Amazon App Runner service
- ☐ AWS AppSync API
- ☐ Amazon Cognito user pool
- ☐ AWS Verified Access

**Resources (0)**

Select the resource you want to associate with the web ACL.

**Find AWS resources to associate**

- ☐ 1
- ☐ 0

**Name**

**No results**

There are no results to display

**Cancel** **Next**

**Cancel** **Add**

---

# AWS WAF

- Web ACLs
- Step 1 / Add AWS resources
- 보통은 Load Balancer에 설정하는데 없으니 우선 패스 (추후 필요)

![[AWS_WAFShield_p12_img3.jpeg]]

![[AWS_WAFShield_p12_img4.jpeg]]

---


## Load Balancer (중요)

- 부하를 분산하는 장치(Load + Balancer)
- 여러 대의 서버에 트래픽을 고르게 분산시켜 웹 서비스의 성능, 안전성, 확장성을 향상
- 하나의 서버에 트래픽이 몰리는 것을 실시간으로 여러 서버에 고르게 배분


### 로드 밸런서 주요 기능

- 트래픽 분산
- 헬스 체크
- 장애 대응
- 확장성 향상
- 보안 기능
- 도메인 단일화
- 요청을 여러 서버(백엔드)에 고르게 나눔
- 서버 상태를 주기적으로 확인하고, 문제 있는 서버는 제외
- 특정 서버 다운 시 자동으로 다른 서버로 트래픽 우회
- 서버를 추가/삭제해도 트래픽 분배 자동 조정
- SSL 종료(HTTPS 처리) 기능 제공
- 여러 서버를 단일 도메인(URL)로 묶어 서비스 가능



### Load Balancer 동작 구조

$$
\begin{aligned}
& \text { 클라이언트 } \longrightarrow \text { 로드 밸런서 } \longrightarrow \text { 서버1 } \\
& \longleftarrow \text { 서버 } 2 \\
& \longleftarrow \text { 서버3 }
\end{aligned}
$$

- 클라이언트는 항상 로드 밸런서 한 곳에만 요청
- 로드 밸런서가 트래픽을 **분배 규칙(알고리즘)**에 따라 서버로 전달
- 서버가 응답율 로드 밸런서를 통해 다시 클라이언트에게 반환

---

# Load Balancer 

- 로드 밸런서 분산 알고리즘
- Round Robin
- 서버 순서대로 요청 분배 (가장 일반적)
- Least Connections
- 연결 수가 가장 적은 서버에 전달
- Weighted Round Robin
- 서버 성능에 따라 가중치 부여 후 분배

---

# Load Balancer 

- ALB (Application Load Balancer)
- 7계층 (HTTP/HTTPS)
- URL$\cdot$헤더$\cdot$쿠키 기반 라우팅 가능
- NLB (Network Load Balancer)
- 4계층 (TCP/UDP)
- 초고속 트래픽 처리, 지연 최소화

---

# AWS WAF

- Web ACLs
- Step 2 / Add rules and rule groups

## Add rules and rule groups info

A rule defines attack patterns to look for in web requests and the action to take when a request matches the patterns. Rule groups are reusable collections of rules. You can use managed rule groups offered by AWS and AWS Marketplace sellers. You can also write your own rules and use your own rule groups.

|  Rules (0) |  | Edit | Delete | Add rules ▲  |
| --- | --- | --- | --- | --- |
|  If a request matches a rule, take the corresponding action. The rules are prioritized in order they appear. |  |  |  | Add managed rule groups  |
|  Name | Capacity | Action |  | Add my own rules and rule groups  |
|   | No rules. |  |  |   |
|   | You don't have any rules added. |  |  |   |

---

# AWS WAF

- Web ACLs
- Paid rule groups

## - AWS managed rule groups

## Paid rule groups

AWS WAF charges subscription and usage fees for paid managed rule groups. These are in addition to the standard service charges for AWS WAF. AWS WAF Pricing

|  Name | Capacity | Additional fees | Action  |
| --- | --- | --- | --- |
|  Account creation fraud prevention - new
Provides protection against the creation of fraudulent accounts on your site. Fraudulent accounts can be used for activities such as obtaining sign-up bonuses and impersonating legitimate users. Learn More $\square$ | 50 | - \$10 per month (prorated hourly).
- Tiered fee model for requests analyzed AWS WAF Pricing $\square$ | (3) Add to web ACL  |
|  Account takeover prevention
Provides protection for your login page against stolen credentials, credential stuffing attacks, brute force login attempts, and other anomalous login activities. With account takeover prevention, you can prevent unauthorized access that may lead to fraudulent activities, or inform legitimate users to take a preventive action. Learn More $\square$ | 50 | - \$10 per month (prorated hourly).
- Tiered fee model for requests analyzed AWS WAF Pricing $\square$ | (3) Add to web ACL  |
|  AntiDDoS Protection for Layer 7 attacks
Provides protection against DDoS attacks targeting the application layer, also known as Layer 7 attacks. | 50 | - \$20 per month (prorated hourly).
- Tiered fee model for requests analyzed AWS WAF Pricing $\square$ | (3) Add to web ACL  |

---

# AWS WAF

## • Web ACLs

## • Free rule groups

|  Name | Capacity | Action  |
| --- | --- | --- |
|  Admin protection |  |   |
|  Contains rules that allow you to block external access to exposed admin pages. This may be useful if you are running third-party software or would like to reduce the risk of a malicious actor gaining administrative access to your application. Learn More ☑ | 100 | Add to web ACL  |
|  Amazon IP reputation list |  |   |
|  This group contains rules that are based on Amazon threat intelligence. This is useful if you would like to block sources associated with bots or other threats. Learn More ☑ | 25 | Add to web ACL  |
|  Anonymous IP list |  |   |
|  This group contains rules that allow you to block requests from services that allow obfuscation of viewer identity. This can include request originating from VPN, proxies, Tor nodes, and hosting providers. This is useful if you want to filter out viewers that may be trying to hide their identity from your application. Learn More ☑ | 50 | Add to web ACL  |
|  Core rule set |  |   |
|  Contains rules that are generally applicable to web applications. This provides protection against exploitation of a wide range of vulnerabilities, including those described in OWASP publications. Learn More ☑ | 700 | Add to web ACL  |
|  Known bad inputs |  |   |
|  Contains rules that allow you to block request patterns that are known to be invalid and are associated with exploitation or discovery of vulnerabilities. This can help reduce the risk of a malicious actor discovering a vulnerable application. Learn More ☑ | 200 | Add to web ACL  |
|  Linux operating system |  |   |
|  Contains rules that block request patterns associated with exploitation of vulnerabilities specific to Linux, including LFI attacks. This can help prevent attacks that expose file contents or execute code for which the attacker should not have had access. Learn More ☑ | 200 | Add to web ACL  |

---

# AWS WAF

- Web ACLs
- The total WCUs for a web ACL can't exceed 5000. Using over 1500 WCUs affects your costs.
- 表 WCU 5000 이상 X
- 1500 WCU 이상 > 요금 과중

|  AWS WAF > Web ACLs > Create web ACL |  |  |   |
| --- | --- | --- | --- |
|  Step 1
Describe web ACL and associate it to AWS resources |  |  |   |
|  Step 2
Add rules and rule groups |  |  |   |
|  Step 3
Set rule priority |  |  |   |
|  Step 4
Configure metrics |  |  |   |
|  Step 5
Review and create web ACL |  | Add rules and rule groups fully
A rule defines attack patterns to look for in web requests and the action to take when a request matches the patterns. Rule groups are reusable collections of rules. You can use managed rule groups offered by AWS and AWS Marketplace sellers. You can also write your own rules and use your own rule groups. |   |
|   | Rules (1) | Edit | Delete  |
|   | If a request matches a rule, take the corresponding action. The rules are prioritized in order they appear. |  |   |
|   | Name | Capacity | Action  |
|   | AWS-AWSManagedRulesKnownBadInputsRuleSet | 200 | Use rule actions  |
|   | Web ACL capacity units (WCUs) used by your web ACL
The WCUs used by the web ACL will be less than or equal to the sum of the capacities for all of the rules in the web ACL. |  |   |
|   | The total WCUs for a web ACL can't exceed 5000. Using over 1500 WCUs affects your costs. AWS WAF Pricing 12 |  |   |
|   |  |  | 12  |

---

# AWS WAF

- Web ACLs
- The total WCUs for a web ACL can't exceed 5000. Using over 1500 WCUs affects your costs.
- 表 WCU 5000 이상 X
- 1500 WCU 이상 > 요금 과중

|  AWS WAF > Web ACLs > Create web ACL |  |  |  |   |
| --- | --- | --- | --- | --- |
|  Step 1
Describe web ACL and associate it to AWS resources |  |  |  |   |
|  Step 2
Add rules and rule groups |  |  |  |   |
|  Step 3
Set rule priority |  |  |  |   |
|  Step 4
Configure metrics |  |  |  |   |
|  Step 5
Review and create web ACL |  |  |  |   |

Add rules and rule groups fully A rule defines attack patterns to look for in web requests and the action to take when a request matches the patterns. Rule groups are reusable collections of rules. You can use managed rule groups offered by AWS and AWS Marketplace sellers. You can also write your own rules and use your own rule groups.

|  Rules (1) | Edit | Delete | Add rules  |
| --- | --- | --- | --- |
|  If a request matches a rule, take the corresponding action. The rules are prioritized in order they appear. |  |  |   |
|  $\square$ | Name | Capacity | Action  |
|  $\square$ | AWS-AWSManagedRulesKnownBadInputsRuleSet | 200 | Use rule actions  |

Web ACL capacity units (WCUs) used by your web ACL The WCUs used by the web ACL will be less than or equal to the sum of the capacities for all of the rules in the web ACL.

The total WCUs for a web ACL can't exceed 5000. Using over 1500 WCUs affects your costs. AWS WAF Pricing

---

# Web ACLs

- Step 3. Set rule priority
- 우선순위 설정
    - 현재 Rules이 1개이기 때문에 우선순위 할 것이 없음

|  AWS WAF > Web ACLs > Create web ACL |  |  |   |
| --- | --- | --- | --- |
|  Step 1
Describe web ACL and associate it to AWS resources |  |  |   |
|  Step 2
Add rules and rule groups |  |  |   |
|  Step 3
Set rule priority | Set rule priority info |  |   |
|  Step 4
Configure metrics |  |  |   |
|  Step 5
Review and create web ACL |  |  |   |

## Set rule priority info

|  Rules (1) | $\Delta$ | Move up | $\nabla$ | Move down  |
| --- | --- | --- | --- | --- |
|  If a request matches a rule, take the corresponding action. The rules are prioritized in order they appear. |  |  |  |   |
|   | Name | Capacity | Action |   |
|   | AWS-AWSManagedRulesKnownBadInputsRuleSet | 200 | Use rule actions |   |
|  |   |   |   |   |
|   |  | Cancel | Previous | Next  |

---

# Web ACLs

## Step 4. Configure metrics

|  AWS WAF > Web ACLs > Create web ACL | |
| --- | --- |
|  Step 1 | |
|  Describe web ACL and | |
|  associate it to AWS resources | |
|  Step 2 | |
|  Add rules and rule groups | |
|  Step 3 | |
|  Set rule priority | |
|  Step 4 | |
|  Configure metrics | |
|  Step 5 | |
|  Review and create web ACL | |

### Configure metrics **Info**

#### **Amazon CloudWatch metrics**

CloudWatch metrics allow you to monitor web requests, web ACLs, and rules.

- **Rules**: CloudWatch metric name
- AWS AWS Managed Rules Known Bad Inputs Rule Set
- AWS AWS Managed Rules Known Bad Inputs Rule Set

#### **Request sampling options**

If you disable request sampling, you can't view requests that match your web ACL rules.

- **Options**:
- Enable sampled requests
- Disable sampled requests
- Enable sampled requests with exclusions

---

# Web ACLs

## Step 5. Review and create web ACL

|  AWS WAF > Web ACLs > Create web ACL |  |  |  |  |   |
| --- | --- | --- | --- | --- | --- |
|  Step 1
Describe web ACL and associate it to AWS resources |  |  |  |  |   |
|  Step 2
Add rules and rule groups |  |  |  |  |   |
|  Step 3
Set rule priority |  |  |  |  |   |
|  Step 4
Configure metrics |  |  |  |  |   |
|  Step 5
Review and create web ACL |  |  |  |  |   |

## Review and create web ACL info

Step 1: Describe web ACL and associate it to AWS resources

Web ACL details

|  Name | Scope  |
| --- | --- |
|  251001_web_acl | REGIONAL  |
|  Description | Region  |
|  CloudWatch metric name | us-east-2  |
|  251001_web_acl |   |

## Steps 2 and 3: Add rules and set rule priority

Edit steps 2 and 3

Rules (1) If a request matches a rule, take the corresponding action. The rules are prioritized in order they appear.

|  Name | Capacity | Action  |
| --- | --- | --- |
|  AWS-AWSManagedRulesKnownBadInputsRuleSet | 200 | Use rule actions  |

---



WAF

- WAF는 HTTP 프로토콜을 사용하는 AWS리소스만 사용 가능
- Cloudfront
- application load balancer
- Api gateway

- AWS리소스 필수!!!

---

# EC2 – Load Balancer

• Load Balancer 설정

![[AWS_WAFShield_p27_img5.jpeg]]

---

# EC2 – Load Balancer

- **Load Balancer 설정**
- **Application Load Balancer**

![[AWS_WAFShield_p28_img6.jpeg]]

### **로드 밸런서 유형 비교 및 선택**

자세한 하이브리드와 함께 전체 기능을 비교도 제공합니다. 자세히 알아보기

---

# EC2 - Load Balancer 

## - Load Balancer 설정

- Application Load Balancer


## 기본 구성

## 로드 밸런서 이름

이름은 AWS 계정 내에서 고유해야 하며 로드 밸런서 생성 후에는 변경할 수 없습니다.

## 251001_load_balancer

하이픈을 포함하여 최대 32자의 명숫자 문자를 사용할 수 있지만 이름이 하이픈으로 시작하거나 끝나지 않아야 합니다.

## 체계 정보

로드 밸런서 생성 후에는 스키마를 변경할 수 없습니다.

## 인터넷 경계

- 인터넷 경계 트래픽을 처리합니다.
- 퍼블릭 IP 주소가 있습니다.
- DNS 이름은 퍼블릭 IP로 확인됩니다.
- 퍼블릭 서브넷이 필요합니다.


## 내부

- 내부 트래픽을 처리합니다.
- 프라이빗 IP 주소가 있습니다.
- DNS 이름은 프라이빗 IP로 확인됩니다.
- IPv4 및 듀얼 스택 IP 주소 유형과 호환됩니다.


## 로드 밸런서 IP 주소 유형 정보

로드 밸런서에 할당할 프런트엔드 IP 주소 유형을 선택합니다. 이 로드 밸런서에 매핑된 VPC 및 서브넷에는 선택한 IP 주소 유형이 포함되어야 합니다. 퍼블릭 IPv4 주소에는 추가 비용이 부과됩니다.

## IPv4

IPv4 주소만 포함합니다.

## 듀얼 스택

IPv4 및 IPv6 주소를 포함합니다.

## 퍼블릭 IPv4가 없는 듀얼 스택

퍼블릭 IPv6 주소와 프라이빗 IPv4 및 IPv6 주소를 포함합니다. 인터넷 연결 로드 밸런서와만 호환됩니다.

---

# EC2 – Load Balancer

- Load Balancer 설정
- Application Load Balancer

네트워크 매핑 정보
로드 밸런서는 IP 주소 설정에 따라 선택한 서브넷의 대상으로 트래픽을 라우팅합니다.

VPC 정보
로드 밸런서는 선택한 VPC 내에서 존재하고 확인됩니다. 또한 선택한 VPC는 Lambda 또는 은프레위스 대상으로 라우팅하거나 VPC 피어링을 사용하는 경우를 제외하고 로드 밸런서 대상을 호스팅해야 하는 위치어
기도 합니다. 대상의 VPC를 확인하려면 대상 그룹 및 확인자격도

vpc-059v8bde926a22096 (250930vpc)
10.0.0.0/16 ▼ VPC 생성

IP 홀 정보
선택적으로 IPMA 홀을 로드 밸런서 IP 주소의 기본 소스로 구성하도록 선택할 수 있습니다. Amazon VPC IP 주소 관리자 콘솔 1에서 홀을 생성하거나 확인합니다.

☐ 외장식 IPv4 주소의 IPMA 등 사용
선택한 IPMA 홀의 회중의 IPv4 주소의 기본 소스가 됩니다. 홀의 고정되면 4bit에서 IPv4 주소를 할당합니다.

가용 영역 및 서브넷 정보
가용 영역을 3개 이상 선택하고 각 영역에 대해 서브넷을 선택합니다. 로드 밸런서 노드는 선택한 각 영역에 배치되며 트래픽에 따라 자동으로 확장됩니다. 로드 밸런서는 선택한 가용 영역의 대상으로만 트래픽을 라우팅합니다.

us-east-2a (use2-as1)
서브넷
로드 밸런서 IP 주소 유형에 해당하는 ODH 블록만 사용됩니다. 로드 밸런서를 효율적으로 확장하려면 사용 가능한 IP 주소가 8개 이상 필요합니다.

submit-Go11b0bddoe052869
IPv4 서브넷 ODH 10.0.0.0/24

보안 그룹 정보
보안 그룹은 로드 밸런서에 대한 트래픽을 제어하는 방화벽 규칙 세트입니다. 기존 보안 그룹을 선택하거나 새 보안 그룹을 생성 할 수 있습니다.

보안 그룹

최대 5 개의 보안 그룹 선택 ▼

default
vpc-05a0077030a48c7d VPC vpc-059v8bde926a22096

---

# EC2 – Load Balancer

• Load Balancer 설정

• Application Load Balancer

네트워크 매핑 정보
로드 밸런서는 IP 주소 설정에 따라 선택한 서브넷의 대상으로 트래픽을 라우팅합니다.

VPC 정보
로드 밸런서는 선택한 VPC 내에서 존재하고 확인됩니다. 또한 선택한 VPC는 Lambda 또는 은프레위스 대상으로 라우팅하거나 VPC 피어링을 사용하는 경우를 제외하고 로드 밸런서 대상을 호스팅해야 하는 위치어
기도 합니다. 대상의 VPC를 확인하려면 대상 그룹 및 확인자격도

vpc-059v8bde926a22096 (250930vpc)
10.0.0.0/16 ▼ VPC 생성

IP 홀 정보
선택적으로 IPMA 홀을 로드 밸런서 IP 주소의 기본 소스로 구성하도록 선택할 수 있습니다. Amazon VPC IP 주소 관리자 콘솔 1에서 홀을 생성하거나 확인합니다.

☐ 외장식 IPv4 주소의 IPMA 등 사용
선택한 IPMA 홀의 회중의 IPv4 주소의 기본 소스가 됩니다. 홀의 고정되면 4bit에서 IPv4 주소를 할당합니다.

가용 영역 및 서브넷 정보
가용 영역을 3개 이상 선택하고 각 영역에 대해 서브넷을 선택합니다. 로드 밸런서 노드는 선택한 각 영역에 배치되며 트래픽에 따라 자동으로 확장됩니다. 로드 밸런서는 선택한 가용 영역의 대상으로만 트래픽을 라우팅합니다.

us-east-2a (use2-as1)
서브넷
로드 밸런서 IP 주소 유형에 해당하는 ODH 블록만 사용됩니다. 로드 밸런서를 효율적으로 확장하려면 사용 가능한 IP 주소가 8개 이상 필요합니다.

submit-Go11b0bddoe052869
IPv4 서브넷 ODH 10.0.0.0/24

보안 그룹 정보
보안 그룹은 로드 밸런서에 대한 트래픽을 제어하는 방화벽 규칙 세트입니다. 기존 보안 그룹을 선택하거나 새 보안 그룹을 생성 할 수 있습니다.

보안 그룹

최대 5 개의 보안 그룹 선택 ▼

default
vpc-05a0077030a48c7d VPC vpc-059v8bde926a22096

---

# EC2 – Load Balancer

## Security Group

### 보안 그룹 생성 정보

보안 그룹은 인바운드 및 아웃바운드 트래픽을 관리하는 인스턴스의 가상 방화벽 역할을 합니다. 새 보안 그룹을 생성하려면 아래의 필드를 작성하십시오.

### 기본 세부 정보

보안 그룹 이름 정보 201601_security_group 생성 위쪽는 이름을 반입할 수 없습니다.

설정 정보

개발자(8개소)나 액세스 지분

납세 정보

up=100x46db920a220961200930cpc

### 인바운드 규칙 정보

---

# EC2 - Load Balancer 

- CloudFront + WAF
- WAF
- Global Accelerator

서비스 통합을 통한 최적화 - 선택 사항 정보
시작 시 AWS 서비스를 이 로드 밸런서와 통합하여 로드 밸런싱 구조를 최적화할 수 있습니다. 로드 밸런서의 "통합" 탭을 검토하여 로드 밸런서가 생성된 후 이러한 서비스 및 기타 서비스를 추가할 수도 있습니다.

Amazon CloudFront + AWS 웹 애플리케이션 방화벽(WAF) - 신규 정보
최적화: 성능, 가용 여부, 보안
$\square$ 애플리케이션 계층 가속화 및 보안 보호 적용 - 로드 밸런서 앞에
기본 관점 AWS WAF 보안 보호를 사용하여 CloudFront 배포를 자동으로 구성 및 생성하고 로드 밸런서에 연결합니다. 추가 요금 적용 $\square$

- Benefits and considerations

AWS 웹 애플리케이션 방화벽(WAF) 정보
최적화: 보안
$\square$ 애플리케이션 계층 보안 보호 적용 - 대상 앞에
기본 관점 AWS WAF 보안 보호가 포함된 사전 잠재된 보안 구성을 선택하거나 사용자 지정 보호를 위한 기존 WAF 구성을 연결할 수 있습니다. 추가 요금 적용 $\square$

- Benefits and considerations

AWS Global Accelerator 정보
최적화: 성능, 가용 여부
$\square$ 여러 리턴에 글로벌 로드 밸런싱 적용
로드 밸런서의 고정 전입장 역할을 하는 두 개의 글로벌 고정 IP를 사용하여 계정에 액셀러레이터를 생성합니다. 여러 리턴에 걸친 글로벌 고정 IP 또는 트래픽 관리가 필요하지 않은 경우 Amazon CloudFront를 선택하세요. 추가 요금 적용 $\square$

- Benefits and considerations

---

# EC2 - Load Balancer 

- WAF


## AWS 웹 애플리케이션 방화벽(WAF) 정보

## 최적화:보안

애플리케이션 계층 보안 보호 적용 - 대상 알제
기본 권장 AWS WAF 보안 보호가 포함된 사전 정의된 보안 구성을 선택하거나 사용자 지정 보호를 위한 기존 WAF 구성을 연결할 수 있습니다. 추가 요금 적용

## 사전 정의된 WAF 자동 생성

다음을 보호하기 위한 3 가지 관리 규칙이 포함되어 있습니다.

- 웹 애플리케이션에서 가장 흔히 발견되는 취약점.
- 애플리케이션 취약점을 발견한 악의적인 행위자.
- Amazon 내부 위험 인텔리전스를 기반으로 한 잠재적 위험.


## 웹 ACL

이 로드 맵런서에 적용할 기존 WAF 웹 ACL을 선택합니다. WAF 콘솔 $\square$에서 관련 웹 ACL을 관리할 수 있습니다.
251001_web_acl
1개 규칙 | Resource-level DDoS protection: Active under DDoS | 설명: -

---

# EC2 – Load Balancer

- WAF는 특정 서브넷에서 동작하는 것이 아닌 Region/Global에서 동작됨
- Web ACL만 생성해서 AWS Resources에 연결해서 사용해야 함

|  네트워크 해킹 정보 |  |  |  |  |  |   |
| --- | --- | --- | --- | --- | --- | --- |
|  로드 탭인서는 IP 주소 설정에 따라 선택한 서브넷의 대상으로 트래픽을 라우팅합니다. |  |  |  |  |  |   |
|  VPC 정보 |  |  |  |  |  |   |
|  로드 탭인서는 선택한 VPC 내에서 존재하고 확장됩니다. 또한 선택한 VPC는 Lambda 또는 프로세이스 대상으로 라우팅하거나 VPC 피어링을 사용하는 경우를 제외하고 로드 탭인서 대상을 호스팅해야 하는 위치의 |  |  |  |  |  |   |
|  가도 합니다. 대상의 VPC를 확인하려면 대상 그룹을 확인하세요. |  |  |  |  |  |   |
|  vpc-05fc4bde926a22096 (250930vpc) |  |  |  |  |  |   |
|  10200379 |  |  |  |  |  |   |
|  IP 통 정보 |  |  |  |  |  |   |
|  선택적으로 IP644 툴을 로드 탭인서 IP 주소의 기본 스스로 구성하도록 선택할 수 있습니다. Amazon VPC IP 주소 관리자 콘솔에서 툴을 생성하거나 확인합니다. |  |  |  |  |  |   |
|  ☐ 미만의 IPv4 주소에 IP644 툴 사용 |  |  |  |  |  |   |
|  선택한 IP644 툴이 미만의 IPv4 주소의 기본 소스가 됩니다. 툴이 고갈되면 4bit에서 IPv4 주소를 할당합니다. |  |  |  |  |  |   |
|  가용 영역 및 서브넷 정보 |  |  |  |  |  |   |
|  가용 영역을 2개 이상 선택하고 각 영역에 대해 서브넷을 선택합니다. 로드 탭인서 노드는 선택한 각 영역에 배치되며 트래픽에 따라 자동으로 확장됩니다. 로드 탭인서는 선택한 가용 영역의 대상으로만 트래픽을 라우팅합니다. |  |  |  |  |  |   |
|  24비트 (128비트) 서브넷 |  |  |  |  |  |   |
|  로드 탭인서 IP 주소 요청에 해당하는 CEN 블록만 사용됩니다. 로드 탭인서를 효율적으로 확장하려면 사용 가능한 IP 주소가 8개 이상 할당합니다. |  |  |  |  |  |   |
|  subnet-0a11b06ebbe852869 |  |  |  |  |  |   |
|  IPv4 서브넷 CEN: 102003239 |  |  |  |  |  |   |
|  2개 이상의 서브넷을 지정해야 합니다. |  |  |  |  |  |   |

---

# EC2 - Load Balancer 

- WAF


## 네트워크 매핑 정보

로드 밸런서는 IP 주소 설정에 따라 선택한 서브넷의 대상으로 트래픽을 라우팅합니다.

## VPC | 정보

로드 밸런서는 선택한 VPC 내에서 존재하고 확장됩니다. 또한 선택한 VPC는 Lambda 또는 온프레미스 대상으로 라우팅하거나 VPC 피어링을 사용하는 경우를 제외하고 로드 밸런서 대상을 호스팅해야 하는 위치이 기도 합니다. 대상의 VPC를 확인하려면 대상 그룹 을 확인하세요.

## VPC 생성

IP 풀 | 정보
선택적으로 IPAM 풀을 로드 밸런서 IP 주소의 기본 소스로 구성하도록 선택할 수 있습니다. Amazon VPC IP 주소 관리자 콘솔 에서 풀을 생성하거나 확인합니다.
퍼블릭 IPv4 주소에 IPAM 풀 사용
선택한 IPAM 풀이 퍼블릭 IPv4 주소의 기본 소스가 됩니다. 풀이 고갈되면 AWS에서 IPv4 주소를 할당합니다.

## 가용 영역 및 서브넷 | 정보

가용 영역을 2 개 이상 선택하고 각 영역에 대해 서브넷을 선택합니다. 로드 밸런서 노드는 선택한 각 영역에 배치되며 트래픽에 따라 자동으로 확장됩니다. 로드 밸런서는 선택한 가용 영역의 대상으로만 트래픽을 라우팅합니다.

## $\square$ us-east-2a (use2-az1)

us-east-2b (use2-az2)
us-east-2c (use2-az3)
2 개 이상의 서브넷을 지정해야 합니다.

---

# EC2 - Load Balancer 

- WAF

네트워크 매핑 정보
로드 밸런서는 IP 주소 설정에 따라 선택한 서브넷의 대상으로 트래픽을 라우팅합니다.

## VPC 정보

로드 밸런서는 선택한 VPC 내에서 존재하고 확장됩니다. 또한 선택한 VPC는 Lambda 또는 온프레미스 대상으로 라우팅하거나 VPC 피어링을 사용하는 경우를 제외하고 로드 밸런서 대상을 호스팅해야 하는 위치이 기도 합니다. 대상의 VPC를 확인하려면 대상 그룹 을 확인하세요.

| vpc-74fe9f1d |
| :-- |
| 172.31.0.0/16 |

## IP 풀 정보

선택적으로 IPAM 풀을 로드 밸런서 IP 주소의 기본 소스로 구성하도록 선택할 수 있습니다. Amazon VPC IP 주소 관리자 콘솔 에서 풀을 생성하거나 확인합니다.
$\square$ 퍼블릭 IPv4 주소에 IPAM 풀 사용
선택한 IPAM 풀이 퍼블릭 IPv4 주소의 기본 소스가 됩니다. 풀이 고갈되면 AWS에서 IPv4 주소를 할당합니다.

## 가용 영역 및 서브넷 정보

가용 영역을 2 개 이상 선택하고 각 영역에 대해 서브넷을 선택합니다. 로드 밸런서 노드는 선택한 각 영역에 배치되며 트래픽에 따라 차등으로 확장됩니다. 로드 밸런서는 선택한 가용 영역의 대상으로만 트래픽을 라우팅합니다.

## 2 us-east-2a (use2-az1)

서브넷
로드 밸런서 IP 주소 유형에 해당하는 CIDR 블록만 사용됩니다. 로드 밸런서를 효율적으로 확장하려면 사용 가능한 IP 주소가 8개 이상 필요합니다.

## subnet-4ba1d622

IPv4 서브넷 CIDR: 172.31.0.0/20

## 2 us-east-2b (use2-az2)

서브넷
로드 밸런서 IP 주소 유형에 해당하는 CIDR 블록만 사용됩니다. 로드 밸런서를 효율적으로 확장하려면 사용 가능한 IP 주소가 8개 이상 필요합니다.

## subnet-9dd864e6

IPv4 서브넷 CIDR: 172.31.16.0/20

## $\square$ us-east-2c (use2-az3)

---

# EC2 – Load Balancer

- 대상 그룹 생성

### **리스너 및 라우팅** 정보

리스너는 사용자가 구성한 포트 및 프로토콜을 사용하여 연결 요청을 검사하는 프로세스입니다. 리스너에 대해 정의한 규칙에 따라 로드 밸런서가 등록된 대상으로 요청을 라우팅하는 방법이 결정됩니다.

#### **▼** 리스너 **HTTP/80**

|  프로토콜 | 포트  |
| --- | --- |
|  HTTP | 80  |
|   | 1-63335  |

#### **기본 작업** 정보

이온 규칙이 적용되지 않는 경우 기본 작업이 사용됩니다. 이 리스너의 도래하에 대해 기본 작업을 선택하세요.

#### **라우팅 액션**

|  |
| --- |
|  대상 그룹으로 전달 | |
|  대상 그룹으로 전달 정보 | |
|  대상 그룹을 선택하고 라우팅 자동차를 지정하거나 대상 그룹을 생성합니다. | |
|  대상 그룹 | |
|  대상 그룹 선택 | |
|  |
|  |
|  |
|  대상 그룹 추가 | |
|  |

#### **▶** 대상 그룹 추가

파크 4개의 대상 그룹을 더 추가할 수 있습니다.

#### **대상 그룹 고정성** 정보

소스 챗브시가 사용자 세션을 특정 대상 그룹에 바인딩할 수 있도록 합니다. 고정성을 사용하려면 클라이언트가 쿠키를 지원해야 합니다. 사용자 세션을 특정 대상에 바인딩하려면 대상 그룹 속성인 고정성을 하세요.

- 대상 그룹 고정성 제거

#### **리스너 태그 - 선택 사항**

리스너에 태그를 추가하는 것을 고려하십시오. 태그를 사용하면 AWIS 리스크를 분류하여 좀 더 쉽게 관리할 수 있습니다.

#### **리스너 태그 추가**

 최대 50개의 태그를 더 추가할 수 있습니다.

#### **리스너 추가**

파크 40개의 리스너를 더 추가할 수 있습니다.

---

# EC2 - Load Balancer 

- 보통 대부분 인스턴스 로 유형 지정
- 인스턴스의 IP를 가끔 바꿀 수도 있어서 인스턴스가 편리

1단계
그룹 세부 정보 지정
2단계
대상 등록

## 그룹 세부 정보 지정

로드 웰빈서는 요청을 대상 그룹의 대상으로 라우팅하고 대상에 대한 상태 확인을 수행합니다.

## 기본 구성

대상 그룹이 생성된 후에는 이 섹션의 설정을 변경할 수 없습니다.

## 대상 유형 선택

## 인스턴스

- 특정 VPC 내의 인스턴스에 대한 로드 웰빈성을 지원합니다.
- Amazon EC2 Auto Scaling $\square$ 을 사용하여 EC2 용량을 관리하고 크기를 조정할 수 있습니다.

IP 주소

- VPC 및 온트레피스 리소스에 대한 로드 웰빈성을 지원합니다.
- 동일한 인스턴스에 있는 여러 IP 주소 및 네트워크 인터페이스로의 라우팅을 지원합니다.
- 마이크로서비스 기반 아키텍처를 통한 유연성을 제공하여 애플리케이션 간 통신을 감소화합니다.
- IPv6 대상을 지원하여 중단 간 IPv6 통신 및 IPv4에서 IPv6로의 NAT를 활성화합니다.

Lambda 함수

- 단일 Lambda 함수로 라우팅을 지원합니다.
- Application Load Balancer에만 액세스할 수 있습니다.

Application Load Balancer

- Network Load Balancer가 특정 VPC 내에서 TCP 요청을 수락하고 라우팅할 수 있는 유연성을 제공합니다.
- Application Load Balancer로 고정 IP 주소 및 PrivateLink를 손쉽게 사용할 수 있습니다.

대상 그룹 이름

하이콘을 포함하여 최대 32차의 명숫자 문자를 사용할 수 있지만 이름이 하이콘으로 시작하거나 끝나지 않아야 합니다.

---

# EC2 – Load Balancer

- 대상 그룹 > 대상 그룹 생성

|  |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |  

---

# EC2 – Load Balancer

- 대상 그룹 > 대상 그룹 생성

EC2 > 대상 그룹 > group-ec2-251001-loadbalancer


---

# EC2 – Load Balancer

- 리스너 및 라우팅

## 리스너 및 라우팅

|  프로토콜 | 포트  |
| --- | --- |
|  HTTP | 60  |
|   | 1-60000  |

### 기본 작업

- 기본 UI/UX 지침되지 않는 경우 기본 작업이 사용됩니다. 이 리스너의 트래픽에 대해 기본 작업을 선택하세요.

### 라우팅 액션

|  대상 그룹으로 전달 | URL로 리스에선 | 고정 응답 방향  |
| --- | --- | --- |
|  대상 그룹으로 전달 |  |   |
|  대상 그룹을 선택하고 라우팅 사용자를 지정하거나 대상 그룹을 생성합니다. |  |   |

### 대상 그룹

|  group-m2-251001-loadbalance | HTTP | 1 | 100%  |
| --- | --- | --- | --- |
|  대상 그룹의 |  |  |   |
|  1 |  |  |   |
|  2 |  |  |   |
|  3 |  |  |   |

### 대상 그룹 추가

- 최대 4개의 대상 그룹을 더 추가할 수 있습니다.

### 대상 그룹 고정성 성능

- 로드 웹사이트 사용자 세션을 특정 대상 그룹에 배정받을 수 있도록 합니다. 고정성을 사용하려면 클라이언트가 부지를 지원해야 합니다. 사용자 세션을 특정 대상에 배정당하려면 대상 그룹 속성만 고정성을 하세요.
- 대상 그룹 고정성 허기

### 리스너 테그 - 선택 사항

- 리스너에 테그를 추가하는 것을 고려하십시오. 테그를 사용하면 AWS 리소스를 분류하여 좀 더 쉽게 관리할 수 있습니다.

### 리스너 테그 추가

- 최대 30개의 테그를 더 추가할 수 있습니다.

### 리스너 추가

- 최대 40개의 리스너를 더 추가할 수 있습니다.

---

# EC2 – Load Balancer

• 로드 밸런서 생성 완료

EC2 > 로드 밸런서 > 251001-load-balancer

EC2
데시보드
EC2 공유할 보기
이벤트

▼ 인스턴스
인스턴스
인스턴스 유형
시작 템플릿
소형 요형
Savings Plans
매우 인스턴스
전용 호스트
용량 매약

▼ 이미지
API
API 카탈로그

▼ Elastic Block Store
볼륨
스냅샷
수명 추가 관리자

▼ 네트워크 및 보안
보안 그룹
전략적 IP
배치 그룹
키 떼어

EC2 > 로드 밸런서 > 251001-load-balancer


---

# WAF – Load Balancer

## WAF > Associated AWS resources

### WAF & Shield

- **WAF & Shield**
  - **Success**
    - Successfully associated web ACL with 251001-load-balancer.

- **AWS WAF**
  - Getting started
  - **Web ACLs**
  - Bot control dashboard
  - Application integration
  - IP sets
  - Regex pattern sets
  - Rule groups
  - Add-on protections

- **AWS WAF > Web ACLs > 251001_web_acl**
  - **251001_web_acl**
    - `arn:aws:wafv2:us-east-2:274130523831:regional/webacl/251001_web_acl/621e6ab8-20bb-40db-919b-59fc4ca53b23`
  - `< Associated AWS resources Custom response bodies Logging and metrics Sampled requests CloudWatch >`

- **Associated AWS resources**
  - **Disassociate**
    - **Add AWS resources**
  - ☑ *Find associated AWS resources*
  - ☐ 1
  - ☐ 0

- **Name**
- **Resource type**
- **Region**
- ☐ 251001-load-balancer
- **Application Load Balancer**
- **US East (Ohio)**

Switch to AWS WAF Classic
