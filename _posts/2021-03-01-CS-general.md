---
title:	"CS 기술면접 준비 - 개발 상식"

tags: CS
categories: 기술면접
use_math: true

---
# 개발 상식

> **기술면접**을 위해 기초 CS에 대한 복습중이다.
공부한 내용 중 요점이나 나중에 기억해야할 부분을 정리해보려고 한다.
내가 아는 부분은 생략되어 있을 수 있고, 혹여나 틀린 부분이 있을 수도 있으니 이 글을 보고 '다른 사람'이 공부하기에는 도움이 되지 않을 수 있으니 주의!


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

## 32bit & 64bit
- CPU가 한 번에 처리할 수 있는 메모리 크기
- 64bit가 더 빠른 이유: 데이터 입출력이 줄고 연산이 빠르기 때문
- ``int``는 시스템의 기본 단위의 크기
    - 16bit 컴퓨터: 2byte
    - 32bit 컴퓨터: 4byte
    - 64bit 컴퓨터: 4byte (이게 익숙해서 그냥 4byte라는 이야기가 있음)
    ※ 대신 long은 64bit 컴퓨터에서 8byte이다.

---

**참고한 사이트**
- 유튜브 채널 [얄팍한 코딩사전](https://www.youtube.com/channel/UC2nkWbaJt1KQDi2r2XclzTQ)
