# BinarySearch

이진탐색(BinarySearch)은 가장 기본적인 탐색 알고리즘이다.

배열의 중간 값을 선택하여 찾고자 하는 값과 비교하고, 그 값이 중간 값보다 작은 경우에는 중간 값을 기준으로 왼쪽의 데이터를 대상으로,

큰 경우에는 오른쪽의 데이터를 대상으로 탐색을 한다. 중간 값이 찾고자 하는 값과 같을 때까지 반복을 하고 찾고자 하는 값이 배열에 존재하지 않을 경우에는 -1을 반환한다.

\*\* 이진 탐색의 시간 복잡도는 평균적으로 O(log n)

```
function binarySearch(arr, target) {
    let left = 0;
    let right = arr.length - 1;

    while (left <= right) {
        const mid = Math.floor((left + right) / 2);

        if (arr[mid] === target) {
            return mid;
        } else if (arr[mid] < target) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }

    return -1;
}



```
