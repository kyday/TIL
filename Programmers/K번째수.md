# K번째수

## 문제

배열 array의 i번째 숫자부터 j번째 숫자까지 자르고 정렬했을 때, k번째에 있는 수를 구하려 합니다.

예를 들어 array가 [1, 5, 2, 6, 3, 7, 4], i = 2, j = 5, k = 3이라면

array의 2번째부터 5번째까지 자르면 [5, 2, 6, 3]입니다.
1에서 나온 배열을 정렬하면 [2, 3, 5, 6]입니다.
2에서 나온 배열의 3번째 숫자는 5입니다.
배열 array, [i, j, k]를 원소로 가진 2차원 배열 commands가 매개변수로 주어질 때, commands의 모든 원소에 대해 앞서 설명한 연산을 적용했을 때 나온 결과를 배열에 담아 return 하도록 solution 함수를 작성해주세요.

나의 풀이

```
function solution(array, commands) {
    let answer = [];

    commands.forEach((item,index) => {
      let sliceItem = array.slice(item[0] - 1, item[1])
      sliceItem.sort((a,b) => a-b)
      answer.push(sliceItem[commands[index][2] - 1]);
    })

    return answer;
}
```

다른 사람 풀이

```
function solution(array, commands) {
    return commands.map(command => {
        const [sPosition, ePosition, position] = command
        const newArray = array
            .filter((value, fIndex) => fIndex >= sPosition - 1 && fIndex <= ePosition - 1)
            .sort((a,b) => a - b)

        return newArray[position - 1]
    })
}
```

#### 독백

프로그래머스 정렬에 있는 Lv1 문제를 풀었는데 생각보다 어려웠다.

풀고 나서 다른 사람 풀이를 보니..역시나 코딩테스트는 고수가 정말 많다.

나도 열심히 풀다보면 저렇게 짤 수 있으려나..?

이 문제에서는 배열에 index에 대한 지식과, slice를 잘 사용할 수 있나?

정렬을 할 수 있나? 이런것들을 보는 문제였던것 같다.
