# 방화벽, IDS / IPS

IDS/IPS 강의 노트입니다.

노트를 작성하며 추가 개념을 함께 살펴보았습니다.
-`ICMP`에 관련한 노트를 포함합니다.

---

## TLDR

- **IDS**: Detection, 탐지에 관한 기술.
- **IPS**: Prevention, 예방/보호에 관한 기술.

- 오늘날엔 `IDS/IPS`가 상호 기능을 모두 제공하여 구분이 모호하지만, 자격증 시험에 종종 나온다고 합니다.

이번 강의에선 방화벽의 개념, `IPS/IDS`, `Linux`의 방화벽 설정 등 기본적인 보안 프로그램과 `IPS/IDS` 명령어에 대해 학습했습니다.

---

## 1. Firewall

- 방화벽
- 특정 포트, IP, 프로토콜 등 여러 기준을 가지고 통제를 제어함

## 2. IDS

- Intrusion Detection System
- IDS
- HIDS (Host based IDS)
  - 호스트 기반 (컴퓨터 자체 내부 시스템)
- NIDS (Network based IDS)
  - 네트워크 기반

## 3. IPS

- Intrusion Prevention System
- IDS의 고급화 버전
- 침입 탐지뿐만 아니라 **사전에 차단 및 방어 기능** 수행

## 4. 리눅스에서 IDS IPS

리눅스에서 사용되는 주요 IPS/IDS 툴은 다음과 같습니다:
- **iptables** → IPS
- **Snort** → IDS
*note: `Snort`의 경우 면접에서 종종 물어보기에 실제로 사용해보는 것을 권장한다고 합니다.

### `Iptables` 기본 문법

```bash
iptables [A. 규칙] [B. 체인명] [C. 옵션] [D. 타겟]
```

- **A. 규칙**
  - `-A`: 새로운 규칙 맨 아래 추가
  - `-I`: 새로운 규칙 맨 앞 추가
  - `-D`: 특정 규칙을 삭제
  - `-F`: 모든 규칙을 삭제
  - `-L`: 현재 적용된 규칙을 출력

- **B. 체인명**
  - `INPUT`: 외부 → 내부 패킷
    - 예: 외부 사용자가 서버의 22번 포트로 SSH 접속 시도
  - `OUTPUT`: 내부 → 외부 패킷
    - 예: 서버가 외부 웹사이트에 HTTP 요청을 보낼 때
  - `FORWARD`: 서버를 거쳐가는 패킷
    - 예: 서버가 게이트웨이 역할을 하여 다른 네트워크로 패킷 전달

`INPUT/OUTPUT` 체인과 함께 인바운드, 아웃바운드 개념을 살펴봅니다.

- 인바운드 (Inbound) : 외부에서 내부로 들어오는 트래픽. 주로 `INPUT` 체인과 연관됩니다.
    - 서버가 외부 요청을 받을 때, 예: 웹서버의 80포트 접근
- 아웃바운드 (Outbound) : 내부에서 외부로 나가는 트래픽. 주로 `OUTPUT`과 관련있습니다.
    - 서버가 외부로 요청을 보낼 때, 예: 서버가 업데이트 서버로 접속

**주의**
- 인바운드 = `INPUT`만은 아님
    - 인바운드 트래픽이 반드시 INPUT에서 끝나는 건 아님.
	- 라우터나 방화벽처럼 패킷을 중간에 전달만 하는 장비라면, 외부 → 내부로 들어온 패킷이 `FORWARD` 체인에서 처리될 수 있음.
- 아웃바운드 = `OUTPUT`만은 아님
    - 서버 자체에서 나가는 건 OUTPUT이 맞지만, 내부 PC → 외부 인터넷 트래픽을 **라우터가 중계할 때**는 `FORWARD`에서 걸림.
- `IDS > snort`에서 `--dprot | --sport`와 함께 혼동되어 다시 살펴볼 예정입니다.

- **D. 타겟**
  - `ACCEPT`: 허용
  - `DROP`: 무반응 거부
  - `REJECT`: 거부 메시지 전송
  - `LOG`: syslog 기록
  - `RETURN`: 패킷 처리 계속

`DROP` vs `REJECT`
- `DROP`: 차단 당한 사용자가 자신의 차단 여부를 알 수 없습니다.
- `REJECT`: 차단 당한 사용자에게 차단 사실을 알립니다.

### 예시

```bash
Iptables –A INPUT –p tcp –s 195.2.3.5 --sport 31523 –j DROP
```
- 발신지 IP(`-s`)가 `195.2.3.5`, 발신지 포트가 `31523`인 패킷 거부(`DROP`)
- `--dprot`는 도착지 포트입니다.
- `DROP` > 거부 메시지 전송 X

---

### LINUX 관리자 권한

- `root`
  - 윈도우의 관리자Administrator와 동일한 개념
  - 방화벽 관련 정책을 실행하기 위해 관리자 권한이 필요함
- `su`
  - 관리자 권한 상승 리눅스 명령어
- `sudopasswd`
  - root 패스워드를 신규 등록
