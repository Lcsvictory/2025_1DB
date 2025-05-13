# 2025_1DB
MS Access 

# 중간시험정리
## 2장 데이버베이스 개요

### 2-1 파일처리 시스템의 문제점
- 파일처리 시스템은 파일에 의존성 문제가 있음.  
    1. 구조적 종속
``데이터 파일의 구조가 변함에 따라 프로그램도 바뀌어야함.``
    2. 데이터 종속
``데이터 파일의 데이터가 변함에 따라 프로그램도 바뀌어야함.``

- 데이터 비일관성
    - 1.데이터 중복
    - 2.데이터 무결성 결여

### 2-2 데이터베이스 개념
- database란?
    1. ``완벽화(exhaustion)``
    2. ``비중복화(non-redundancy)``
    3. ``구조화(structure)``
- 장점
    1. 중복 최소 -> 비 일관성 회피
    2. 데이터의 물리적, 논리적 독립성 유지
    3. 데이터 공유
    4. 데이터 표준화(standardization)
    5. 보안성(sercurity)
    6. 무결성(integrity)
    7. 상충(conflict) 요구 조절(DBMS의 기능)
- 단점
    1. overhead(컴퓨터의 부담)
    2. 복구 어렵다
    3. 전산 비용 증가, 복잡

### 2-3 데이터베이스 시스템
- 구성요소
    1. ``database``
        - 중앙집중식 데이터베이스
        - 분산식 데이터베이스
    2. ``hardware``
        - 전용컴퓨터
        - 범용컴퓨터
    3. ``software``
        - DBMS
    4. ``user``
        - DBA
        - application programmer
        - end user

### 2-4 데이터베이스 3층 구조
- 외부단계
    - ``사용자가 보는 데이터 베이스의 논리적 구조``
    1. 외부 스키마(external schema)
    2. 서브 스키마(sub schema)
    3. 뷰(view)

- 개념단계
    - ``관리자가 보는 데이터 베이스의 논리적 구조``
    1. 개념 스키마(conceptural schema)
    2. 스키마(schema)

- 내부단계
    - ``물리적 구조``
    1. 내부 스키마(internal schema)
    2. 저장 스키마(storage schema)
    
### 2-5 데이터베이스 관리시스템(DBMS)
- 데이터 정의어 ``DDL``
    - DBA가 사용
    - ``create``, ``alter``, ``drop``, ``truncate``, ``rename``
- 데이터 조작어 `` DML``
    - apllication programmer, end user가 사용
    - ``select``, ``update``, ``insert``, ``delete``
- 데이터 제어어 ``DCL``
    - DBA가 사용 (트랜잭션 관리)
    - ``commit``, ``rollback``

### 2-6 데이터베이스 관리자
- 수행 기능
    - 데이터베이스 정의
    - 구조 설계
    - 시스템 평가 및 사용자 요구 대응
- DBMS 제공 유틸리티
    - load routine(적재 루틴)
    - dump/restore routine(덤프/재저장 루틴)
    - reorganization routine(재구성 루틴)
    - statistics routine(통계 루틴)
    - analysis routine(분석 루틴)
    - data dictionary(데이터 사전)
    
### 2-7 데이터 독립성(data independence)
- 논리적, 물리적 데이터 독립성
    - 논리적 데이터 독립성
        - 데이터베이스의 논리구조가 변경되어도 프로그램에 영향을 주지 않음
    - 물리적 데이터 독립성
        - 데이터베이스의 물리구조가 변경되어도 프로그램에 영향을 주지 않음

### 2-8 데이터 사전(data dictionary)
- 시스템 카탈로그라고도 함
    - 데이터베이스에 저장된 모든 데이터의 정의나 명세에 관한 정보를 수록하는 시스템 데이터베이스
    - 기능
        - 데이터 사전의 갱신과 검색을 위한 데이터 정의어 제공
        - 데이터베이스 시스템의 운영과 관리에 필요한 각종 통계 정보 수록
        - 응용 프로그램과 데이터베이스 간의 인터페이스 역할 수행
        - 데이터의 성격과 구조에 대한 정보 저장


## 3장 관계형 데이터베이스(RDBMS)

### 3.1 데이터 모델
- 데이터를 저장하기 위해 데이터베이스의 구조, 제약조건을 설계하는것. 데이터 모델링이라고도 함
    - 데이터베이스를 구성하는 개체(Entity), 속성(Attribute), 관계(Relationship)를 표현하는 추상화된 모형
    - 데이터의 구조와 의미, 제약조건 등을 체계적으로 표현하는 도구

- 종류
    1. ``계층형``
    2. ``네트워크형``
    3. ``관계형``
    4. ``객체관계형``
### 3.2 기존 데이터 모델
- 계층형DBMS(Hierarchical DBMS)
    - 1960년 후반 IBM사의 ``IMS``
    - ``트리구조`` 기반
    - 동일한 형태의 데이터 집합체 ``세그멘트``간의 부모/자식관계
- 네트워크DBMS
    - ``CODASYL``모델, ``DBTG``모델
    - 1960년 초반 Charles Bachman이 Hoenywell사에서 ``IDS``개발
    - ``그래프구조``기반
    - ``onwer-member``관계표현
- 객체지향DBMS
    - 1980년 후반 객체 지향 프로그래밍의 패러다임을 차용한 DBMS
    - ONTOS, OpenODB, GemStone, ObejctStore, Versant, O2 등
- 객체관계DBMS
    - 관계형 DBMS에 객체지향 개념을 추가한 DBMS
    - Oracle, Informix Universal Server 등
