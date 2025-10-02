# CSP와 AWS-SEC

`CSP별 보안 서비스 실습`이라는 제목으로 진행된 강의입니다.
조금 더 이해하기 편하게 강의 자료 기반으로 제가 이해한 바를 노트로 작성했습니다.
강의 시간엔 `AWS` 대시보드에서 설정하는 방법, 팁을 알려주셨는데요,
이에 앞서 용어와 기능 목적부터 익히고자 간략히 정리합니다.

이 글은 다음 내용을 다룹니다.

- Cloud Service Provider 개요
- AWS Security Service
- Access Control List
- IAM / IAM Identity Center (`AWS SSO`)

*이탤릭체는 인용입니다.*

## CSP

> Cloud Service Provider

*대부분의 클라우드에서 보안 관련 서비스는 이름만 다르고 기능과 역할은 대동소이*합니다.
대부분의 `CSP`는 서로 비슷한 보안 기능을 이미 갖추고 있습니다.
그럼에도 *"**한국의 법적, 사회적 특수한 상황**을 고려하여 **해외** 혹은**국내** `CSP`를 사용하거나 **별도의 내부 클라우드 및 데이터 센터**를 적재적소에 맞게 사용해야"*한다고 합니다. 정부 규제를 고려하면 일리가 있습니다. 금융, 국가 기밀 등 보안이 중요 사안을 모두 해외 기업에 의존하기는 어려울 것 같습니다.

#### MSP

- 클라우드 도입 컨설팅, 운영, 기술 지원 업체라고 합니다.
- MSP가 보통 CSP에 대한 컨설팅을 진행한다고 합니다.
- 클라우드 네트워크 설계에 따라 비용이 천차만별이 될 수 있기 때문에 컨설팅(설계)/운영을 컨설팅한다고 합니다.

---

## AWS 해킹 실제 사례

> *2-Factor-Authentication(2차 인증)을 걸지 않고 `ROOT` 계정으로 사용하다가 해커가 대량의 ECS를 짧은 시간에 생성하여 과금 폭탄 발생*

- 1주일도 안되어 1000만원 요금 발생
    - 코인 채굴/좀비 PC 활용
    - 과금 폭탄 해킹 사례를 상세히 공유해주셨습니다.
        - 모든 리전의 1~2k 클러스터 보안 정책을 직접 지워야 했는데, `selenium`으로 자동화하셨다고 하여 인상 깊었습니다.
- `AWS` 뿐만 아니라 `Vercel` 등 `AWS` 기반 `SaaS` 제품군에서도 심심찮게 발생합니다.
    - https://www.youtube.com/watch?v=SCIfWhAheVw&pp=ygUVcHJpbWVhZ2VuIHZlcmNlbCBiaWxs
    - https://www.youtube.com/watch?v=jsuNjCAngnQ&t=1060s&pp=ygUVcHJpbWVhZ2VuIHZlcmNlbCBiaWxs0gcJCfsJAYcqIYzv

## AWS Secirity Service

`CSP` 중 하나인 `Amazon Web Service` 보안 서비스에 대해서 학습했습니다.

### AWS 보안 서비스 분류

반복해서 볼 내용들이 있으니 눈에 익히기 위해 정리합니다.
강의에서 언급된 기능 위주로 볼드 처리했습니다.

1. 데이터 보호 (**Data Protection**)
    - Key Management Service (KMS): 암호화 키 생성 및 제어 관리
    - CloudHSM: 하드웨어 기반 키 저장소
    - Macie: 데이터를 탐지·분류·보호
    - Server-side Encryption: 유연한 데이터 암호화 옵션 제공
    - Encrypted Boot & EBS volumes: 암호화된 부팅 및 EBS 볼륨 지원

2. 신원·디렉토리·액세스 관리 (Identity, Directory, and Access)
    - **IAM: 사용자 접근 및 암호화 키 관리**
    - **Single Sign-On (SSO)**: AWS 계정 및 비즈니스 앱을 위한 클라우드 기반 `SSO`
    - Directory Service: Microsoft Active Directory를 호스팅 및 관리
    - Organizations: 여러 계정의 설정 관리
    - Resource Access Manager: 계정 간 리소스 공유
    - Secrets Manager: 보안 정보(비밀) 회전·관리·검색
    - Cognito: 앱을 위한 사용자 신원 관리

