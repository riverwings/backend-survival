---
description: 2주차 강의
---

# 1. REST API
### API(Application Programming Interface)
 여러 프로그램들과 데이터베이스, 기능들의 상호 통신 방법을 규정하고 도와주는 매개체이다. 각자 권한 분야에서 필요한 것만 연계할 수 있도록 해주는 서비스.
 - 장점
   - 데이터 접속의 표준화와 편의성: 모든 접속을 표준화하기 때문에 디바이스/ 운영체제 등과 상관없이 조건만 맞다면, 누구나 동일한 엑세스를 약속.
   - 자동화와 확장성: API를 통한 CRUD 처리에 따라 관련 데이터와 콘텐츠가 자동으로 생성되고 사용자의 환경에 맞춰 정보가 전달되어 개발 워크플로우가 간소화되고 애플리케이션 확장이 다소 용이하다.
   - 적용력: 변화 예측에 큰 도움이 되기 때문에 데이터를 수집하고 전달하는 데 있어 유연한 서비스 환경을 구축할 때 용이.
 - 단점
   - 보안성과 HTTP 방식의 제한: API의 단일 진입점인 API 게이트웨이는 해커의 타겟 대상이 될 수 있고, HTTP 메서드를 사용하여 액세스 할 수 있지만 HTTP method는 메서드 형태가 다소 제한적이라는 문제점이 있다.
   - 표준의 무재와 개발 비용: 공식화 된 표준이 존재하지 않으므로 관리가 어렵고, 개발 시간, 지속적인 유지 관리 요구사항 및 지원 제공 측면에서 비용이 많이 들 수 있다.
### 정보은닉(Information Hiding)과 캡슐화(Encapsulation)
정보 은닉은 객체지향 언어적 요소를 활용하여 객체에 대한 구체적인 정보를 노출시키지 않도록 하는 기법을 칭한다. 대표적으로 세가지 정도가 있다.
 1. 객체의 구체적인 타입 은닉 => 업캐스팅
 2. 객체의 필드 및 메소드 은닉 => 캡슐화: 변수나 메서드들을 캡슐로 감싸 안보이게 하는 정보 은닉 개념중 하나이다. 객체의 속성(Field)과 행위(Method)를 하나로 묶고, 외부로부터 내부를 감싸 숨겨 은닉한다. 또한 외부의 잘못된 접근으로 값이 변하는 의도치 않는 동작을 방지하는 보호 효과도 누릴 수 있다.
 3. 구현 은닉 => 인터페이스 & 추상 클래스
### Architecture와 Architecture Style의 차이
시스템의 소프트웨어 아키텍처는 시스템에 대해 추론하는 데 필요하는 구조의 집합으로, 소프트웨어 구성요소(Element)와 속성(Properties)으로 구성된다.
아키텍처 스타일은 소프트웨어 시스템을 위한 구조적인 스키마이다.
### REST

<br>


# 2. URI & MIME type

### URI & URL & URN
<br><br>

### MIME type
<br><br>


# 3. Collection Pattern
<br><br>

# 4. Collection pattern 적용
### CQS
 
<br><br>

# 5. Spring Web MVC로 구현
- @RequestMapping
    - @GetMapping
    - @PostMapping
    - @PatchMapping
    - @DeleteMapping
    - @PathVariable
- @RequestBody
- @ExceptionHandler
- @ResponseStatus

