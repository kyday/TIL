# Copy

## 얕은 복사(Shallow copy)

- 객체의 첫 번째 레벨만 복사하는 과정이다 -> 첫 번째 레벨의 속성에 대해 복사하기 때문에 서로 다른 값을 부여할 수 있다.

- 중첩된 구조는 원본 객체와 복사된 객체가 같은 메모리 주소를 공유하게 된다.

## 얕은 복사 방법

- `전개 구문`,
- `Array.prototype.concat()`,
- `Array.prototype.slice()`,
- `Array.from()`,
- `Object.assign()`,
- `Object.create()`

```
let zoo = {
  name: "Amazing Zoo",
  location: "Melbourne, Australia",
  animals: [
    {
      species: "Lion",
      favoriteTreat: "🥩",
    },
    {
      species: "Panda",
      favoriteTreat: "🎋",
    },
  ],
};
let shallowCopyZoo = {...zoo };

첫번째 레벨
shallowCopyZoo.name = "Super Amazing Zoo";
console.log(zoo.name); // "Amazing Zoo"
console.log(shallowCopyZoo.name); // "Super Amazing Zoo"

두번째 레벨
shallowCopyZoo.animals[0].species = "😙";
console.log(zoo.animals[0].species ); // "😙"
console.log(shallowCopyZoo.animals[0].species ); // "😙"

```

## 깊은 복사(Deep copy)

객체나 배열을 복제할 때 원본 데이터와 복제된 데이터가 서로 독립적인 데이터를 복사한다.

원본 데이터를 변경해도 복제된 데이터에 영향을 주지 않으며, 반대로 복제된 데이터를 변경해도 원본 데이터에는 영향을 주지 않는다는 특징

### 깊은 복사 방법

- `JSON.parse()`, `JSON.stringify()`

- `lodash - cloneDeep()`

- `재귀함수`

```
const originalObj = { a: 1, b: { c: 2 } };
const deepCopy = JSON.parse(JSON.stringify(originalObj));
```

참조 ) https://developer.mozilla.org/ko/docs/Glossary/Shallow_copy
