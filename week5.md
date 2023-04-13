---
description: 5주차 강의
---

# 1. Dependency Injection
### Spring AOP(Aspect Oriented Programming)
 AOP는 Aspect Oriented Programming의 약자로 관점 지향 프로그래밍으로 불린다.<br>
 관점 지향은 어떤 로직을 기준으로 핵심적인 관점, 부가적인 관점으로 나누어서 보고 그 관점을 기준으로 각각 모듈화하겠다는 것. 모듈화란 어떤 공통된 로직이나 기능을 하나의 단위로 묶는 것을 말함.<br>
AOP에서 각 관점을 기준으로 로직을 모듈화한다는 것은 코드들을 부분적으로 나누어서 모듈화하겠다는 의미이며, 소스 코드 상에서 다른 부분에 계속 반복해서 쓰이는 코드(흩어진 관심사_Crosscutting Concerns)를 Aspect로 모듈화하고 핵심적인 비즈니스 로직에서 분리하여 재사용하겠다는 것이 AOP의 취지이다.
- AOP의 주요 개념
  - Aspect: 흩어진 관심사를 모듈화 한 것. 주로 부가 기능을 모듈화 함.
  - Target: 클래스나 메서드 등 Aspect를 적용하는 곳
  - Advice: 실질적으로 해야할 일에 대한 것. 실질적 부가기능을 담은 구현체
  - JointPoint: Advice가 적용될 위치, 끼어들 수 있는 지점. 메서드 진입 지점, 생성자 호출 시점, 필드에서 값을 꺼내 올 때 등 다양한 시점에 적용 가능
  - PointCut: JointPoint의 상세한 스펙을 정의ㅣ한 것으로 구체적으로 Advice가 실행될 지점을 정할 수 있음.

- Spring AOP 특징
  - 프록시 패턴 기반의 AOP 구현체, 접근 제어 및 부가기능을 추가하기 위해 프록시 객체를 사용함.
  - Spring bean에만 AOP를 적용 가능
  - 모든 AOP 기능을 제공하는 것이 아닌 Spring IoC와 연동하여 엔터프라이즈 애플리케이션에서 흔한 문제(중복코드, 프록시 클래스 작성의 번거로움, 객체들 간 관계 복잡도 증가 등)에 대한 해결책을 지원하는 것이 목적

### Dependency Injection
의존성 주입.<br>
한 객체가 어떤 객체(구체 클래스)에 의존할 것인지는 별도의 관심사. Spring은 의존성 주입을 도와주는 DI컨테이너로서, 강하게 결합된 클래스들을 분리하고, 애플리케이션 실행 시점에 객체 간의 관계를 결정해 줌으로써 결합도를 낮추고 유연성을 확보해준다. 이러한 방법은 상속보다 훨씬 유연하다. 단, 한 객체가 다른 객체를 주입받으려면 반드시 DI 컨테이너에 의해 관리되어야 한다.

### 싱글턴 패턴
싱클턴은 오직 하나의 객체만을 생성할 수 있는 클래스를 말하며, 싱글턴 패턴을 사용하면 쉽게 객체의 유일성을 보장할 수 있다.<br>

### IoC(Inversion of Control)


### Spring Bean

### BeanFactory

<br>

# 2. Unit Test
### V 모델


### Test Matrix


### 내적 품질(테스트 코드 작성 등)을 높이면 좋은 이유


### JUnit

### 단위 테스트

### E2E 테스트

<br>

# 3. Spring Test
### 통합 테스트(Integration Test)


### @Autowired


### @SpyBean

### MockMvc


### @SpyBean


### MockBean


### @WebMvcTest


