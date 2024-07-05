# ArrayMethod

## forEach

각 배열 요소에 대해 제공된 함수를 한 번씩 실행

```
const array1 = ['a', 'b', 'c'];

array1.forEach((element) => console.log(element));
```

## map

배열을 순회해서 처리한 새로운 배열을 반환

```
const array1 = [1, 4, 9, 16];

const map1 = array1.map((x) => x * 2);

console.log(map1);

```

## push

push() 메서드는 배열의 끝에 하나 이상의 요소를 추가하고, 배열의 새로운 길이를 반환합니다.

```
let fruits = ["Apple", "Mango"];

fruits.push("Cherry");

console.log(fruits); // ["Apple", "Mango", "Cherry"]

```

## pop

pop() 메서드는 배열에서 마지막 요소를 제거하고 그 요소를 반환합니다.

```
let fruits = ["Apple", "Mango", "Cherry"];

let lastFruit = fruits.pop();

console.log(lastFruit); // "Cherry"
```

## shift

배열에서 첫 번째 요소를 제거하고, 제거된 요소를 반환

```
const array1 = [1, 2, 3];

const firstElement = array1.shift();

console.log(array1);
// Expected output: Array [2, 3]

console.log(firstElement);
// Expected output: 1
```

## unshift

새로운 요소를 배열의 맨 앞쪽에 추가하고, 새로운 길이를 반환

```
const arr = [1, 2, 3];

// 배열 시작 부분에 하나의 요소를 추가합니다.
arr.unshift(4);

console.log(arr); // 출력: [4, 1, 2, 3]


// 배열 시작 부분에 여러 개의 요소를 추가합니다.
arr.unshift(5, 6, 7);

console.log(arr) // 출력: [5, 6, 7, 4, 1, 2, 3]
```

## indexOf

배열에서 주어진 요소를 찾을 수 있는 인덱스를 반환하거나 해당 요소가 없으면 -1을 반환합니다.
(배열에서 요소의 위치를 찾거나, 존재하는지 확인할 때 유용)

```
const fruits = ["Apple", "Banana"];

console.log(fruits.indexOf("Apple")); // 0

console.log(fruits.indexOf("Banana")); // 1

없으면 -1
```

## sort

배열 요소를 원하는 정렬 순서로 정렬한 후 그 배열을 반환

```

const enStrings = ["d", "b", "c", "a"];
enStrings.sort();

console.log(enStrings); // 출력: ["a", "b", "c", "d"]


const koStrings = ["다", "가", "나"];
koStrings.sort();

console.log(koStrings); // 출력: ["가", "나", "다"]

/* 오름차순 */

let numbers = [40, 100, 1, 5, 25, 10];
numbers.sort((a, b) => a - b);
console.log(numbers); // [1, 5, 10, 25, 40, 100]

/*  내림차순  */
const reverseNumbers = [1, 3, 2, 4, 5];
reverseNumbers.sort((a, b) => b - a);

console.log(reverseNumbers); // 출력: [5, 4, 3, 2, 1]
```

## join

배열의 각 요소를 지정된 구분자로 연결(join)하여 하나의 문자열로 반환

```
const elements = ['Fire', 'Air', 'Water'];

console.log(elements.join());
// Expected output: "Fire,Air,Water"

console.log(elements.join(''));
// Expected output: "FireAirWater"

console.log(elements.join('-'));
// Expected output: "Fire-Air-Water"
```
