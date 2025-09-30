

# VMware & Kali Linux Slow HTTP DoS

---

## 1. VMware 개요
- 가상 머신(VM, Virtual Machine)은 물리적 컴퓨터 하드웨어를 에뮬레이션한 소프트웨어
- 하나의 물리적 컴퓨터에서 여러 운영체제를 동시에 실행 가능
- 각 VM은 독립적인 CPU, 메모리, 네트워크, 스토리지, 운영체제 보유
- 예시: Windows 환경 내에 Linux VM 실행

---

## 2. VMware / Broadcom

### 2.1 설치 & 등록
- VMware Workstation Pro 17 설치
- Broadcom 계정 등록 필요  
  👉 [Broadcom Registration](https://profile.broadcom.com/web/registration)

### 2.2 Kali Linux
- [Kali Linux 공식 사이트](https://www.kali.org/)에서 다운로드 가능
- Penetration Testing / Ethical Hacking 용도

### 2.3 VM 구성
- Attacker VM
- Victim VM

---

## 3. Kali Linux 환경

### 3.1 기본 계정
- Username: `kali`
- Password: `kali`

### 3.2 네트워크 & 방화벽
- `ifconfig` → IP 확인 (예: `192.168.26.130`)
- 방화벽 중지:
  - 일시 중지: `stop nftables`
  - 영구 중지: `disable nftables`

### 3.3 웹 서버
- Apache2 기본 설치
- Victim VM에서 웹 페이지 접속 가능 여부 확인 필요

---

## 4. 공격자/피해자 시뮬레이션
- **VM1 (Attacker)**: 공격 실행
- **VM2 (Victim)**: 웹 서버 동작 확인

---

## 5. 스크립트 키디
- 기존 도구(toolkit) 또는 Python 스크립트를 그대로 사용하는 경우
- [나무위키: 스크립트 키디](https://namu.wiki/w/%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%20%ED%82%A4%EB%94%94)

---

## 6. Slow HTTP DoS 공격

### 6.1 개념
- HTTP 요청을 조금씩 천천히 전송하여 서버가 대기하도록 유도
- CRLF(`\r\n`) 미전송 → 서버가 Body 대기 상태 유지
- 결과적으로 TCP 세션이 계속 누적되어 연결 불가 상태 발생

### 6.2 GitHub 스크립트
- [Original Slowloris HTTP DoS](https://github.com/Ogglas/Orignal-Slowloris-HTTP-DoS)
- `slowloris.pl` (IPv4)
- `slowloris6.pl` (IPv6)

### 6.3 실행 준비
```bash
git clone https://github.com/Ogglas/Orignal-Slowloris-HTTP-DoS.git
chmod a+x slowloris.pl
```

- `/etc/hosts`에 Victim IP → Domain 매핑
```plaintext
192.168.28.130 www.a.com
```

---

## 7. Apache 방어 설정

### 7.1 모듈 수정
```bash
sudo nano /etc/apache2/mods-enabled/reqtimeout.conf
```

### 7.2 방어 모듈 설치
```bash
sudo apt update
sudo apt install libapache2-mod-evasive -y
```

### 7.3 설정 수정
```bash
sudo vi /etc/apache2/sites-available/000-default.conf
sudo vi /etc/apache2/apache2.conf
```

### 7.4 Slowloris 프로세스 종료
```bash
ps aux | grep slowloris | grep -v grep | awk '{print $2}' | xargs sudo kill -9
```

---

## 8. 프로세스 관리
- `Ctrl + C`: 종료 (프로세스 완전 종료)
- `Ctrl + Z`: 종료 (백그라운드 프로세스 잔존)

---

## 9. Reference
- [ZDNet Korea: 보안 상장사 9곳 공동 설명회](https://zdnet.co.kr/view/?no=20250619154054)
- [bWAPP: Slow HTTP DoS](https://spadework-blog.tistory.com/50)
- [정보보안 블로그 - HTTP Header DoS](https://honeybeehoney.github.io/dos/http_header_dos/)