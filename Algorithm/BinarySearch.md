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

1. binarySearch 함수는 정렬된 배열 arr와 찾고자 하는 target 값을 매개변수로 받습니다.

2. left와 right 변수를 사용하여 탐색 범위는 left는 배열의 시작 인덱스이고 right는 배열의 끝 인덱스이다.

3. while 루프 내에서 mid를 계산하여 현재 탐색 범위의 중간 인덱스를 찾습니다.

4. if 문을 사용하여 mid 위치의 값이 target와 같은지 확인합니다. 같다면 mid 위치를 반환합니다.

5. else if 문을 사용하여 mid 위치의 값이 target보다 작은지 확인합니다. 그렇다면 left를 mid + 1로 설정하여 왼쪽 탐색 범위를 좁힙니다.

6. else 문을 사용하여 mid 위치의 값이 target보다 큰지 확인합니다. 그렇다면 right를 mid - 1로 설정하여 오른쪽 탐색 범위를 좁힙니다.

7. while 루프가 종료되면, target 값이 배열에 존재하지 않는 경우 -1을 반환합니다.