### 3.3 관계형 데이터 모델
- 관계형DBMS 탄생배경
    - 미국 IBM 연구소에서 진행된 ``System R``
    - 캘리포니아 버클리대에서 진행된 Ingres 프로젝트
    - 1970년 ``E.F. Codd``가 IBM연구소에서 제안
    - Oracle, MS SQL Server, Sybase, DB2, Informix 등
- 관계형DBMS 구조
    - database > table > column, low
- 용어 정리
    1. 릴레이션(relation), 테이블(table), 파일(file)
    2. 튜플(tuple), 행(row), 레코드(record)
    3. 속성(attribute), 열(column), 필드(field), 데이터 항목(data item)
        - 데이터의 가장 작은 논리적 단위
    4. 도메인(domain)
        - 각 속성이 취할 수 있는 값의 집합
        1. 단순 도메인(simple)
        2. 복합 도메인(composite)
        3. 다치 속성(miltivalued attribute)
    5. 릴레이션 스키마, 내연(intension), 엔티티 유형(type)
    6. 릴레이션 인스턴스, 릴레이션 어커런스(occurrence), 외연(extension), 릴레이션
    7.  차수(degree)
        - 속성(열)의 개수
    8. 카디널리티(cardinality)
        - 튜플(행)의 개수
- 테이블(릴레이션)의 특징
    1. 튜플의 유일성
    2. 튜플(행)의 무순서
    3. 속성(열)의 무순서
    4. 속성(열)의 원자값(atomic)
        - 속성은 더이상 쪼갤 수 없다.
- 키(key)
    - 슈퍼키(super)
        - 유니크한 키 or 유니크한 키 + 속성
    - 후보키(candidate) 
        - 각 튜플(행)을 고유하게 식별할 수 있는 ``최소한``의 속성들
        - 두개 이상의 속성으로 이뤄져있다면 ``복합키(composite key)``라고 함
    - ``기본키(PK)``
        - 중복이 허용되지 않고 NULL값이 허용되지 않는 고유한 속성값.
        - 후보키 중에서 길이가 짧은 키.
    - 대체키(alternate)
        - 후보키 중에서 PK가 아닌 키.
    - ``외래키(FK)``
        - 다른 테이블의 PK를 참조하는 키.
- 제약 조건(Constraint)
    - 도메인 제약조건
        - 각 속성(열)은 반드시 ``원자값``이어야 함.
    - 키 제약조건
        - 테이블(릴레이션)의 모든 키는 유일한 값이어야함.
    - 엔티티 무결성 제약조건(entity integrity)
        - 릴레이션의 ``기본키(PK)``는 어떠한 경우에도 NULL 값을 가질 수 없다.
    - ``참조 무결성 제약조건``
        - ``외래키(FK)``는 참조하는 테이블의 ``기본키(PK)`` 값과 동일하거나 NULL이어야 한다.
- 관계해석 vs 관계대수 언어

    | 관계해석 | 관계대수 |
    |----------|-----------|
    | 비 절차적 언어 | 절차적 언어 |
    | 선언적 언어 | 수행적 언어 |


### 3.4 관계 데이터베이스 언어
- 관계대수 연산 종류
    1. 제한(Selection) 연산 - σ(시그마)
        - 릴레이션에서 조건을 만족하는 튜플만 선택
    2. 프로젝트(Projection) 연산 - π(파이)
        - 릴레이션에서 지정된 속성만 추출
    3. 조인(Join) 연산 - ⋈
        - 두 릴레이션의 공통 속성을 기준으로 결합
    4. 디비전(Division) 연산 - ÷
        - 한 릴레이션을 다른 릴레이션으로 나누는 연산
    5. 합집합(Union) 연산 - ∪
        - 두 릴레이션의 합집합
    6. 교집합(Intersection) 연산 - ∩
        - 두 릴레이션의 교집합
    7. 차집합(Difference) 연산 - -
        - 두 릴레이션의 차집합
    8. 카티션 프로덕트(Cartesian Product) 연산 - ×
        - 두 릴레이션의 모든 튜플 조합 생성

## 4장 SQL

### View
- `virtual table`
- `query modification`
    - `data dictionary` 에 view생성 명령을 저장해놓고, 해당 명령을 토대로 view의 질의를 대신 수행함. 즉, view테이블에 질의하는것은 view테이블이 참조한 원본 테이블에 view의 조건을 만족하는 가상의 테이블에 질문하는 것임.

- 데이터를 가지고 있지 않다. 
- order by 불가능하다.


### SQL 함수들

``date 타입 함수``
| 함수 | 설명 | 예시 |
|------|------|------|
| `Date()` | 현재 날짜 반환 | `SELECT Date();` → `2025-04-17` |
| `Now()` | 현재 날짜와 시간 반환 | `SELECT Now();` |
| `Year(date)` | 연도 추출 | `Year(#2023-04-17#)` → `2023` |
| `Month(date)` | 월 추출 | `Month(#2023-04-17#)` → `4` |
| `Day(date)` | 일(day) 추출 | `Day(#2023-04-17#)` → `17` |
| `Weekday(date)` | 요일 추출 (1=일요일, 2=월요일...) | `Weekday(Date())` |
| `DatePart("interval", date)` | 특정 부분 추출 (`"yyyy"`, `"m"`, `"d"`, `"ww"` 등) | `DatePart("m", Date())` |
| `DateDiff("interval", date1, date2)` | 두 날짜 간 차이 계산 | `DateDiff("d", #2023-01-01#, #2023-01-10#)` → `9` |
| `DateAdd("interval", number, date)` | 날짜에 기간 더하기 | `DateAdd("m", 2, #2023-01-01#)` → `2023-03-01` |
| `Format(date, "format")` | 날짜 형식 변경 | `Format(Date(), "yyyy-mm-dd")` |
| `IsDate(value)` | 날짜인지 여부 확인 | `IsDate("2025-04-17")` → `True` |

