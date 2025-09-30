
# 방화벽, IDS / IPS

---

## 1. Firewall (방화벽)

- 특정 포트, IP, 프로토콜 등 여러 기준으로 통제를 제어하는 보안 시스템

---

## 2. IDS (Intrusion Detection System)

- 침입 탐지 시스템
- **종류**
  - **HIDS (Host-based IDS)**: 호스트 기반, 개별 컴퓨터 내부 시스템 감시
  - **NIDS (Network-based IDS)**: 네트워크 기반, 트래픽 감시

---

## 3. IPS (Intrusion Prevention System)

- 침입 방지 시스템
- IDS의 고급화 버전
- 침입 탐지뿐만 아니라 사전에 차단 및 방어 기능 수행

---

## 4. 리눅스에서 IDS / IPS

### 4.1 주요 툴
- **iptables** → IPS
- **Snort** → IDS

### 4.2 iptables 기본 문법
```
iptables [A. 규칙] [B. 체인명] [C. 옵션] [D. 타겟]
```

- **A. 규칙**
  - `-A`: 새로운 규칙 맨 아래 추가
  - `-I`: 새로운 규칙 맨 앞 추가
  - `-D`: 규칙 삭제
  - `-F`: 모든 규칙 삭제
  - `-L`: 규칙 출력

- **B. 체인명**
  - `INPUT`: 외부 → 내부 패킷
  - `OUTPUT`: 내부 → 외부 패킷
  - `FORWARD`: 서버를 거쳐가는 패킷

- **D. 타겟**
  - `ACCEPT`: 허용
  - `DROP`: 무반응 거부
  - `REJECT`: 거부 메시지 전송
  - `LOG`: syslog 기록
  - `RETURN`: 패킷 처리 계속

### 4.3 예시
```bash
iptables -A INPUT -p tcp -s 195.2.3.5 --sport 31523 -j DROP
```
- 출발지 IP가 `195.2.3.5`, 출발지 포트가 `31523`인 패킷 차단

---

## 5. 리눅스 IPS 실습

- Victim(localhost) 웹페이지 정상 동작 여부 우선 확인
- Attacker(192.168.26.130) → Victim(192.168.26.129) 접속 테스트
- 주요 포트
  - HTTP: 80
  - HTTPS: 443
- iptables 설정 예시:
```bash
iptables -A INPUT -p tcp -s 192.168.26.130 --dport 80 -j DROP
```

- `--dport`: 목적지 포트 지정 (외부에서 내부 접근 제어)

---

## 6. 리눅스 IDS (Snort)

- 실시간 트래픽 분석 및 패킷 로깅 가능
- 오픈소스, 리눅스/윈도우 지원
- IDS / IPS 가능 (윈도우는 IDS만 지원)

### 6.1 Snort 역사
- 1998: 패킷 스니퍼로 시작
- 2001: Sourcefire 설립, 상용 버전 출시
- 2009: IPv6 지원
- 2013: Cisco가 Sourcefire 인수

### 6.2 Snort 규칙
- 형식:
```
[동작] [프로토콜] [출발지IP] [출발지포트] -> [목적지IP] [목적지포트] (옵션)
```
- 예시:
```bash
alert icmp any any -> any any (msg:"PING TEST"; sid:1000001;)
```
- `msg`: 이벤트 이름
- `sid`: 규칙 ID
  - 99 이하: 시스템 예약
  - 100 ~ 1,000,000: Snort 지정
  - 1,000,001 이상: 사용자 지정

### 6.3 실행 예시
```bash
snort -c /etc/snort/snort.lua -R /etc/snort/rules/local.rules -i eth0 -A alert_fast
```

---

## 7. 참고 자료

- 방화벽/IDS/IPS 정의 및 차이
- iptables(IPS)와 snort(IDS) 실습
- Snort 관련 블로그 및 튜토리얼
  - [Snort IDS Setup and Testing Tutorial](https://www.linkedin.com/pulse/snort-ids-setup-testing-tutorial-wilfridus-handaya-s2pkc/)
  - [네이버 블로그 - snort](https://catchingitsecure.tistory.com/4)
  - [Velog - iptables와 snort 실습](https://velog.io/@sot_sky/iptablesIPS%EC%99%80-snortIDS-%EC%8B%A4%EC%8A%B5)
  - [Naver Blog - Snort 예시](https://m.blog.naver.com/aladdin76/223394899408)