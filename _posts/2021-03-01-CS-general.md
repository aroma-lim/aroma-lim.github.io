---
title:	"CS 기술면접 준비 - 개발 상식"

tags: CS
use_math: true

---
# 개발 상식

> **기술면접**을 위해 기초 CS에 대한 복습중이다.
공부한 내용 중 요점이나 나중에 기억해야할 부분을 정리해보려고 한다.
내가 아는 부분은 생략되어 있을 수 있고, 혹여나 틀린 부분이 있을 수도 있으니 이 글을 보고 '다른 사람'이 공부하기에는 도움이 되지 않을 수 있으니 주의!


## OOP
- 장점: 재사용성, 생산성↑, 유지보수 용이, 디버깅 용이, 대형 프로젝트 함에 있어 분담 용이
- 5가지 키워드: 클래스&객체, 추상화, 캡슐화, 상속, 다형성
    - 추상화: 공통의 속성이나 기능을 묶어 이름을 붙이는 것. Class 정의
    - 다형성: 오버라이딩, 오버로딩(매개 변수 수나 타입을 달리하는 것)
- 객체지향 설계원칙(SOLID)
    - Single Responsible Principle: 단일 책임 원칙. 클래스의 단 하나의 책임
    - Open-Closed Principle: 확장성에 대해선 개방, 변경 가능성에 대해서는 패쇄
    - Liskov Substitution Principle: 상위 타입 객체를 하위 타입으로 치환해도 상위 타입을 사용하는 프로그램은 정상 동작
    - Interface Segregation Principle: 인터페이스는 클라이언트 기준으로 분리
    - Dependency Inversion Principle: 고수준 모듈은 저수준 모듈을 의존해선 안됨
- Interface와 추상클래스의 차이
    - 인터페이스는 공통적인 것을 장착하는 느낌이라면, 추상클래스는 상속해주는 부모클래스
    - 여러 인터페이스를 가질 순 있지만, 여러 추상클래스에서 상속 받는 건 불가능 (다중상속 vs 단일상속)
    - 인터페이스는 모든 메소드가 추상 메소드이지만, 추상클래스는 일부만 추상 메소드
    - 둘 다 객체를 생성할 수 없다.

## RESTful API
- REST의 기본 원칙을 지킨 API
- 개발자들 사이에서 널리 알려진 약속. 어떤 URI에 어떤 Method를 사용할지
- URI: 자료를 구조와 함께 나타내는 구분자. **리소스**. 명사. 소문자
- HTTP Method: 자원에 대한 행위. CRUD
    - POST, GET, PUT/PATCH, DELETE

## TDD (Test-Driven Development)
- 새로운 기능을 추가하기 전에 테스트 코드를 먼저 작성
- (TDD라는 걸 몰랐지만, 미국인 사수와 같이 일할 때 이런 식으로 자주 코드를 작성했었다.)

## 함수형 프로그래밍
- 선언형: 명령형과 달리 ``이거는 이거다`` 식으로 선언. Input이 같으면 Output은 **항상** 같다.
- 함수도 **값**이다: 함수는 행위라고만 생각해왔던 개념과 달리 값처럼 사용된다.
- 고계 함수: 인자로 함수를 받아서 내보내는 함수, 다른 함수를 반환하는 함수 등 (런타임 중에도 함수가 만들어질 수 있음)

## GC - 가비지컬렉터
- mark-and-sweep: Root에서 닿지 않는 것, 즉 mark 안된 것을 쭉 훑어서 지움
- reference counting: 몇 번 참조되는지 count하는 방식. count가 0이 되면 지움
    - 주의: 순환 참조하는 게 있으면 제대로 동작하지 않을 수 있다.
    
## MVC
- Model: 데이터. DB에서 불러온 Class, object 등
- View: Model의 데이터를 User 눈에 보이게 시각화
- Controller: Model과 View 사이에서 제어해줌. Routing(주소)

---

**참고한 사이트**
- 유튜브 채널 [얄팍한 코딩사전](https://www.youtube.com/channel/UC2nkWbaJt1KQDi2r2XclzTQ)
