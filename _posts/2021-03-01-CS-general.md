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

## RESTful API
- REST의 기본 원칙을 지킨 API
- 개발자들 사이에서 널리 알려진 약속. 어떤 URI에 어떤 Method를 사용할지
- URI: 자료를 구조와 함께 나타내는 구분자. **리소스**. 명사. 소문자
- HTTP Method: 자원에 대한 행위. CRUD
    - POST, GET, PUT/PATCH, DELETE
    