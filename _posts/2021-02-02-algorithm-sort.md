---
title:	"Algorithm - Sort"

tags: [C++, sort]
categories: algorithm
use_math: true

---
# 정렬 알고리즘(Sort)

> **기술면접**을 위해 기초 CS에 대한 복습중이다.
그 중 오늘은 **정렬 알고리즘, Sorting**에 관한 알고리즘에 대해 공부하고, 공부한 내용 중 요점이나 나중에 기억해야할 부분을 정리해보려고 한다.
내가 아는 부분은 생략되어 있을 수 있고, 혹여나 틀린 부분이 있을 수도 있으니 이 글을 보고 '다른 사람'이 공부하기에는 도움이 되지 않을 수 있으니 주의!

## 버블 정렬(Bubble Sort)
- 시간 복잡도: 정렬이 되어있든 아니든 $O(n^{2})$이다.
- 공간 복잡도: 주어진 배열 안에서 swap만 하기 때문에 $O(n)$이다.

## 선택 정렬(Selection Sort)
- 기본 알고리즘
	1. 처리되지 않은 데이터를 linear search로 가장 작은 숫자를 찾는다.
	2. 그 처리되지 않은 데이터 중 가장 앞쪽에 있는 숫자와 swap한다.
	3. 위의 1,2번을 반복   

- 시간 복잡도: 2중 loop를 사용하므로 $O(n^{2})$가 된다.
- 공간 복잡도: 주어진 배열 안에서 swap만 하기 때문에 $O(n)$이다.

## 삽입 정렬(Insertion Sort)
- 기본 알고리즘
	0. 첫 번째 숫자는 정렬되어있다고 가정한다.
	1. 처리되지 않은 데이터 중 가장 앞쪽에 있는 숫자가 비교대상이 될 것이고,
	2. 바로 왼쪽(앞쪽) 숫자와 비교한다. 더 작으면 왼쪽으로 옮기고(swap), 더 크면 그 자리에 둔다. 이걸 j>0까지 반복한다.
	3. 위의 1,2번을 반복

- 시간 복잡도: 2중 loop라서 마찬가지로 $O(n^{2})$가 된다.
	- 특징은 데이터가 거의 정렬이 되어있는 상태라면 매우 빠르게 동작
	- best case에는 $O(n)$이 된다.
- 공간 복잡도: 주어진 배열 안에서 swap만 하기 때문에 $O(n)$이다.

## 퀵 정렬(Quick Sort)
- 특징: 대부분 언어의 정렬 라이브러리의 근간이 될 정도로 일반적인 상황에서 가장 많이 사용된다.

- 기본 알고리즘
	1. pivot 값을 정한다. (보통 기본적으로 배울 땐 맨 앞의 숫자를 pivot으로 하는 알고리즘으로 배움)
	2. 맨 왼쪽부터 pivot보다 큰 값을 찾고, 맨 오른쪽부터는 pivot보다 작은 값을 찾는다.
	3. 찾으면 둘을 swap한다.
	4. 위의 2,3번을 반복한다. 그 다음 왼쪽부터, 그 다음 오른쪽부터 순차적으로 가운데로 오게 된다.
	5. 그러다 엇갈리게 되면 _swap_(둘 중 작은 숫자, pivot)한다. 그럼 pivot이 중간에 들어가서 **divide**가 된다.
	6. 이제 재귀적으로 1~5를 반복한다.   
	
- 시간 복잡도
	- 평균의 경우: 매번 절반에 가깝게 분할이 일어난다고 가정하면 $O(NlogN)$이 된다.
	- 최악의 경우: 이미 정렬된 배열이라면 분할이 이루어질 때마다 왼쪽은 없고 오른쪽만 그대로 있게 되기 때문에 $O(n^{2})$이 된다.
	- 그러나 **표준 라이브러리를 이용할 경우**, pivot을 선택할 때 최악의 경우가 나오지 않게끔 하도록 구현되어 있어서 worst case가 되지 않도록  **$O(NlogN)$을 보장**한다.
- 공간 복잡도: 주어진 배열 안에서 swap만 하기 때문에 $O(n)$이다.

## 계수 정렬(Count Sort)
- 특징: 데이터의 크기 범위가 제한되어 있을 때 사용하기 용이하며, 최댓값에 영향을 크게 받기 때문에 최악의 경우 메모리를 낭비하게 된다.
- 기본 알고리즘
	1. 카운트에 해당하는 배열을 MAX_VALUE 크기만큼 만든다. (전부 0으로 초기화)
	2. 각 데이터에 해당하는 인덱스의 값을 +1한다.
	3. 카운트 배열에 들어있는 숫자만큼 인덱스를 출력한다.

- 시간 복잡도: 데이터 개수만큼 _N_와 가장 큰 숫자 _K_만큼 실행되기 때문에 $O(N+K)$이다.
- 공간 복잡도: 데이터 개수만큼의 배열과 가장 큰 숫자만큼의 배열의 공간이 필요하기 때문에 $O(N+K)$이다.

## C++에서 표준라이브러리 Sort 사용
- C++ STL 제공 Sort 함수 사용 시 \<algorithm\> 헤더를 추가해야 한다.
- 사용 방법
	```
	// 1. begin 이상 end 미만 범위를 오름차순으로 정렬
	sort(begin, end);
	// 2. comp 함수 기준에 따라 정렬
	//    보통 a>b를 bool로 출력하여 내림차순하도록 구현
	sort(begin, end, comp);
	```
    - 세 번째 파라미터인 comp 자리에는 커스터마이징 코드를 만들어 넣을 수 있다.
    ```
    // return값이 true일 때 a와 b의 순서대로 정렬된다.
    bool comp(int a, int b) {
        string st1 = to_string(a) + to_string(b);
        string st2 = to_string(b) + to_string(a);
        return st1 > st2;
    }
    ```
    - 주의: Strick Weak Ordering을 따라야한다.
    ```
    bool compare(string a, string b) {
        string ab, ba;
        ab = a + b;
        ba = b + a;
        
        // 두 값이 같을 때에는 <, > 비교에 둘 다 false가 나와야 하는데
        // 그럴 수 있도록 구현해야한다. 아래와 같이 해주면 된다.
        // true, false를 직접 return하지 말고 비교해서 return하도록..
        return ab > ba;
    }
    ```
    
## 여러 기준으로 sort할 때
- 본 예시는 Sort first descending by score, then ascending by name을 조건으로 한다.
- 큰 조건, 즉 first 조건으로 먼저 큰 조건으로 하고, 다음 조건은 그 안에서 다루면 된다.  

    ```
    class Checker {
    public:
        // complete this method
        static int comparator(Player a, Player b) {
            if (a.score > b.score)
                return 1;
            else if (a.score == b.score) {
                if (a.name <= b.name)
                    return 1;
                else
                    return -1;
            }
            else {
                return -1;
            }

        }
    };

    bool compare(Player a, Player b) {
        if (Checker::comparator(a, b) == -1)
            return false;
        return true;
    }


    sort(players.begin(), players.end(), compare);
    ```