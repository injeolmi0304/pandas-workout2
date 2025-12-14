# Field of Study 데이터셋 설명

## 개요

이 문서는 `FieldOfStudyData1718_1819_PP.csv.gz` 파일의 Field of Study (전공 분야) 데이터셋에 대한 설명입니다.

**출처:** 미국 교육부(U.S. Department of Education) - College Scorecard  
**웹사이트:** https://collegescorecard.ed.gov  
**데이터 형식:** gzip 압축된 CSV 파일  
**데이터 기간:** 2017-18, 2018-19 학년도 (PP: Programs and Prices)

---

## 데이터셋 정보

이 데이터셋은 미국 대학들이 제공하는 개별 전공 프로그램(학위 과정)에 대한 정보를 포함합니다. 각 행은 특정 대학의 특정 전공 프로그램을 나타냅니다.

**특징:**
- 한 대학이 여러 전공을 제공하므로, 같은 대학(OPEID6)이 여러 번 나타날 수 있음
- 학사, 석사, 박사 등 학위 수준별로 같은 전공도 별도의 행으로 존재
- `Most-Recent-Cohorts-Institution.csv.gz`와 `OPEID6`를 기준으로 조인 가능

---

## 컬럼 상세 설명

### 1. OPEID6
- **설명:** 대학 고유 식별 번호 (6자리)
- **데이터 타입:** 문자열 또는 정수
- **특징:** 동일한 `OPEID6`가 여러 행에 나타날 수 있음 (한 대학이 여러 전공 제공)

---

### 2. INSTNM
- **설명:** 대학명 (Institution Name)
- **데이터 타입:** 문자열
- **예시:** 
  - "Harvard University"
  - "Stanford University"
  - "University of California-Berkeley"
- **참고:** 같은 대학이라도 캠퍼스별로 이름이 다를 수 있음

---

### 3. CREDDESC
- **설명:** 학위 종류 설명 (Credential Description)
- **의미:** 해당 프로그램이 수여하는 학위의 수준
- **데이터 타입:** 문자열
- **가능한 값:**
  - `"Bachelors Degree"` (학사 학위, 4년제)
  - `"Master's Degree"` (석사 학위)
  - `"Doctoral Degree"` (박사 학위)
  - `"Associate's Degree"` (준학사 학위, 2년제)
  - `"Graduate/Professional Certificate"` (대학원 수료증)
  - `"Undergraduate Certificate"` (학부 수료증)
  - `"Postbaccalaureate Certificate"` (학사 후 수료증)

---

### 4. CIPDESC
- **설명:** 전공 분야 설명 (CIP Description)
- **CIP란?** Classification of Instructional Programs - 미국 교육부가 정의한 표준 전공 분류 체계
- **데이터 타입:** 문자열
- **예시:**
  - `"Computer Science"`
  - `"Business Administration and Management"`
  - `"Mechanical Engineering"`
  - `"Psychology, General"`
  - `"Registered Nursing/Registered Nurse"`
  - `"Biology/Biological Sciences, General"`
- **특징:** 매우 세부적인 전공까지 구분 (예: "Computer Science" vs "Computer Engineering")

---

### 5. CONTROL
- **설명:** 대학 운영 주체 (대학 유형)
- **데이터 타입:** 문자열
- **가능한 값:**
  - `"Public"` (공립 대학) - 주 정부나 지방 정부가 운영
  - `"Private nonprofit"` (사립 비영리 대학) - 예: Harvard, Stanford, MIT
  - `"Private for-profit"` (사립 영리 대학) - 예: University of Phoenix

---

## 데이터 구조 예시

| OPEID6 | INSTNM | CREDDESC | CIPDESC | CONTROL |
|--------|---------|----------|---------|---------|
| 100654 | Harvard University | Bachelors Degree | Computer Science | Private nonprofit |
| 100654 | Harvard University | Master's Degree | Computer Science | Private nonprofit |
| 100654 | Harvard University | Bachelors Degree | Economics | Private nonprofit |
| 110635 | Stanford University | Bachelors Degree | Computer Science | Private nonprofit |
| 110635 | Stanford University | Doctoral Degree | Computer Science | Private nonprofit |

**특징:**
- 같은 대학(OPEID6)이 여러 번 나타남
- 같은 전공도 학위 수준(CREDDESC)에 따라 별도의 행으로 존재
- 한 대학이 수십~수백 개의 프로그램을 제공할 수 있음

---

## 데이터 품질 고려사항

### 결측값
- 일부 프로그램은 특정 컬럼이 비어 있을 수 있음
- 특히 `CONTROL` 정보가 누락된 경우가 있을 수 있음

### 데이터 중복
- 같은 대학, 같은 전공이 여러 행에 나타날 수 있음

### 문자열 일관성
- `CIPDESC`의 경우 대소문자나 공백 차이가 있을 수 있음

---

## 참고 링크

- **College Scorecard 공식 웹사이트:** https://collegescorecard.ed.gov
- **Field of Study 데이터 다운로드:** https://collegescorecard.ed.gov/data/