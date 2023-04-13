---
description: 6주차 강의
---

# 1. Database
### Database 란
컴퓨터 시스템에서 데이터를 구성하고 저장하며, 검색하고 업데이트할 수 있는 구조적인 방법을 제공하는 데이터의 집합.<br>
일반적으로 여러 개의 테이블로 구성되며, 각 테이블은 데이터를 저장하는 레코드의 집합으로 구성 됨. 각 레코드는 필드(field) 또는 열(column)로 구성된 데이터 요소의 집합.<br>
데이터베이스를 사용하면 여러 사용자가 데이터에 동시에 접근할 수 있으며, 데이터의 일관성과 무결성을 보장할 수 있음.
 
### DBMS(Database Management System)
데이터베이스를 관리하는 소프트웨어이며, 데이터를 생성, 수정, 삭제 및 검색하는 기능을 제공함.

### RDBMS(Relational Database Management System)
관계형 데이터베이스 모델을 기반으로 하는 DBMS이며, 데이터를 테이블 형태로 저장하며, 각 테이블은 키(key)와 속성(attribute)으로 구성됨.

### 데이터베이스 언어
- DDL(Data Definition Language): 데이터베이스의 구조를 정의하는 데 사용되는 언어이며, DDL 명령어로 테이블 생성, 변경, 삭제 등이 가능함.
- DML(Data Manipulation Language): 데이터를 조작하는 데 사용되는 언어이며, DML 명령어로 데이터를 삽입, 수정, 삭제, 검색 등이 가능함.
- DCL(Data Control Language): 데이터베이스의 보안과 권한 관리를 위해 사용되는 언어이며, DCL 명령어로 사용자 권한 설정, 권한 취소 등이 가능함.

### SQL(Structured Query Language)
데이터베이스를 조작하기 위해 사용되는 표준 데이터베이스 언어이며, DDL, DML, DCL을 모두 지원한다.

### 데이터 모델(Data Model)
데이터의 구조를 나타내는 방법론.<br>데이터베이스는 여러 종류의 데이터 모델을 사용할 수 있으며, 관계형 데이터 모델은 가장 널리 사용되는 모델임.
- 관계형 데이터 모델: 테이블을 사용하여 데이터를 저장하고, 테이블 간의 관계를 이용하여 데이터를 연결하는 모델.<br> 각 테이블은 열(column)과 행(row)으로 구성됨.

### 튜플
관계형 데이터베이스에서 하나의 레코드를 나타내는 용어이며, 하나 이상의 속성(attribute)으로 구성됨. 각 속성에는 값을 저장할 수 있음.
<br>

# 2. Relational Model
### 관계형 데이터 모델 용어 정리
- 속성(Attribute): 테이블에서 대게 열(Column)으로 구현 됨. 이름과 타입으로 구성되며, 이름은 집합안에서 유일해야 함. 각 속성은 해당 테이블에서 저장되는 데이터의 특성을 나타냄.<br>예) 학생 테이블의 속성: 학번/문자열, 이름/문자열, 나이/정수
- 튜플(Tuple): 테이블에서 대게 행(Row), Record로 구현 됨. (속성, 값) 쌍의 집합.<br> 예) 학생 테이블의 튜플: {(학번/문자열, 13학번), (이름/문자열, 강나래), (나이/정수, 29)}<br>튜플은 집합이기에 중복을 허용하지 않지만, 대부분의 RDBMS는 PK와 UNIQUE를 제외하고 중복을 허용하고 NULL도 허용함.
- 관계(Relation): 테이블 간의 관계를 나타냄. (속성의 집합, 튜플의 집합) 쌍. 속성의 집합을 heading, 튜플의 집합을 body로 구분함. 그냥 관계는 튜플의 집합이라 할 수 있음. 대게는 Table로 구현되며, 속성 집합을 Schema로 표현함.<br>
```
// 예)
(
    // Heading
    {학번/문자열, 이름/문자열, 나이/정수},

    // Body
    {
        {(학번/문자열, 13학번), (이름/문자열, 강나래), (나이/정수, 29)},
        {(학번/문자열, 15학번), (이름/문자열, 이도영), (나이/정수, 27)}
    }
)
people => 관계변수
```
관계는 시간에 따라 변하므로, 관계 변수란 개념을 구분하여 사용할 수 있음.
- 관계변수(Relation Value): 특정 관계(Relation)에 대한 참조를 나타내는 변수. 즉, 특정 데이터베이스에서 관계형 데이터 모델을 사용할 때, 관계변수는 특정 테이블에 해당하는 데이터의 참조를 가리키는 변수로 사용될 수 있음.
<br>

# 3. Relational Algerbra
### 관계 대수
관계형 데이터 모델에서 데이터를 다루기 위한 형식적인 언어이며, 데이터를 조작하고 처리하기 위해 일련의 연산자와 규칙을 제공함.<br>
관계 대수는 일반적으로 집합론(Set Theory)에 기반을 둔 형태로 구성되며, 이를 통해 데이터베이스에서 데이터를 선택, 조합, 필터링, 연결 등의 연산을 수행할 수 있음.<br>
#### 연산
하나 이상의 Relation으로 두 개 이상의 Relation을 만들 수 있다.
 - 단항 연산: Selection, Projection, Rename, ...
 - 이항 연산: Cartesian Product, Set Union, Set Difference, ...
