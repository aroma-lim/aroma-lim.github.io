---
title:	"Permutation 순열 (C++)"

tags: C++
categories: algorithm
use_math: true

---
# 순열 - 재귀함수 (C++)

> **기술면접**을 위해 기초 CS에 대한 복습중이다.
공부한 내용 중 요점이나 나중에 기억해야할 부분을 정리해보려고 한다.
내가 아는 부분은 생략되어 있을 수 있고, 혹여나 틀린 부분이 있을 수도 있으니 이 글을 보고 '다른 사람'이 공부하기에는 도움이 되지 않을 수 있으니 주의!


## 재귀함수로 구현
```
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

/* 순열 알고리즘 */
void Permutation(vector<int>& Array, int Start, int End)
{
    // 시작과 끝이 같으면 모든 인덱스 순환했다는 뜻
    if (Start == End) {
        for (const auto it : Array) {
            cout << it << " ";
        }
        cout << endl;
    }
    // 인덱스가 서로 다르면
    else {
        // 모든 인덱스에 대해 
        for (int i = Start; i <= End; ++i) {
            // 시작과 해당 자리 인덱스 바꾸고
            swap(Array[Start], Array[i]);
            
            // 시작을 +1만큼 이동시켜 재귀적으로 호출
            Permutation(Array, Start + 1, End);
            
            // 원래 상태로 되돌림
            // 그래야 다음 인덱스 차례에서 쓸 수 있음
            swap(Array[Start], Array[i]);
        }
    }
}
```

내가 이해한 바로는,
인덱스를 돌면서 그 인덱스에 해당하는 값을 앞쪽에 고정해놓고
나머지를 자리 바꾸는 식으로 경우의 수를 따지는 방식이다.
그 **"나머지"**라는 게 재귀적으로 호출되는 방식이다.

---
※ 출처: [미누시님 블로그](https://minusi.tistory.com/entry/%EC%88%9C%EC%97%B4-%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98-Permutation-Algorithm)