3. **탐지** 및 관리 제어 **Detective** Controls and Management
    - **Security Hub**: 보안 알림 중앙 관리 및 컴플라이언스 자동화
    - **GuardDuty**: 지속적인 위협 탐지 및 모니터링
    - Config: 리소스 인벤토리 및 변경 사항 추적
    - CloudTrail: 사용자 활동 및 API 사용 추적
    - CloudWatch: 리소스와 애플리케이션 모니터링
    - Inspector: 애플리케이션 보안 분석
    - Artifact: AWS 컴플라이언스 보고서 셀프 서비스

4. 네트워크 및 인프라 (Networking and Infrastructure)
    - **Virtual Private Cloud** (VPC): 격리된 클라우드 리소스
    - VPC Flow **Logs**: 네트워크 흐름 로그 기록
    - Certificate Manager (ACM): SSL/TLS 인증서 발급·관리·배포
    - ACM Private CA: 사설 인증 기관 관리
    - Service Catalog: 표준화된 제품 생성 및 사용
    - Launch Templates: 리소스 배포 표준화

5. 애플리케이션 및 트래픽 보안 (Application & Traffic Security)
    - **WAF** (Web Application Firewall): 악성 웹 트래픽 필터링
    - **Shield**: DDoS 방어
    - Firewall Manager: **여러 계정**의 WAF 규칙 관리
    - PrivateLink: AWS에서 호스팅된 서비스에 안전하게 접근

앞선 강의에서 배운 `IDS`/`IPS` 개념으로 분류하기엔 그 경계가 모호한 면이 있다고 합니다.
*`IDS`도 `IPS` 기능을 갖고 역으로도 마찬가지로 제공하는 경우가 많다*고 해주신 게 떠올랐습니다.
탐지 중심 기능은 `IDS`로 분류할 수 있겠습니다.

```bash| 분류                                      | 서비스 예시 (역할 중심)                                                                                  |
|-------------------------------------------|----------------------------------------------------------------------------------------------------------|
| 탐지 중심(Detection / Detective)          | GuardDuty (지속적 위협 탐지), Inspector (취약성 탐지), Config / CloudTrail / CloudWatch (이상 행위 감지) |
| 차단 / 완화 중심(Prevention / Mitigation) | WAF (HTTP 요청 필터링), Shield (DDoS 완화), AWS Network Firewall 등 네트워크 수준 방화벽 솔루션          |
| 관리 / 통합 중심                          | Security Hub (발견 데이터 수집/분석), Firewall Manager (방어 규칙 일관 적용)                             |
| 네트워크 연결 / 접근 제어 중심            | PrivateLink (인터넷 노출 감소), VPC Security Groups / ACL 등                                             |
```



### IAM / Access Key

IAM `Identity and Access Management`

AWS 권한 설정 실습 예제를 보며 `IAM`을 말그대로 접근 관리 서비스로 이해했습니다.

- 액세스 키 ID (Access Key ID): ID 역할을 하며, 인증 요청의 출처를 식별하는 정보입니다.
    - **중요 : 실습 시 Access Key를 공유하면 안됩니다! 유출 시 키/계정 삭제 필요합니다**
    - *"**루트 사용자에게 액세스 키가 없는 것을 권장**"*한다고 합니다.
- 시크릿 액세스 키 (Secret Access Key): 비밀번호 역할을 하며, 본인임을 증명하는 비밀 정보입니다.

#### 주요 특징 및 용도

- 프로그래밍 방식 접근: `AWS CLI`, `AWS API`, `AWS SDK` 등 AWS 앱, 스크립트에서 `AWS` 서비스에 접근하고 **리소스를 제어할 때 사용**됩니다.
    - 예를 들어 게시판에 사진을 올리면, AWS 저장소에 이미지를 저장하기 위해서 키를 함꼐 요구할 수 있습니다.
- 장기 자격 증명: 웹 콘솔 로그인 시 사용하는 비밀번호와 달리, **액세스 키는 만료되지 않고 계속 사용할 수 있는 자격 증명**입니다.
- 보호 방법: 액세스 키는 AWS IAM 사용자를 통해 관리하며, 시크릿 액세스 키는 안전한 곳에 보관하고 절대 공유하지 않도록 주의해야 합니다.