#### 주요 연산
- 선택(Selection): 주어진 술어(거칠게 말하면 "조건")를 만족하는 튜플만 선택. SQL에선 SELECT문의 WHERE절로 술어를 표현할 수 있음.
- 투영(Projection): 튜플에서 원하는 속성만 선택하여 새로운 테이블을 생성. SQL에선 SELECT절 바로 뒤에 속성 이름을 나열하는 방식으로 표현할 수 있음. 특별히 속성을 제한하고 싶지 않다면 와일드카드(*)를 쓰면 됨.
- 교집합(Intersection): 두 개의 테이블에서 공통된 튜플만 선택.
- 합집합(Union): 두 개의 테이블에서 중복을 제거하고 모든 튜플을 선택.
- 곱집합(Cartesian Product): 원래의 의미와 다름. 원래는 각 요소의 쌍을 요소로 취하지만(x와 y가 있다면 (x, y)를 새로운 요소로 사용), 관계 대수에서는 그냥 튜플을 합침. SQL에서는 FROM 뒤에 관계(SQL에서는 Table)이름을 나열하면 됨.<br>
```
// 곱집합
SELECT people.name AS person_name, items.name AS item_name
FROM people, items
WHERE people.name = person_name;

// Join
SELECT people.name, age, gender, items.name AS item_name, usage
FROM people
JOIN items ON people.name = items.person_name;
```
이 외에도 다양한 관계 대수 연산자들이 존재하며, 이를 조합하여 복잡한 쿼리를 수행할 수 있음.
<br>

# 4. Entity-Relationship Model
### ERM(Entity-Relationship Model) 이란
ERD(Entity-Relationship Diagram) 또는 ERM(Entity-Relationship Model)은 개체(Entity)와 개체 간의 관계(Relationship)를 그래픽으로 표현하는 데이터 모델링 방법 중 하나이며, 가자 인기 있는 개념적 데이터 모델. ERD는 관계형 데이터베이스 설계에 자주 사용되며, 데이터베이스 구조와 데이터 흐름을 시각적으로 파악하기 쉽게 만들어 줌.
### Entity
데이터베이스에서 정보를 저장하고 처리하기 위한 객체 또는 개념.
ER 모델에서 Entity는 개별적으로 다룰 수 있는 데이터를 의미.<br>예)"사용자", "주문", "상품"<br>
보통 속성(Attribute)을 가지며, 이 속성을 이용하여 Entity를 식별하거나 그에 대한 정보를 관리함.<br>
ER 모델에서 Relationship은 Entity 사이의 관계를 의미함. 관계형 데이터베이스의 관계(Relation)를 ERM의 관계(Relationship)로 잘못 알고 있는 경우가 많으니 주의!
### 데이터베이스 정규화(Database Normalization)
데이터베이스 설계 과정에서 중복 데이터를 제거하고 데이터를 분해하는 과정.<br>
정규화는 1차 정규화, 2차 정규화, 3차 정규화 등의 단계로 이루어지며, 각 단계에서는 특정 조건을 만족하는 데이터베이스 스키마(Schema)로 분해함. 이를 통해 데이터 중복이나 이상 현상을 최소화하면서도 데이터의 일관성과 신뢰성을 유지할 수 있음.
<br>

# 5. JDBC
### JDBC(Java Database Connectivity)
자바 프로그램에서 관계형 데이터베이스에 접속하여 데이터를 조회, 수정, 삭제할 수 있도록 하는 자바 API. JDBC는 자바에서 표준적으로 제공되며, 데이터베이스 제조사나 버전에 상관없이 동일한 방식으로 데이터베이스와 상호작용할 수 있음.<br>
JDBC를 사용하면 자바 애플리케이션에서 다양한 데이터베이스에 접속할 수 있으며, SQL 쿼리를 실행하여 데이터를 조회하거나 수정할 수 있음.<br>JDBC를 사용하려면 우선 JDBC 드라이버를 로드하고, 데이터베이스 연결을 설정한 다음, SQL 쿼리를 실행하여 데이터를 처리함.

JDBC는 다른 자바 라이브러리나 프레임워크와 연동하여 사용할 수 있음. 예) Spring Framework에서 JdbcTemplate을 제공하여 JDBC를 더 쉽게 사용할 수 있음.
<br>

# 6. JdbcTemplate
### JdbcTemplate
Spring Framework에서 제공하는 JDBC 추상화 라이브러리 중 하나이며, JDBC를 사용하여 데이터베이스와 상호작용하는 코드를 간결하게 작성할 수 있도록 도와줌.

데이터베이스 연결 설정, SQL 쿼리 실행, 쿼리 결과 처리 등 다양한 기능을 제공하여, JdbcTemplate을 사용하면 JDBC API를 직접 사용하는 것보다 코드 양이 적어지고, 예외 처리, 리소스 해제 등의 부수적인 작업을 자동으로 처리할 수 있음. 