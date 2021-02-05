---
title:	"Binary Search"

tags: Algorithm
use_math: true

---
# 이진탐색: Binary Search

> **기술면접**을 위해 기초 CS에 대한 복습중이다.
공부한 내용 중 요점이나 나중에 기억해야할 부분을 정리해보려고 한다.
내가 아는 부분은 생략되어 있을 수 있고, 혹여나 틀린 부분이 있을 수도 있으니 이 글을 보고 '다른 사람'이 공부하기에는 도움이 되지 않을 수 있으니 주의!

## 이진탐색
- 정렬되어 있는 리스트에서 절반씩 좁혀가며 탐색한다.
- 시작점, 끝점, 중간점을 이용한다.
- 시간 복잡도: $O(logN)$
```
// 이진 탐색 소스코드 구현(반복문)
int binarySearch(vector<int>& arr, int target, int start, int end) {
    while (start <= end) {
        int mid = (start + end) / 2;
        // 찾은 경우 중간점 인덱스 반환
        if (arr[mid] == target) return mid;
        // 중간점의 값보다 찾고자 하는 값이 작은 경우 왼쪽 확인
        else if (arr[mid] > target) end = mid - 1;
        // 중간점의 값보다 찾고자 하는 값이 큰 경우 오른쪽 확인
        else start = mid + 1;
    }
    return -1;
}
```

## 파라메트릭 서치 (Parametric Search)
- 최적화 문제를 결정문제(Y or N)로 바꾸어 해결하는 기법
- 이진 탐색을 이용하여 해결할 수 있다.

## 기타 필요한 C++ STL
- vector::iterator는 포인터처럼 요소들의 위치와 연관된 동작을 하는 객체
	```
	vector<int> v;
	vector<int>::iterator itr;
	//itr을 v의 시작위치를 갖게 선언
	itr = v.begin();
	```
- lower_bound, upper_bound는 vector에서 해당 위치를 리턴한다.

	```
	// v = {10 10 10 20 20 20 30 30}
	low = std::lower_bound (v.begin(), v.end(), 20);  // 3
	up = std::upper_bound (v.begin(), v.end(), 20);  // 6
	```
- lower_bound는 x보다 작지 않은 최초의 숫자의 iterator를 반환한다. 예를 들어 lower_bound(13)이면 맨 앞쪽 20 (네 번째 원소)의 iterator가 반환된다.

- upper_bound는 x보다 큰 최초의 숫자의 iterator를 반환한다. 예를 들어 upper_bound(13)이면 마찬가지로 맨 앞쪽 20 (네 번째 원소)의 iterator가 반환된다.

---

**참고한 사이트**
- 나동빈님 유튜브: [이코테 2021 강의](https://www.youtube.com/watch?v=94RC-DsGMLo)
- 나동빈님 Github: [이코테 소스코드 저장소](https://github.com/ndb796/python-for-coding-test)