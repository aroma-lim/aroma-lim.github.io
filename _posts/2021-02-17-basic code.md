---
title:	"Basic Code (C++)"

tags: [C++, string, iterator, hash, set, sort, vector, ascii, binary, limits, unique, erase, combination, permutation, prime]
categories: algorithm
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

    // i번째부터 n개까지만
    s3 = s.substr(i, n);
    ```
- string 뒤집기: ``reverse(s.begin(), s.end());``
- string 정렬하기: ``sort(s.begin(), s.end());``

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

## Hash 사용법
- 할당
    ```
    // hash[key값].push_back(value값);
    hash["aroma"].push_back(100);
    hash[tickets[i][0]].push_back(tickets[i][1]);
    ```

## Set 사용법 (set, unordered_set)
- 할당
    ```
    // set.insert(값);
    set.insert(s1[i]);
    ```

## Sort 사용법
- 헤더 추가: ``#include <algorithm>``
- 내림차순 정렬 (앞 값 > 뒤 값)
```
// 시작, 끝, greater<타입>
sort(s.begin(), s.end(), greater<vector<string>>());
```
- 오름차순 정렬 (앞 값 < 뒤 값; default)
```
// 시작, 끝, less<타입>
sort(v.begin(), v.end(), less<int>());
```
- 참고: string을 sort하면 그 안에 char들을 sort한다.
- 참고2: priority_queue는 greater와 less의 의미가 다르다. 반대로 쓰임. [Heap 참고](https://aroma-lim.github.io//algorithm/heap/)

## 배열/vector
- 선언 및 할당
    ```
    vector<vector<string>> tickets = { { "ICN", "JFK" }, { "ICN", "IAD" }, {"JFK", "HND"} };
    vector<string> s = {"ICN"};
    ```

## 알파벳 다루기 (Ascii)
- A~Z(a~z)까지 26개
    ```
    // 소문자 + n의 index
    char idx = (s[i] - 'a' + n) % 26;
    char s1 = 'a' + idx;

    // 대문자 + n의 index
    char idx = (s[i] - 'A' + n) % 26;
    char s2 = 'A' + idx;
    ```
- 아스키 코드로 대문자가 먼저, 소문자가 나중. 그 사이에 다른 값들 있음 주의!
- A~Z는 65번~90번
- a~z는 97번~122번
- 소문자/대문자 범위
    ```
    // 소문자일 때
    if (s[i] >= 'a' && s[i] <= 'z')

    // 대문자일 때
    if (s[i] >= 'A' && s[i] <= 'Z')
    ```

## 진법 다루기 - 2진수 등
```
// 10진수 -> 2진수로 변환 후 string에 넣기
while (num1 > 0)
{
    s += to_string(num1 % 2);
    num1 /= 2;
}
```

## 배열 동적 할당 (Dynamic Allocation)
```
// 배열 선언
int *arr = new int[n];


// 2중 배열 (2d array)
int **d = new int*[N];

for (int i = 0; i < N; i++)
    d[i] = new int[N];

// 할당 해제
delete[] a;
delete[] d;
```

## 초기화 시 최소값 최대값
```
// 헤더 필요
#include <limits.h>

// 가장 큰 수를 미리 넣어두어 min을 초기화 하고 싶을 때
int min = INT_MAX;
```

## 배열 및 벡터에서 중복값 제거
- unique를 사용해서 중복값을 뒤로 보내고, 다 보낸 뒤 iterator가 바로 그 다음을 가리키고 있어서 거기서 부터 지우면 된다.  
    ```
    // 헤더 필요
    #include <algorithm>

    // unique 후 erase
    v.erase(unique(v.begin(), v.end()), v.end());
    ```

## 조합 공식 (combination)
- 공식: $nCr = nPr / r!$
- 예시: $5C3 = 5P3 / 3! = (5 * 4 * 3) / (3 * 2 * 1)$

## 소수 구하기
1) 간단하게 구하는 방법
```
bool isPrime(int n) {
    if (n == 0 || n == 1) return false;

    for (int i = 2; i <= sqrt(n); i++) {
        if (n % i == 0) return false;
    }
    return true;
}
```
2) [아리토스텔레스의 체](https://ko.wikipedia.org/wiki/%EC%97%90%EB%9D%BC%ED%86%A0%EC%8A%A4%ED%85%8C%EB%84%A4%EC%8A%A4%EC%9D%98_%EC%B2%B4)로 구하는 방법

## 순열 구하는 함수
- **next_permutation**함수: ``<algorithm>`` 헤더에 포함되어 있다.

```
// 반드시 오름차순으로 정렬 후 시행해야 한다.
sort(numbers.begin(), numbers.end());

do {
        // do sth...

    } while (next_permutation(numbers.begin(), numbers.end()));
```
