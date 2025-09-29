시스템 해킹 / Pwnable

주요 관련 기술
	•	리버싱 (리버스 엔지니어링)
	•	C 언어
	•	메모리 / 포인터와 밀접한 프로그래밍 언어
	•	고급언어이지만 중급언어라고도 함 (시스템 제어 가능 영역 多)
	•	(대조: Java → 메모리를 자동 관리)
	•	어셈블리어
	•	Python
	•	자동화 및 exploit tool 지원이 잘 되어 있음
	•	공격 코드를 쉽게 제작 가능

---

학습 사이트

    •	pwnable.kr
	•	리눅스 기본기부터 시스템 해킹 관련 문제를 풀 수 있는 워게임 사이트

---

대표 취약점 및 기법
	•	Buffer Overflow (BOF)
	•	Return Oriented Programming (ROP)
	•	Return To Library (RTL)
	•	Format String Bug (FSB)
	•	Out Of Bound (OOB)

BOF (Buffer Overflow)
	•	Return address가 변경되면 실행 흐름이 바뀜

⸻

BOF 보호 기법

1. ASLR (Address Space Layout Randomization)
   •	실행할 때마다 메모리에 mapping되는 주소가 랜덤
   •	Stack, Heap, Shared library 위치가 변경됨
   •	주소 랜덤화로 원하는 값/주소 참조가 어려워짐
2. Canary
   •	스택 버퍼와 반환 주소 사이에 임의의 값을 삽입
   •	Canary 값이 변조되면 탐지 → BOF 차단
3. DEP / NX
   •	리눅스 계열: NX
   •	윈도우 계열: DEP
   •	메모리 공간의 실행 권한 제거 (스택, 힙 등)

⸻

취약점 분석
	•	취약점 발생 지점: Stack trace 에러, Crash
	•	과거: 수동 분석(노가다)
	•	현재: 퍼징(Fuzzing) 도구로 자동화
	•	무작위 데이터를 입력 → 예기치 않은 동작/충돌/메모리 누수/입력 검증 실패 탐지

⸻

AEG (Automatic Exploit Generation)
	•	취약점 자동화 연구 (AI 기반과 연계)
	•	CMU 차상길 교수 (현재 KAIST 정보보호대학원)
	•	CMU 소속 해킹팀 PPP → DEFCON 다수 우승
	•	대표 논문: Avgerinos et al., NDSS 2011 (avgerinos-ndss11.pdf)

⸻

보안 Top 컨퍼런스
	•	NDSS
	•	IEEE S&P
	•	USENIX Security

암호학 Top 컨퍼런스
	•	CRYPTO
	•	EUROCRYPT

⸻

Reference
	•	[Pwnable] 기초 포너블 공격기법 총정리
