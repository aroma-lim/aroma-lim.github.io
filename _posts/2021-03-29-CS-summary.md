---
title:	"CS 기술면접 준비 - CS 요약"

tags: [CS, C++]
categories: tech-interview
use_math: true

---
# 외국계 시험 대비 Summary

> **기술면접**을 위해 기초 CS에 대한 복습중이다.
공부한 내용 중 요점이나 나중에 기억해야할 부분을 정리해보려고 한다.
내가 아는 부분은 생략되어 있을 수 있고, 혹여나 틀린 부분이 있을 수도 있으니 이 글을 보고 '다른 사람'이 공부하기에는 도움이 되지 않을 수 있으니 주의!


## 1. C++ templetes
```
templete <typename T>
void swap(T& a, T& b) {
    //...
}
```
- T가 int든, string이든 어느 타입이든 다 될 수 있다.
- generic programming의 특징을 구현할 수 있게 하는 게 templete이다.

## 2. Dynamic allocation
```
int *array = new int[length];
// ...
delete[] array;
```

## 3. Class access control
- private: 클래스 멤버 함수, friend에서만 접근 가능
- protected: private 가능한 부분 + 파생 클래스까지 접근 가능
- public: 어디서든 가능
- static 멤버 변수
    - 같은 클래스 내 모든 객체가 공용으로 사용.
    - 만약 private static이라면 static 멤버 **함수**로 접근 가능
    
## 4. Inheritance
- 파생(Derived) 클래스 객체 생성
    - 기초 클래스 생성자 호출 -> 파생 클래스 생성자 호출
- 소멸
    - 파생 클래스 소멸자 호출 -> 기초 클래스 소멸자 호출
    
## Exception processing
- ``throw std::out_of_range("범위초과");`` 이런 식으로 std안에 여러 종류의 예외를 가지고 있음.
- try 문
    - 예외 발생 가능성이 있는 블록
    - 발생 시 가장 가까운 catch문으로 점프
- ``catch(std::out_of_range& e)``: 발생할 예외에 대해 처리할 내용
```
try {
    blarblar
} catch(blarblar) {

}
// blarblar 부분이 throw부분. try에서 발생한 오류에 대한 정보 전달
```

## 6. C++ Const & Volatile Qualifiers
- Const: 이미 assign된 값을 변경할 수 없다.
- Volatile: 언제 바뀔지 모르는 값이라 최적화하지 말라는 키워드

## 7. C/C++ Preprocessor
- 컴파일러에 앞서 실행
- ``#define``: function-like macro
    - 장점: 빠르고, 타입 신경 안 써도 됨
    - 단점: 단순 치환이라 오류가 많고 디버깅이 어려움. 가독성이 떨어짐.
- ``##``: 두 개의 토큰을 하나의 토큰으로 결합해주는 preprocessor 연산자
    - ``#define XN(n) x ## n`` 이면, XN(1) 호출 시, x ## n 이니까 즉, ``x1``이 된다. 
    - Runtime에 변수를 만들 수 있다.
- ``#pragma once``: 헤더파일 include하는 게 중복되지 않도록 설정해주는 것.

## 8. C++ Standard library
- 표준으로 만들어진 class와 함수들
- h로 끝나지 않는다.
- C 표준은 ~.h를 c~로 변환. ``ex) <time.h> -> <ctime>``
- STL의 영향 많이 받음

## 9. C++ Standard Templete Library
- 템플릿 이용. 제네릭 프로그래밍
- 3가지 분류: 컨테이너, 반복자, 알고리즘
- 컨테이너: 시퀀스 컨테이너(vecter 등), 연관 컨테이너(map, set), 컨테이너 어댑터(stack)

## 10. C++ Basic Concepts
- type system: variable, object, auto, void
- scope: global scope, local scope, class(public/protected/private) scope, statement scope(for/while), function scope, namespace scope(::으로 구분)
- Translation unit: Definition은 한 번만, Declaration은 여러 번 가능
- extern: external linkage
- ``main()``: declaration이 없다. return 값이 없으면 0을 return한다.

## 11. Polymorphism (다형성)
- override, overloading
- Override
    - 추상화(abstraction)와 같이 가는 개념. 
    - virtual로 선언한 걸 상속받아 여러 모양으로 정의할 수 있다. 
    - ex. draw를 네모, 세모, 동그라미 그리는 걸로 상속
    - 자식이 부모 위에 ride해서 재정의해버리는 것
    
## 12. Overloading
- 다형성 중 하나
- 함수 개수나 타입을 달리한 **같은 이름**의 함수를 정의하는 것. 중복 정의

## 13. File and stream I/O
- ``<fstream>``은 ``<ifstream>``과 ``<ofstream>``을 포함한 것.
- ifstream/ofstream으로 객체 생성 -> ``.open("파일이름")``으로 열기 -> ``cin/cout`` -> ``getline`` -> ``.close()``

## 14. Pointer
- ``&``: 주소 연산자. 해당 변수의 주소 값 변환
- ``*``: 참조 연산자. 포인터에 저장된 주소에 저장되어 있는 값 반환
```
int n = 100;
int *ptr = &n;
```