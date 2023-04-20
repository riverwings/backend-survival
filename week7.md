---
description: 7주차 강의
---

# 1. ORM
### ORM(객체-관계 매핑)
객체 지향 프로그래밍 언어에서 사용되는 객체와 관계형 데이터베이스의 데이터를 매핑하는 기술이며, ORM을 사용하면 객체 지향적인 방식으로 데이터를 다룰 수 있어서 개발자가 데이터베이스와 상호 작용하는 코드를 작성하는 데 필요한 시간과 노력을 줄일 수 있음.
 
### JPA(Jakarta Persistence API)
ORM 기술 중 하나이며, 자바 애플리케이션에서 객체와 관계형 데이터베이스를 매핑하는 표준 기술. JPA는 애플리케이션 개발자가 데이터베이스와의 상호 작용을 추상화하고, 표준화된 방식으로 데이터베이스를 조작할 수 있도록 지원함.<br>
Relationship Mapping과 Aggregate Mapping 등을 지원하고, 이를 잘 활용함으로써 객체와 관계를 적절히 조화시킬 수 있음.

### Jakarta EE
이전에는 Java EE로 알려졌고, 자바 기반의 서버 사이드 애플리케이션 개발을 위한 플랫폼. Jakarta EE는 자바 서버 애플리케이션 개발에 필요한 여러 가지 API를 제공하며, JPA도 Jakarta EE의 일부임.

### Entity
JPA에서 데이터베이스의 테이블과 매핑되는 자바 클래스. Entity 클래스는 데이터베이스 테이블의 각 열(column)과 매핑되는 멤버 변수를 포함하고 있으며, JPA를 사용하여 이러한 엔티티 클래스를 조작할 수 있음. 엔티티 클래스의 인스턴스는 데이터베이스의 테이블 레코드와 일치하며, JPA는 엔티티 클래스의 인스턴스와 데이터베이스 레코드 간의 매핑을 처리함.
<br>

# 2. Hibernate
### Hibernate
ORM 기술 중 하나로, 객체와 관계형 데이터베이스 간의 매핑을 쉽게 처리할 수 있도록 지원하는 자바 오픈소스 프레임워크. Hibernate는 JPA의 구현체 중 하나이며, JPA에서 정의한 기능들을 모두 포함하고 있음.

### 데이터 모델 / 객체 모델
데이터 모델은 데이터베이스에서 사용하는 테이블, 컬럼, 제약 조건 등의 구조를 말하며, 객체 모델은 자바 언어에서 사용하는 클래스, 객체, 상속 등의 구조를 말함. Hibernate를 사용하면 데이터 모델과 객체 모델 간의 매핑을 간단하게 처리할 수 있으며, 객체 지향적인 방식으로 데이터베이스를 다룰 수 있음.

### entityManager
JPA를 사용하여 데이터베이스와 상호 작용할 때 사용하는 중요한 객체. entityManager는 엔티티의 영속성(persistence)을 관리하며, 데이터베이스와의 통신을 담당함.

### 트랜잭션
데이터베이스에서 한 번에 처리해야 할 일련의 작업들을 하나의 작업 단위로 묶어서 처리하는 것을 말함. JPA에서는 트랜잭션을 사용하여 엔티티 매니저를 통해 데이터베이스와의 상호 작용을 할 때, 데이터베이스 상태를 안정적으로 유지할 수 있음.

### JPQL(Java Persistence Query Language)
JPA에서 사용하는 쿼리 언어. JPQL은 객체 지향적인 방식으로 데이터베이스를 다룰 수 있도록 지원함. 엔티티 객체를 대상으로 쿼리를 작성할 수 있으며, SQL과 유사한 문법을 사용. JPQL을 사용하면 객체지향적인 방식으로 데이터베이스를 조회하고 조작할 수 있음.
<br>

# 3. Embeddable
JPA에서 엔티티(Entity)에서 다른 엔티티를 포함하는 객체를 말함. Embeddable 객체는 다른 엔티티와 관련된 정보를 담고 있으며, 해당 엔티티와 함께 영속성을 유지함.
### Aggregate Mapping
JPA에서 객체 간의 연관 관계를 표현하는 방식 중 하나. Aggregate Mapping은 하나의 엔티티를 기준으로 연관된 엔티티를 그룹으로 묶어서 표현함.
#### Value Object
객체를 구성하는 값들을 하나로 묶어서 표현하는 객체. Value Object는 엔티티(Entity)와 다르게 식별자(ID)를 가지지 않으며, 불변성(immutable)을 유지해야 함. Value Object는 엔티티의 속성으로 사용되며, 값이 변경될 경우 해당 엔티티의 상태도 변경됨.
#### JPA 어노테이션
- @Entity: JPA에서 엔티티 클래스를 정의할 때 사용하는 어노테이션.
- @Table: 엔티티와 매핑될 데이터베이스 테이블의 정보를 지정하는 어노테이션.
- @Id: 엔티티의 식별자(ID)를 지정하는 어노테이션.
- @Embeddable: Embeddable 클래스를 정의할 때 사용하는 어노테이션.
- @Embedded: Embeddable 클래스를 사용하는 엔티티의 속성을 지정하는 어노테이션. Embeddable 객체를 엔티티의 속성으로 사용하려면 해당 속성에 @Embedded 어노테이션을 붙여야 함.
<br>

