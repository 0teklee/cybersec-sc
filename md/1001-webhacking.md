# old-26

문제 링크: https://webhacking.kr/challenge/web-11/

- `PHP`에 대해 얕게나마 공부할 수 있어 좋은 문제였습니다.
    - `PHP`는 기본적으로 **서버사이드 렌더링**에 해당합니다.
    - `MPA`에 익숙하신 분들은 기본 개념을 쉽게 받아들일 수 있겠습니다.
    - `Next.js`의 서버사이드 파트의 로직을 `<?php></?>` 작성한다-정도만 이해한 상태로 문제를 풀었습니다.

---

## 코드 및 접근

### 키워드: 2중 인코딩

```php
<?php
// 1. preg_match에서 decode 되었을 때 "admin"이 나와선 안됩니다.
  if(preg_match("/admin/",$_GET['id'])) { 
        echo "no!";
        exit(); 
    }
// preg_match 조건문을 통과한 뒤, 2번 조건문을 통과해야 합니다.
  $_GET['id'] = urldecode($_GET['id']);
  //  $_GET['id']의 재할당이 이루어집니다.
  // urldecode(_GET['id'])가 "admin"이 되어야 합니다. 

// 2. 조건문:
  if($_GET['id'] == "admin"){
    solve(26);
  }
?>
```

**URL 인코딩은 `HEX` 16진수로 변환하는 것**이 전부라고 합니다. 강사님과 함께 인코딩 표를 보며 문자열을 변환했습니다.

2번 조건문의 `$_GET['id']`는 재할당이 이루어져있기 때문에, `urldecode($_GET['id'])`가 "admin"이 되어야 합니다.

정리하자면,
    1. 1번 조건문의 `preg_match`로 디코딩될 때   
    - 디코딩 시 `"admin"`이 나오지 않으면서
    2. 2번 조건문 통과를 위해 1번을 통과한 값은 디코딩 시 `"admin"`이 나와야 합니다.


---

## PHP vs Web API 인코딩 차이

