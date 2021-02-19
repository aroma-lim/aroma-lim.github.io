---
title:	"Basic Code (C++)"

tags: C++
use_math: true

---
# 코딩 테스트에서 자주 쓰이는 기본 문법들

> **기술면접**을 위해 기초 CS에 대한 복습중이다.
공부한 내용 중 요점이나 나중에 기억해야할 부분을 정리해보려고 한다.
내가 아는 부분은 생략되어 있을 수 있고, 혹여나 틀린 부분이 있을 수도 있으니 이 글을 보고 '다른 사람'이 공부하기에는 도움이 되지 않을 수 있으니 주의!


## String 사용법
- String 크기: ``s.length();`` 혹은 ``s.size()``
- String의 첫 문자: ``s.front();``
- String의 끝 문자: ``s.back();``
- String 찾기: ``s.find("aroma");``라고 하면 aroma라는 단어가 나오기 시작하는 곳의 index를 반환
- String 맨 뒤에 문자 추가하기: ``void push_back(char a);``
- String 맨 뒤에 문자 삭제하기: ``s.pop_back();``
- String에서 부분 string 만들기: 

    ```
    // i번째부터 끝까지
    s1 = s.substr(i);  
    
    // i번째부터 끝까지 (s.length() - i 값은 남은 길이이기 때문에)
    s2 = s.substr(i, s.length() - i);  
    ```
- string 뒤집기: ``reverse(s.begin(), s.end());``

## 컨테이너 순환문
Hash 같은 거는 숫자로 iterator를 사용할 수 없기 때문에 해당하는 iterator가 필요하다.
직접 선언할 수도 있겠지만 간단하게 auto를 사용해도 된다.

```
for(auto& i : hash) {
    // i에 해당하는 key는 first, value는 second이다.
    cout << i.first << " " << i.second << endl;
    
    // i에 해당하는 원소 출력
    cout << *i << endl;
}
```

## Sort 사용법
- 헤더 추가: ``#include <algorithm>``
- 오름차순 정렬
```
// 시작, 끝, greater<타입>
sort(s.begin(), s.end(), greater<vector<string>>());
```
- 내림차순 정렬
```
// 시작, 끝, less<타입>
sort(v.begin(), v.end(), less<int>());
```

## Hash 사용법
- 할당
    ```
    // hash[key값].push_back(value값);
    hash["aroma"].push_back(100);
    hash[tickets[i][0]].push_back(tickets[i][1]);
    ```

## 배열/vector
- 선언 및 할당
    ```
    vector<vector<string>> tickets = { { "ICN", "JFK" }, { "ICN", "IAD" }, {"JFK", "HND"} };
    vector<string> s = {"ICN"};
    ```