# 4. Relationship Mapping
JPA에서 엔티티(Entity) 간의 연관 관계를 표현하는 방식 중 하나. JPA에서는 @OneToMany, @ManyToOne, @OneToOne, @ManyToMany 등의 어노테이션을 사용하여 엔티티 간의 관계를 매핑함.
### N + 1 problem
JPA에서 데이터를 조회할 때 발생하는 성능 문제 중 하나. 이 문제는 하나의 엔티티와 그와 연관된 다른 엔티티를 함께 조회할 때, 연관된 엔티티를 조회하는 쿼리가 너무 많이 실행되어 성능이 저하되는 문제임.
### DDD의 Aggregate
도메인 주도 설계(Domain Driven Design)에서 사용되는 개념 중 하나. Aggregate는 연관된 객체들을 하나의 논리적인 단위로 묶어서 캡슐화하는 개념임.
### CascaseType.All
JPA에서 엔티티의 영속성(persistence)을 관리하는 옵션 중 하나이며, 엔티티를 저장할 때 연관된 모든 엔티티도 함께 저장하도록 설정하는 옵션.
### orpahanRemoval
CascadeType.Remove와 유사한 옵션으로, 부모 엔티티와 연관된 자식 엔티티를 삭제할 때 자식 엔티티를 자동으로 제거하는 옵션.
### Event Sourcing
소프트웨어 개발에서 사용되는 패턴 중 하나. 이 패턴은 모든 변경 사항을 이벤트(Event)의 형태로 저장하고, 변경 이벤트를 사용하여 애플리케이션의 상태를 재구성하는 방식으로 동작함.
### JPA 어노테이션
- @OneToMany: 엔티티 간의 일대다 관계를 정의할 때 사용하는 어노테이션.
- @JoinColumn: 엔티티 간의 관계에서 연관 키(외래 키)를 지정할 때 사용하는 어노테이션. 이 어노테이션을 사용하면 연관된 엔티티의 ID를 저장하는 컬럼을 생성할 수 있음.
<br>

# 5. Spring Data JPA
### Spring Data JPA
Spring Framework에서 JPA를 쉽게 사용할 수 있도록 지원하는 프레임워크. Spring Data JPA를 사용하면, 기본적인 CRUD(Create, Read, Update, Delete) 기능을 간단하게 구현할 수 있고, 쿼리 메서드(Query Method)를 사용하여 복잡한 쿼리도 쉽게 구현할 수 있음.
### Dao 와 Repository 차이
Dao와 Repository는 모두 데이터 액세스 계층(Data Access Layer)에서 사용되는 개념. Dao(Data Access Object)는 전통적인 방식의 데이터 액세스 계층에서 사용되는 개념으로, 데이터베이스에 접근하여 데이터를 조작하는 메서드들을 포함함. Repository는 Spring Data JPA에서 사용되는 개념으로, JPA를 쉽게 사용하기 위한 추상화된 인터페이스를 제공함.
### JPA Repository와 DDD의 Repository
서로 다르게 사용됨. JPA Repository는 Spring Data JPA에서 제공하는 인터페이스로, JPA를 쉽게 사용할 수 있도록 많은 기능을 제공함. DDD의 Repository는 도메인 주도 설계(Domain Driven Design)에서 사용되는 개념으로, 도메인 모델과 데이터베이스 사이의 매핑을 처리함.
### Spring AOP(Aspect-Oriented Programming)
객체지향 프로그래밍에서의 관점 지향 프로그래밍 기법. Spring AOP는 메서드 실행 전후, 예외 발생 시 등의 시점에서 공통적으로 수행해야 하는 작업을 분리하여 모듈화할 수 있음.
### @Transactional
Spring에서 제공하는 트랜잭션 관리를 위한 어노테이션. 이 어노테이션을 메서드에 추가하면, 해당 메서드가 실행될 때 트랜잭션을 시작하고, 메서드 실행이 완료되면 트랜잭션을 커밋하거나 롤백함. 또한, readOnly, propagation, isolation, timeout 등의 속성을 설정하여 트랜잭션의 동작 방식을 조정할 수 있음.