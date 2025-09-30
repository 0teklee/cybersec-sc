

# Threat Intelligence (위협 인텔리전스) 활용 기법

---

## 📌 Threat Intelligence란?

- 사이버 보안 관점에서 조직이 직면할 수 있는 **잠재적·실제적 보안 위협**에 대한 정보와 대응 전략
- 단순 탐지가 아닌 **공격자의 의도, 전술, 기법, 절차(TTPs)** 분석을 통해 사전 예측 및 방어 능력 강화

---

## 📌 Threat Intelligence의 주요 요소

- **위협 행위자(Threat Actor)** 정보  
  - 해커, 범죄 조직, 국가 지원 공격자 등
- **공격 기법 정보**  
  - 취약점, 악성코드, 인프라(IP, 도메인 등)
- **패턴 및 트렌드 분석**  
  - 실제 공격에서 반복적으로 활용되는 전술
- **실행 가능한 인텔리전스 (Actionable Intelligence)**  
  - 조직 보안 전략 및 사고 대응(Incident Response)에 활용

---

## 📌 Threat Intelligence 활용

- **보안 시스템 연계**
  - EDR, XDR과 연동
- **위협 데이터 수집 출처**
  - 다크웹, 딥웹
  - 오픈 소스(OSINT)
  - Shodan (인터넷 연결 장비 탐색)
  - OSINT Framework: [https://osintframework.com/](https://osintframework.com/)

---

## 📌 Shodan 예시

- **CCTV 검색**
  - [Shodan CCTV Search](https://www.shodan.io/search?query=cctv)
- **국가별 제한**
  - `cctv country:kr`
- **활용 사례**
  - CCTV 관리자 페이지 노출 및 무단 열람 가능성

---

## 📚 Reference

- [클라우드 보안: 클라우드별 보안 서비스 비교](https://spacek82.tistory.com/18)