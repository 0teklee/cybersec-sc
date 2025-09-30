# 시스템 해킹 / Pwnable

## 1. 주요 관련 기술

-**리버싱** (**리버스 엔지니어링**)
-C 언어
	- 메모리 / 포인터와 밀접한 프로그래밍 언어
	- 고급언어이지만 중급언어라고도 함 (시스템 제어 가능 영역 多)
	- (대조: Java → 메모리를 자동 관리)
- Python
	- **자동화** 및 **exploit tool** 지원이 잘 되어 있음
	- 공격 코드를 쉽게 제작 가능

### 학습 사이트

    - [pwnable.kr](https://pwnable.kr)
	- 리눅스 기본기부터 시스템 해킹 관련 문제를 풀 수 있는 **워게임 사이트**

---

## 2. 대표 취약점 및 기법

줄임말abbr로 많이 불리는 것 같습니다.  
수업시간엔 주로 `BOF`를 다루었습니다.

- **Buffer Overflow** (BOF)
- Return Oriented Programming (ROP)
- Return To Library (RTL)
- Format String Bug (FSB)
- Out Of Bound (OOB)

---

### a. BOF (Buffer Overflow)

예제:

```c
//gcc -fno-stack-protector bof.c -o bof
#include<stdio.h›
	int main(void){
	char buf[64];
	scanf ("%s", buf);
	printf("%", buf);
}

여기서 팁! 
64bit 환경에서는 주소값이 8byte로 표현되고 스택도 8바이트 단위로 할당됩니다.
buf 의 크기를 8의 배수에 맞지 않게 지정한다면, 스택은 8바이트 단위로 할당되기 때문에 남는 공간이 생겨 
return address 까지 위치가 달라질 수 있습니다.
```

입력받을 `buf`의 크기는 64이지만, `scanf()` 함수로 "`%64s`" 같은 서식문자를 사용하지 않고, 그냥 `"%"` 를 사용해 입력을 받으니, `buf`의 크기보다 입력을 크게 받을 수 있어, `BOF`가 발생합니다.
즉 **"데이터를 넘겨서 실행흐름을 바꾼다."**는 것이 핵심이라고 짚어주셨습니다.  
이외로 `int8` 타입을 인자로 받는 함수에 `64`를 넣어 오작동을 유발하는 등의 예시가 있었습니다.


```shell
 ex) A함수 호출 → 함수 반환값으로 예상된 값이 아닌 함수를 호출하도록 조작
```

- `Return address`가 변경되면 **실행 흐름이 바뀐다**
	- 앞선 예제를 통해 함수가 의도치 않게 동작하게 되어 실행흐름이 바뀌게 된 것을 알게 되었습니다.

#### BOF 보호 기법

1. ASLR (Address Space Layout Randomization)
   - 주소 랜덤화로 원하는 값/주소 참조가 어려워짐
	- 공격에 취약할 수 있는 반환값의 메모리 주소를 랜덤화하는 것으로 이해했습니다.
   - 실행할 때마다 메모리에 mapping되는 주소가 랜덤
   - Stack, Heap, Shared library 위치가 변경됨
2. Canary
   - 스택 버퍼와 반환 주소 사이에 임의의 값을 삽입
   - Canary 값이 변조되면 탐지 → BOF 차단
	- CI/CD에서 `Canary` 버전닝과 체크섬이 떠오르는 부분입니다.
3. DEP / NX
   - 리눅스 계열: NX
   - 윈도우 계열: DEP
   - 메모리 공간의 실행 권한 제거 (스택, 힙 등)

---


## 3. 취약점 분석
	- 취약점 발생 지점: Stack trace 에러, Crash
		- 과거: 수동 분석(노가다)
		- 현재: 퍼징(Fuzzing) 도구로 자동화
	- 무작위 데이터를 입력 → 예기치 않은 동작/충돌/메모리 누수/입력 검증 실패 탐지
		- 현직에서 QA가 떠오르는 부분이었습니다.  


### AEG (Automatic Exploit Generation)
	- 취약점 자동화 연구 (AI 기반과 연계)
	- CMU 차상길 교수 (현재 KAIST 정보보호대학원)
	- CMU 소속 해킹팀 PPP → DEFCON 다수 우승
	- 대표 논문: Avgerinos et al., NDSS 2011 (avgerinos-ndss11.pdf)


### 보안 Top 컨퍼런스
	- NDSS
	- IEEE S&P
	- USENIX Security

### 암호학 Top 컨퍼런스
	- CRYPTO
	- EUROCRYPT

### 읽을 거리

[Pwnable 기초 포너블 공격기법 총정리](https://snwo.tistory.com/147)

---

읽어주셔서 감사합니다!