- Root의 패스워드를 등록한 후 `su`가 정상적으로 실행됨예: `su > root`
- `Iptables` 명령어가 정상적으로 실행되는 것을 확인할 수 있음

---

### nftables

- 2022년 이후로 `iptables` 대신 `nftables`가 **기본 방화벽 설정**으로 되어 있는 경우가 있습니다.
- 아무것도 출력되지 않으면 방화벽 정책 없다는 뜻입니다.

---

### 기능 동작 테스트

- `ifconfig`IP 확인 명령어 (inet)
  - 리눅스에서 `ifconfig` 명령어는 Windows의 `ipconfig` 명령어에 해당합니다.
  - 두 명령어 모두 네트워크 인터페이스의 IP 주소, 서브넷 마스크, MAC 주소 등의 네트워크 구성을 확인하고 설정하는 데 사용됩니다.
  - 리눅스에서는 `ifconfig`보다 더 강력하고 최신 기능의 `ip` 명령어가 권장됩니다.
- 환경:
  - Attacker
  - Victim (192.168.26.129)

#### 테스트 시나리오

- Attacker PC로 Victim (192.168.26.129) 홈페이지 접속 테스트
- Victim(localhost)에서는 웹페이지가 잘 열리는지 우선 확인할 것
  > 홈페이지 동작 여부는 1순위로 localhost 체크가 우선입니다.
  - 기본적이라 자주 실수 할 수 있다고 합니다.
- Attacker(192.168.26.130) > victim(192.168.26.129) 접속 확인
- `KaliLinux`를 통해 두 대의 가상머신`VM`에서 각각 서버를 열어 실행할 수 있습니다.


---

### HTTP 포트

- HTTP > 포트번호??
- HTTP > 80 포트 (저번 강의 자료 Web 에서 설명)
- HTTPS > 443 포트 
  (CLOUDFLARE와 같은 플랫폼 이용해서 인증서(`TLS/SSL`) 세팅해서 구축하기도 함)

❓ `TLS/SSL`

- **TLS/SSL은 전송 계층(OSI L4)과 응용 계층(L7) 사이에서 사용되는 보안  프로토콜**입니다.
- LS/SSL 인증서는 웹사이트와 사용자 브라우저 사이의 인터넷 연결을 암호화하여 **데이터를 안전하게 보호하는 디지털 파일 (인증서)**입니다."

### 방화벽 설정 예시

```bash
Iptables –A INPUT –p tcp –s 192.168.26.130 --sport 80 –j DROP
        
        -A :[새로운 규칙 추가]
        INPUT: 외부 → 내부 패킷
        -p: tcp 프로토콜
        -s: 발신지 IP가 192.168.26.130
        --sport: 발신지 포트 80
        -j DROP: 해당 조건(192.168.26.130 IP, TCP 프로토콜, 발신지 포트 80)에 해당하는 패킷을 차단(버림).
        즉, 규칙과 일치하는 패킷을 받아들이지 않고 완전히 무시하여 송신자에게 응답하지 않음.
```

- Attacker가 victim 웹서버를 접속하지 못하도록 `iptables`로 방화벽을 설정합니다.


---

### 로그 확인

- `/var/log/apache2/access.log`
  192.168.26.130 확인

---

### 명령어 오류 및 수정

```bash
iptables –A INPUT –p tcp –s 192.168.26.130 --sport 80 –j DROP
```

- `CLI`의 인자(param)가 잘못되었습니다.

```bash
iptables –A INPUT –p tcp –s 192.168.26.130 --dport 80 –j DROP
```

- **`INPUT` 체인에서는 보통 목적지 포트 (`dport`)를 다룬다고 합니다.**
- `Sport`(`src port`소스포트)를 다루는 경우는 보통 로컬 프로세스(localhost)에서 처리할 때 사용
- `Dport` > **외부에서 내부로 접근할 때 처리**

---

### 방화벽 정책 삭제

```bash
sudo nftflush ruleset
```

- 방화벽 정책 삭제
- 다시 접속 되는 것을 확인

---

## Snort (리눅스 IDS)

앞서 말씀드린 것처럼 `Snort`를 해보는 것을 권장한다고 하십니다.  
`Snort`의 주요 기능은 다음과 같습니다:
- 네트워크상의 실시간 트래픽 분석 및 패킷 로깅 가능
- **오픈소스**
- 리눅스 / 윈도우 둘 다 가능
- 패킷 스니퍼 (훔쳐보기)
- 패킷 로거 > 모니터링 / 로그 저장
- IDS / IPS도 가능하긴 함
- 리눅스 IPS 지원 O / 윈도우 IPS 지원 X

---

### Snort 역사

- 1998: 패킷 스니퍼
- 2001: sourcefire 설립 / 상용 버전 출시
- 2009: `ipv6` 지원
- 2013: `Cisco` > `sourcefire` 인수
  `Cisco` 미국 상장사로 네트워크계의 강자
  - 네트워크 자격증을 주로 주관하는 시험이 많음
  - `Cisco` 계열 네트워크 장비 솔루션 등 많음

---

