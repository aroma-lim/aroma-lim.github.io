---
title:	"CS 기술면접 준비 - 디자인패턴2"

tags: [CS, 디자인패턴]
categories: tech-interview
use_math: true

---
# Design Pattern 2

> **기술면접**을 위해 기초 CS에 대한 복습중이다.
공부한 내용 중 요점이나 나중에 기억해야할 부분을 정리해보려고 한다.
내가 아는 부분은 생략되어 있을 수 있고, 혹여나 틀린 부분이 있을 수도 있으니 이 글을 보고 '다른 사람'이 공부하기에는 도움이 되지 않을 수 있으니 주의!


## Facade 패턴
- 여러 객체를 만들고 작업하는 것을 facade(외벽)으로 감싸서 사용하는 방식

## Templet-method 패턴
- 세부방식을 다양화하기 위함
- Strategy와 다른 점: Overriding. 추상클래스의 method 절차는 바꿀 수 없음.
    같은 method 절차를 따르는데 그 안 내용이 다름.
    **공통된 절차가 있을 때**

## Decorator 패턴
- 여러 옵션들을 필요에 따라 장착할 수 있게 하는 방식
- abstract에서 상속 받은 자식 클래스들이 ``super``로 부모 메소드도 실행하고, 자체 메소드도 실행하는 방식
- Decorator 여러 개로 감쌀 수도 있음

## Factory-method 패턴
- 특정 종류의 기능들에 사용될 수 있는 클래스들의 종류가 많고 복잡할 때 적용
- 사용할 객체의 조건들만 인자로 넘겨주면 factory클래스가 처리하도록 하는 방식
- 2가지 효용
    1. 만약 생성자 형식 등이 변경되거나 하면 객체 생성할 때마다 다 바꿔줘야 할 것을 factory에서 일괄 처리 가능
    2. 생성자에 대해 다 알 필요 없이 factory에 위임해놓고 개발 가능
- 데코레이터 대신 factory를 사용한다면: 옵션에 따라 인자값(bool 등)만 factory에 넘겨주는 방식으로 구현

## Abstract-factory 패턴
- factory패턴에 추상화를 합친 패턴
- factory를 다양하게 구현. 여러 factory를 만드는 것

## Mediator 패턴
- 여러 클래스들의 관계가 특정 이벤트 중심으로 복잡하게 얽힌 설계에서 유용
- Mediator가 이벤트(모드변경)에 반응하는 클래스들의 list를 가지고 있고, 이벤트에 따른 모드를 일괄적으로 알려주는 방식(중재자 역할)

## Composite 패턴
- 파일 시스템처럼 포함하는 것과 포함되는 것이 같은 방식으로 다뤄질 때 사용하는 패턴

---

**참고한 사이트**
- 유튜브 채널 [얄팍한 코딩사전](https://www.youtube.com/channel/UC2nkWbaJt1KQDi2r2XclzTQ)
    