# Key

## React에서 Key가 필요한 이유?

React는 key를 사용하여 리스트의 각 아이템을 고유하게 식별하는 역할을 하는데,

이를 통해 리스트의 아이템이 추가, 삭제, 이동되거나 순서가 변경되었을 때, React는 변경된 아이템만을 찾아 업데이트할 수 있습니다.

```
const users = [
  { id: 1, name: 'Alice' },
  { id: 2, name: 'Bob' },
  //...
];
const userListItems = users.map((user) =>
  <li key={user.id}>{user.name}</li>
);
```

## `key`를 사용하지 않으면 어떤 문제가 발생할까?

React는 리스트의 아이템을 고유하게 식별할 수 없으므로, 리스트의 아이템이 추가, 삭제, 이동되거나 순서가 변경되었을 때, 모든 아이템을 새로 렌더링을 하게 된다.

이는 `불필요한 렌더링`과 `성능 저하`가 일어날 수 있다.

## `key`를 index로 사용하면 위험한 이유?

인덱스는 배열의 순서가 변경될 때마다 변경될 수 있으므로, key로 사용하면 React가 각 아이템을 고유하게 식별하는 데 문제가 발생할 수 있습니다.

상태를 관리하는 컴포넌트에서 인덱스를 key로 사용하면, 배열의 순서가 변경될 때마다 컴포넌트의 상태가 예상치 못한 방식으로 초기화되거나 변경될 수 있습니다.