### Snort 정책

- `Iptables`, `nftable`(`nft`) 와 유사함

---

### 설치 및 버전 확인

```bash
apt-get install snort
```

```bash
snort --version
```

- (생각보다 버전체크하는게 매우 중요할 수 있음)

---

### 편집기

- Gedit / Windows 메모장 같은 직관적인 편집기
- vi

---

### Snort rules

- snort rules 예시: `gedit local.rules`

```bash
[동작] [프로토콜] [출발지IP] [출발지포트] -> [목적지IP] [목적지포트] (옵션들)
alert icmp any any -> any any (msg:"PINGTEST"; sid:1000001;)
```

- `msg`: 이벤트명. 예시에서는 "PINGTEST"를 사용합니다.
- `sid`:
  - 99 이하: 시스템 예약
  - 100 ~ 1,000,000 이하: snort 자체 지정
  - 1,000,001 이상: 사용자 지정

#### ICMP

추가적으로 `ICMP` 프로토콜과 관련된 네트워크 개념에 대해 알아보았습니다.

- OSI 계층의 **네트워크 계층**에 해당하는 프로토콜입니다. 
- 데이터가 목적지에 도달하는지 여부를 확인하기 위해 사용됩니다.
- 주요 목적은 오류 보고입니다. 연결을 실패하는 경우 오류를 생성하여 두 장치에 공유합니다.
- 보조 용도는 **네트워크 진단**입니다. 터미널 유틸인 `traceRoute`와 `ping`은 모두 `ICMP`를 사용하여 작동합니다.
  - `traceRoute`: 요청과 응답 사이의 라우팅 경로를 표시하는 데 사용됩니다.
    - 라우팅 경로는 요청이 대상에 도달하기 전 **통과해야 하는 연결된 라우티의 실제 물리적 경로입**니다. `traceRoute`는 라우팅 중 각 홉에 필요한 **시간**을 보고합니다. 네트워크 지연 원인 파악에 사용됩니다.
    - `Hob`: 한 라우터와 다른 라우터 간의 여정을 '홉'이라고 합니다.
  - `ping`: `traceRoute`의 단순화 버전입니다. 
    - 두 장치간의 연결 속도를 테스트
    - 데이터 패킷이 대상에 도달하고 발신지로 돌아오는 데 걸리는 **시간**을 측정하는 **메트릭**입니다.
    - `ICMP` 에코 요청 및 에코 응답 메시지는 일반적으로 **`ping`을 수행하기 위해 사용**됩니다.
- 간단한 원리:
  -  `IP`와 달리 `ICMP`는 `TCP`, `UDP`와 같은 **전송 계층 프로토콜 (Transport Layer, OSI L4)**과 연결되지 않습니다.
  - `ICMP`는 *연결이 없는 프로토콜*이므로 메시지를 보내기 전 다른 장치와의 연결을 수행하지 않습니다. 즉 `TCP handshake` 수행하여 통신 양측의 수신 준비를 확인하지 않습니다.
  - 장치의 특정 포트를 대상으로 하는 것을 허용하지 않습니다.
  - 이러한 `ICMP`의 속성을 이용해 `ICMP flood attack`, `Ping of death` 공격을 수행합니다.

`Cloudflare`의 문서를 읽은 뒤 직접 작성했습니다.  
함께 살펴보면 좋은 자료가 많습니다.

참조:

- 네트워크 계층 : https://www.cloudflare.com/ko-kr/learning/network-layer/what-is-the-network-layer/
- `ICMP`: https://www.cloudflare.com/learning/ddos/glossary/internet-control-message-protocol-icmp/.

---

### Snort 실행 명령어와 버전 확인

```bash
snort –c /etc/snort/rules/local.rules
```

- Snort 버전 확인하는게 매우 중요합니다.
  - `Snort 2`와 `Snort 3` 버전 사이에 문법, 사용법, 설치경로 등 차이가 많기 때문이라고 합니다.
- 과거 블로그 혹은 서적에는 snort2 기준으로 기술되어있고, kali-linux 설치된 것은 snort3 이기 때문에 에러 발생
- 사용 중인 버전에 맞게 검색하며, 가급적 최신 글 (근 1년)로 검색하는 것이 좋습니다.

---

### 네트워크 테스트

- Attacker > victim (192.168.26.129)
- `PING` (`ICMP`)

---

### 문제 해결 팁

- Alarm이 안 뜨는 이유???
- > 삽질하기 전에 VMware take snapshot 권장 사용할 것
  >
- 나중에 문제 생기면 이전으로 돌아갈 수 있는 유용한 기능

---

### 설정 검증 명령어

- `-T` / 설정 검증 명령어
- 블로그에 있는 명령어 그대로 사용하지 말고 `path` 같은 경우 로컬 환경에 맞게 설정해야 합니다.

---

### Snort rules (탐지 규칙)

- Snort 제대로 설정되는 경우

```bash
snort -c /etc/snort/snort.lua -R /etc/snort/rules/local.rules -i eth0 -A alert_fast
```

---

읽어주셔서 감사합니다!