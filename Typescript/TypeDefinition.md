# TypeDefinition

TypeScript에서 타입을 정의하는 데 사용되는 두 가지 주요 방법 type과 interface에 대해 적어보려고 한다.

## type

유니온(Union), 인터섹션(Intersection), 매핑된 타입(Mapped Types), 튜플(Tuples), 그리고 복잡한 함수(Function) 타입 등을 정의

`type` 유연성과 복잡한 타입 정의에 적합하다.

## type union

여러 타입 중 하나를 가질 수 있는 타입

```
// Union 타입
type StringOrNumber = string | number;
```

## type intersection

```
type Person = {
  name: string;
  age: number;
};

type Employee = Person & {
  employeeId: number;
  department: string;
};

const employee: Employee = {
  name: "John Doe",
  age: 30,
  employeeId: 12345,
  department: "Engineering"
};
```

## type mapped type

기존에 정의되어 있는 타입을 새로운 타입으로 변환해 주는 문법

```
type StringNumberArray<T> = {
  [P in keyof T]: string;
};

type Person = {
  name: string;
  age: number;
};

type StringPerson = StringNumberArray<Person>;

```

## type tuples

튜플은 고정된 길이의 배열과 유사한 타입입니다. 튜플은 각 요소의 타입을 명시적으로 지정할 수 있으며, 요소의 순서도 중요합니다.

```
// Tuple 타입
type Coordinates = [number, number];
```

## interface

객체의 구조를 정의하는 데 사용이 되고 인터페이스를 확장할 수 있으며, 선언 병합(여러 곳에서 동일한 인터페이스)를 지원한다.

`interface`는 확장성과 선언 병합에 유리합니다

## interface 확장

```

interface Animal {
  name: string;
  sound: string;
}

interface Dog extends Animal {
  breed: string;
}

const myDog: Dog = {
  name: "Buddy",
  sound: "Woof!",
  breed: "Golden Retriever"
};
```

## interface 선언 병합

```
// File 1: person.ts
export interface Person {
  name: string;
  age: number;
}

// File 2: employee.ts
export interface Person {
  employeeId: number;
  department: string;
}

```

결론은 type과 interface는 각각의 장단점이 있고 개발자의 선호도에 따라 다르게 사용하는것 같다.
보통은 type은 복잡하거나 computed value를 쓸때 사용하고 interface는 선언 병합이 필요할 때 사용하는 것 같다.
