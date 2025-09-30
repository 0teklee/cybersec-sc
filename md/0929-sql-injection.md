# SQL Injection

---

## 개요

`SQL Injection`(약칭 SQLi)은 애플리케이션의 **입력값을 통해 악의적인 SQL 문을 삽입**하여 d**b 쿼리를 조작**하는 공격 기법입니다. 공격자는 이를 통해 데이터 열람, 수정, 삭제, **데이터베이스 관리자 권한 획득**이나 **파일시스템 접근**까지 시도할 수 있습니다.

### SQL 삽입

https://demo.testfire.net/login.jsp

`sql injection`을 시험해볼 수 있는 사이트입니다.

---

## 기본 예제

- SELECT 예제:

```sql
SELECT * FROM user_tb WHERE ID=‘$id’ and PW=‘$pw’;
```

- 공격자 입력 예시:

```sql
$id = "’ or 1=1 –‘
$pw = 1
```

- 조합된 결과 (주석 사용):

```sql
SELECT * FROM user_tb WHERE ID=‘’ or 1=1 --’ and PW=‘1’;
--: SQL 주석
SELECT * FROM user_tb WHERE ID=‘’ or 1=1
```

## 논리값과 결과

- 예시:
  `SQL`의 `OR`를 활용해 `false` 입력값 + `%09or%09true`를 만드는 기본적인 쿼리 인젝션입니다. 실습에서 풀어본 `old-18` 문제에서 사용되었습니다.

```sql
SELECT * FROM user_tb WHERE FALSE or TRUE
SELECT * FROM user_tb WHERE TRUE
> TRUE (참)
```

---

## 주요 기법(타입)

- UNION SQL Injection
- Error Based SQL Injection
- Blind SQL Injection
- TIME Based SQL Injection

> 특별한 기법이라기보다는 SQL 문을 응용해 장난치는 느낌이라고 합니다. DBMS별로 문법 차이가 있어(Oracle, MySQL, MSSQL 등) 여러 DBMS 경험이 있으면 유리합니다. 특히 MySQL에서는 `information_schema`가 **매우** 중요합니다.

---

## UNION 기반 예시

```sql
SELECT username FROM coco_marketing_user WHERE id='' UNION SELECT VERSION() # '
```

- 주의: UNION을 사용할 때는 좌/우 SELECT의 컬럼 개수가 일치해야 합니다.

---

## 자동화와 연습

- 하나의 취약점을 발견하면 `Python` 등으로 자동화 스크립트를 만들어 반복 공격에 사용합니다.
- 다양한 `SQL` 키워드를 숙지해야 합니다.

---

## `WAF` 우회 기법 (간단 정리)

1. URL Encoding
   - URL Decoder/Encoder 사용
2. 주석 활용
3. 대소문자 활용
4. 공백 우회 방법 (예: 탭, 개행, URL 인코딩)

- `%0a` (개행)
- `%0d` (캐리지 리턴)
- `%09` (탭)
- `/**/` (주석)
- 개인적으로 실습에서 정규식과 함께 중요하다고 느낀 부분입니다.
- 웹앱은 보통 이러한 `input` 요청에 기본적인 안전장치가 있는 것으로 알고 있습니다.

---

## 워게임 / 실습 리소스

- Webhacking.kr (운영자: rubiya로 알려짐)
  - 예시 계정: Id / a235  Pw / 1
- Wargame.kr
  - already got, QR Code PUZZLE, flee button, login filtering

아래는 Webhacking.kr에서 강사님이 10여년 전에 작성하신 메모입니다.  

문제에서 배울 점들을 정리해주셔서 도움이 됩니다.

> **Webhacking.kr**
>
>
> oldzombie(백호연)님의 워게임 사이트. 초창기에 만들어져있으며 웹해킹의 입문 사이트로 많이 알려져 있다.
> 01 : PHP 코드의 이해와 쿠키에 대한 개념을 배울 수 있음
> 02 : 강력추천 문제. `Blind SQL`를 배울 수 있고 특히 웹해킹할때 감을 좀 기를 수 있는 문제
> 10 : `Javascript` 변조에 대한 문제
> 11 : 정규식을 배울 수 있는 문제..(보통 보안코드로 **정규식을 많이 쓰는 경우가 많아서** 알아두면 좋다)
> 12 : `Javascript` 공부하는데 도움 되는 문제
> **18** : `SQL(SQL Injection)`에 대해서 배울 수 있는 문제 (**실습**)
> 21 : `BSQL`(Blind SQL Injection)에 대해서 공부할 수 있는 문제
> 31 : `Socket`에 대한 개념을 배울 수 있는 문제
> 32 : 웹해킹을 할때 코딩을 왜 해야되는지에 대해 알 수 있고 쿠키를 배울 수 있는 문제
> 53 : `SQL Injection`할 때 필터링 우회를 배울 수 있는 문제

❓**BSQL**

SK쉴더스의 보고서에서 잘 설명이 되어있습니다.

> SQL Injection은 사용자 입력값을 검증하지 않는 경우 설계된 쿼리문에 의도하지 않은 쿼리를 임의로 삽입할 수 있는 공격이다. 공격자는 쿼리를 악의적으로 주입하여 데이터베이스의 데이터를 무단으로 탈취할 수 있다 
>
> (중략...)
> **Blind SQL Injection은 참(True)인 쿼리문과 거짓(False)인 쿼리문 입력 시 반환되는 서버의 응답이 다른 것을 이용**하여 이를 비교하여 데이터를 추출하는 공격이다. Blind SQL Injection은 다른 유형의 SQL Injection과 달리 추출하려는 실제 데이터가 눈에 보이지 않는다. 따라서 참
> 또는 거짓의 입력값에 따른 서버의 응답을 통해 값을 유추해야 한다. 아래의 그림은 게시판의 검색 기능에서 Blind SQL Injection 취약점 여부를 확인한 결과이다. 참인 쿼리문을 입력할 경우 검색 결과가 출력되고, 거짓인 쿼리문을 입력할 경우 검색 결과가 표시되지 않는다.
>
> https://www.skshieldus.com/download/files/download.do?o_fname=EQST%20insight_Special%20Report_202208.pdf&r_fname=20220818113242961.pdf

---

## Webhacking.kr - Challenge 18 

- 취약점 요약: `select id from chall18 where id='guest' and no=$_GET[no]`
- 힌트: No=1 → guest, No=2 → admin
- 우회 예시: `selectidfromchall18whereid='guest'andno=2%09or%09no=2`
  - 여기서 `%09`는 HT(Tab) 문자로 공백 대체 용도
- `php`를 제대로 들여다 본 것이 처음이라 낯설었지만 매우 흥미로웠습니다.


❓  `Form` 태그 입력 요청 시 `payload` 변환
- 텍스트 입력 `input` 태그에 `%09`를 입력한 뒤 `submit` 했을 시, 응답 페이지 쿼리가 입력한 쿼리와 다르게 나왔습니다.
- 제 브라우저의 문제인지 확실치 않았습니다. 강사님께 여쭈어보니, 이런 경우에 당연히 url 쿼리에 입력하는 것을 고려해보라고 하셨습니다.
- 개발자의 관점에서 *주어진 문제를 규칙 안에서* 푸는 것에 익숙하다 보니, 이런 부분이 인상깊게 느껴졌습니다.

---

읽어주셔서 감사합니다!