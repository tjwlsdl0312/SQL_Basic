# 📘 SQL_BASIC 2주차 정규 과제

SQL_BASIC 정규 과제는 매주 정해진 분량의 `초보자를 위한 BigQuery(SQL) 입문` 강의를 듣고, 핵심 개념을 정리한 뒤 간단한 SQL 문제를 직접 풀어보는 방식으로 진행합니다.

이번 주는 저장된 데이터를 확인하는 방법과 `SELECT`, `FROM`, `WHERE`의 기본 구조를 학습합니다.

완성된 과제는 Github에 업로드하고, 링크를 스프레드시트 'SQL' 시트에 입력해 제출해주세요.

**👀 수행 인증란은 필수입니다.**

---

## 📚 SQL_BASIC_2nd_TIL

### 섹션 3. 데이터 탐색 - 조건, 추출, 요약

### 2-2. 저장된 데이터 확인하기(데이터베이스, 데이터 웨어하우스, ERD)

### 2-3. 데이터 탐색(SELECT, FROM, WHERE)

---

## ✨ 선택 강의

- 2-4. SELECT 연습 문제: SELECT, FROM, WHERE를 더 연습하고 싶을 때 선택 수강

---

## 🏁 전체 강의 수강 계획

| 주차 | 필수 강의 범위 | 선택 강의 | 완료 여부 |
| --- | --- | --- | --- |
| 1주차 | 1-1 ~ 2-1 | 1 | ✅ |
| 2주차 | 2-2 ~ 2-3 | 2-4 | ✅ |
| 3주차 | 2-5, 2-7 ~ 2-8 | 2-6 | 🍽️ |
| 4주차 | 3-2 ~ 4-3 | 3-4 | 🍽️ |
| 5주차 | 4-4 ~ 4-6 | 4-5, 4-7 | 🍽️ |
| 6주차 | 5-2 ~ 5-5 | 5-6 | 🍽️ |
| 7주차 | 필수 강의 없음 | 6-2, 6-3, 6-4, 6-5 | 🍽️ |

---

<br>

<!-- 여기까진 그대로 둬 주세요-->

---

# 1️⃣ 개념 정리

아래 키워드 중 중요하다고 생각한 개념을 2개 이상 골라 짧게 정리해주세요. 3개보다 더 많이 정리하고 싶다면 자유롭게 항목을 추가해도 좋습니다.

이번 주 키워드:
- SELECT
- FROM
- WHERE
- 조건식
- ORDER BY
- LIMIT
- 테이블 구조 확인

## 01.

```
개념 이름: FROM  
개념 설명: 데이터를 어떤 테이블에서 확인할지 결정하는 키워드.  
형태는 FROM `<프로젝트 id>.<데이터셋>.<테이블>` 와 같음.  
프로젝트 id의 경우 단일 프로젝트 작업일 때 생략 가능하고 (여러 개일 경우 작성 추천), 생략한 경우 `(백틱)을 적지 않아도 괜찮음.
예시 쿼리:  
FROM `inflearn-bigquery-507811.basic.pokemon`  
FROM `basic.pokemon`  
FROM basic.pokemon  
```

## 02.

```
개념 이름: WHERE  
개념 설명: 테이블의 컬럼 중 원하는 조건을 설정하는 키워드. 데이터를 필터링할 수 있음.
예시 쿼리:  
WHERE   
    type1 = "Fire""
```

## 03.

```
개념 이름: SELECT  
개념 설명: 테이블에서 어떤 컬럼을 출력할 것인지 선택하는 키워드. 
* = 모든 컬럼 출력 / * EXCEPT(column_name) = 괄호 안 컬럼 제외 출력
여러 개의 컬럼 출력 가능 (, 사용) / AS를 통해 컬럼에 별칭 지정 가능
예시 쿼리:  
SELECT  
    id AS pokemon_id,
    kor_name, 
    type1, 
    type2

 SELECT 
    * EXCEPT(eng_name)
```

---

# 2️⃣ 수행 인증란

아래 중 하나 이상을 첨부해주세요.

- 강의 수강 화면 캡처
- 문제 풀이 정답 화면 캡처
- SQL 실행 결과 화면 캡처

![week2](week2image.png)

---

# 3️⃣ 확인 문제

프로그래머스는 로그인이 필요하므로, 로그인 후 문제 풀이를 진행해주세요.

## 🧩 문제 1

문제 링크: [모든 레코드 조회하기](https://school.programmers.co.kr/learn/courses/30/lessons/59034)

풀이 과정:
SELECT 
    *
FROM ANIMAL_INS
ORDERY BY ANIMAL_ID

```
- 테이블에서 확인한 컬럼: ANIMAL_ID, ANIMAL_TYPE, DATETIME, INTAKE_CONDITION, NAME, SEX_UPON_INTAKE
- SELECT와 FROM을 작성한 방식: 모든 컬럼을 출력할 수 있도록 SELECT의 조건으로 *을 작성하였다. FROM에는 나타난 정보가 테이블명 뿐이었기에 테이블명만을 작성해주었다.
- 새로 배운 점: 기본 데이터셋이 설정되어있을 경우 프로젝트ID 외에 데이터셋까지 생략 가능하다 / ORDER BY 문법을 통해 표시컬럼 순서를 조정할 수 있다.
```

![레코드](week2image-1.png)

## 🧩 문제 2

문제 링크: [아픈 동물 찾기](https://school.programmers.co.kr/learn/courses/30/lessons/59036)

풀이 과정:
SELECT
    ANIMAL_ID,
    NAME
FROM ANIMAL_INS
WHERE 
    INTAKE_CONDITION = "Sick"
ORDERY BY ANIMAL_ID

```
- 문제에서 요구한 조건: 데이터셋에서 아픈 동물의 아이디와 이름을 아이디 순으로 조회해야 한다.
- WHERE 절로 옮긴 방식: INTAKE_CONDITION 컬럼의 값이 Sick인 행을 고르기 위해 WHERE INTAKE_CONDITION = "Sick"와 같이 작성하였다.
- 정렬 기준이 있다면 사용한 기준: ANIMAL_ID 순으로 조회해야 했기 때문에 ORDER BY 키워드를 사용하였다.
- 새로 배운 점: SELECT, FROM, WHERE, ORDERY BY 등의 SQL 키워드는 대소문자를 구문하지 않으나, 가독성을 위해 대문자로 작성해주는 것이 좋다.
```

![아픈 동물](week2image-2.png)

---

# 4️⃣ 이번 주 회고

```
1. SELECT, FROM, WHERE 중 가장 헷갈린 개념: FROM-WHERE-SELECT 순으로 실행되는데, 쿼리문을 작성할 때 출력을 위한 SELECT를 가장 먼저 작성해야 된 점이 헷갈렸던 것 같다.
2. 문제를 풀 때 가장 자주 확인하게 된 부분: 마침표와 쉼표, 백틱과 따옴표를 헷갈리지 않으려 자주 확인했던 것 같다. 
3. 다음 주 문제 풀이에서 의식하고 싶은 습관: 기호들을 잘 확인하는 습관, 키워드나 컬럼명 오타를 확인하는 습관
```

수고하셨습니다!