### SSO

자주 보이는 용어라 한번 읽어봤습니다.

*AWS Single Sign-On(SSO)은 1회 사용자 인증으로 다수의 애플리케이션 및 웹사이트에 대한 **사용자 로그인을 허용하는 인증 솔루션**입니다. **요즘 사용자들은 브라우저에서 직접 애플리케이션에 자주 액세스**하기 때문에 조직은 **보안 및 사용자 경험 모두를 개선**하는 액세스 관리 전략에 우선 순위를 둡니다. **SSO는 한 번 자격 증명이 검증된 사용자에게는 반복되는 로그인 없이** 모든 암호 보호 리소스에 액세스하도록 하여 보안과 사용자 경험을 모두 충족할 수 있습니다.*

브라우저보다 `SSO`를 서버에서 관리하면 유용하겠다고 이해했습니다.

https://aws.amazon.com/ko/what-is/sso/

### ACL

Access Control List
접근    제어     리스트

줄임말이 많아서 혼동되는데, 권한 리스트로 이해하겠습니다.
AWS 한국어 자료가 많아서 좋습니다.
아래 문서에서 `ACL`에 대한 내용만 편집 및 밑줄을 치며 읽었습니다. 어렵네요.

https://docs.aws.amazon.com/ko_kr/vpc/latest/userguide/vpc-network-acls.html

*네트워크 액세스 제어 목록(ACL)은 서브넷 수준에서 특정 인바운드 또는 아웃바운드 트래픽을 허용하거나 거부합니다. VPC에 대한 기본 네트워크 ACL을 사용하거나 보안 그룹에 대한 규칙과 유사한 규칙을 사용하여 VPC에 대한 사용자 지정 네트워크 ACL을 생성하여 VPC에 보안 계층을 추가할 수 있습니다.*

***네트워크 ACL을 사용해도 추가 요금이 부과되지 않습니다.***

*다음은 시작하기 전에 네트워크 **ACL에 대해 알아야 할 기본 사항**입니다.*

1. 네트워크 ACL 연결
    - VPC에 있는 **각 서브넷을 네트워크 ACL과 연결**해야 합니다. 
    서브넷을 네트워크 ACL에 명시적으로 연결하지 않을 경우, 서브넷은 **기본 네트워크 ACL에 자동적으로 연결**됩니다.
- 사용자 지정 네트워크 ACL을 생성하고 서브넷과 연결하여 **서브넷 수준에서 특정 인바운드 또는 아웃바운드 트래픽을 허용하거나 거부**할 수 있습니다.
- 네트워크 ACL을 **여러 서브넷과 연결**할 수 있습니다. 
    - 그러나 **서브넷은 한 번에 하나의 네트워크 ACL에만 연결**할 수 있습니다. 
    - 네트워크 ACL을 서브넷과 연결하면 이전 연결은 제거됩니다.

2. 네트워크 ACL 규칙
- 네트워크 ACL에는 인바운드 규칙과 아웃바운드 규칙이 있습니다. 
- 네트워크 ACL당 보유할 수 있는 규칙 수에는 **할당량(또는 제한**)이 있습니다. 
- 각 규칙에서는 트래픽을 허용하거나 거부할 수 있습니다. 각 규칙에는 1부터 32766까지 번호가 있습니다. 
- 규칙은 트래픽 허용 또는 거부가 결정될 때 **가장 낮은 번호의 규칙부터** 순서대로 평가됩니다. 
- 트래픽이 규칙과 일치하면 규칙이 적용되며 추가 규칙은 평가되지 않습니다. 
- 필요한 경우 나중에 새 규칙을 삽입할 수 있도록 증분 방식으로(예: 10 또는 100 단위씩 증분) 규칙을 생성하여 시작하는 것이 좋습니다.
  - 이 부분은 잘 모르겠습니다. 실습 때 익혀보겠습니다.
- 네트워크 ACL 규칙은 트래픽이 서브넷 내에서 라우팅될 때가 아니라 **서브넷에 들어오고 나갈 때 평가**됩니다.
