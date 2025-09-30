# 네트워크 패킷 분석 & 트래픽 모니터링

---

## 1. Kali Linux 시작 전 주의사항
- 로그아웃되는 것이 생각보다 번거로움
- 시스템이 잠자기 모드로 갈 때 Lock screen 발생

---

## 2. Wireshark

### 2.1 개요
- 네트워크 패킷 분석 대표 툴
- 웹 트래픽 분석 가능
- 다운로드: [Wireshark • Go Deep | Download](https://www.wireshark.org/download.html)
- 웹 브라우저 개발자도구, Fiddler 활용 가능

### 2.2 기본 정보
| 항목 | 설명 |
|------|------|
| No | 패킷 수집된 순서 |
| Time | 수집된 시간 |
| Source | 출발지 |
| Destination | 목적지 |
| Protocol | 프로토콜 |
| Length | 패킷 길이 |
| Info | 패킷 정보 |

### 2.3 필터링 예제

#### IP 필터링
- `ip.src==127.0.0.1` : 출발지
- `ip.dst==127.0.0.1` : 목적지
- `ip.addr==127.0.0.1` : 출발지+목적지

#### 포트 필터링
- `tcp.srcport==80` : 출발지 포트
- `tcp.dstport==80` : 목적지 포트
- `tcp.port==80` : 출발지+목적지

#### 데이터 길이 및 값 필터링
- `data.len>0` : 데이터가 있는 패킷
- `data[4]==0x11 and data[10]!=0x01` : 특정 값 포함 패킷

#### 기타 다양한 필터 옵션
- `eth.addr==[맥주소]` : MAC 주소 필터
- `!tcp.port` : 특정 포트 제외
- `ip.src!=10.0.0.1` : 특정 출발지 IP 제외

### 2.4 실습 환경
- VM에서 수행 추천
  - Host에서는 다양한 프로그램 패킷이 혼합되어 분석 어려움
  - 시스템 파괴 걱정 없이 공격 테스트 가능
  - 기본적으로 `eth0`에서 분석
  - 그래프를 통해 패킷 송수신 체크 가능
- 예시: `192.168.26.130(Attacker) > 웹서버 접속`

### 2.5 주요 프로토콜 분석
- **DNS 조회**
- **TCP 3-way handshake**
  - Packet No. 3-5
  - 포트 80 / 443
- **Handshake > TLS**
  - 자세한 내용은 암호학 강의 참고 예정
- **PING / ICMP**
  - Echo Request: 요청 패킷
  - Echo Reply: 응답 패킷
  - PING 5회 → 총 10개 패킷 생성
  - ICMP Type 8: Echo Request
  - Checksum: 오류 검사용
  - Sequence number: 패킷 순서 확인
- **NTP(Network Time Protocol)**
  - 컴퓨터 시계 동기화
  - 분석 제외 가능
- **HTTP 분석**
  - 현재 시간 출력 HTML/JS 작성 필요 (Cache 확인)
  - 순서: 3-way handshake → HTTP REQUEST → HTTP RESPONSE
  - 예시: `Src:192.168.26.130(41646) > Dst:192.168.26.129(80)`

---

## 3. 웹 패킷 분석
- 브라우저 개발자도구(F12)
- Fiddler 활용
  - HTTPS 인증서 제공 (Decrypt 가능)
  - [Fiddler 공식사이트](https://www.telerik.com/fiddler)

---

## 4. 트래픽 모니터링 개요
- 네트워크를 통해 오가는 데이터(패킷, 요청, 응답 등)를 실시간 수집·분석·감시
- 활용 툴
  - Wireshark
  - 브라우저 개발자 도구
  - Fiddler

### 4.1 클라우드 환경
- CSP 제공 모니터링 서비스 활용 가능 (유료)
- 악성코드 사후분석 시 필요

### 4.2 Windows 전용 툴
- **Microsoft Network Monitor 3.4**
  - 프로세스 별 패킷 정리
  - Wireshark와 유사한 필터 기능
- **NetworkUsageView**
  - SRUDB.dat 기반 네트워크 사용량 확인
  - 적은 리소스, 다중 사용자 대역폭 추적 용이
- **NetBalancer**
  - 네트워크 어댑터 설정
  - 프로세스 우선순위 / 속도 제한
  - 트래픽 시각화 및 통계 제공

---

## 5. 참고자료
- [Wireshark • Go Deep | Download](https://www.wireshark.org/download.html)