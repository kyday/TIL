# Event propagation

## 이벤트 버블링( Event Bubbling )

이벤트가 발생한 요소에서 시작하여 상위 요소로 이벤트가 전파되는 프로세스 (상위 -> 하위 요소로의 이벤트 전파 방식)

![과정1](https://blog.kakaocdn.net/dn/bbKdOb/btr8huzzeg5/rouzSgA8XIigc2LvXZzWXK/img.png)

예시 코드)

```
<div id="outer">
    Outer Div
    <div id="middle">
        Middle Div
        <div id="inner">
            Inner Div
        </div>
    </div>
</div>
```

```

Inner를 클릭했을때 자식에서 부모순으로 console.log가 출력된다.

마찬가지로 middle를 클릭하면 Middle Div clicked -> Outer Div clicked 순으로 출력이 된다.

document.getElementById('outer').addEventListener('click', function() {
    console.log('Outer Div clicked');
});

document.getElementById('middle').addEventListener('click', function() {
    console.log('Middle Div clicked');
});

document.getElementById('inner').addEventListener('click', function() {
    console.log('Inner Div clicked');
});
```

## 이벤트 캡쳐 ( Event Capture )

이벤트 버블링이랑은 반대로 상위에서 하위요소로 이벤트가 전파되는 프로세스 (상위 -> 하위 요소로의 이벤트 전파 방식)

![과정2](https://joshua1988.github.io/images/posts/web/javascript/event/event-capture.png)

```
<div id="outer">
    Outer Div
    <div id="middle">
         Middle Div
        <div id="inner">
            Inner Div
        </div>
    </div>


let divs = document.querySelectorAll('div');
function currentID(event) {
	console.log(event.currentTarget.id);
}

divs.forEach(function(div) {
	div.addEventListener('click', currentID, {
		capture: true
	});
});

```

## 이벤트 위임

상위 요소에 하나의 이벤트 리스너를 등록하여 모든 하위 요소의 이벤트를 처리

예시 )

```
const ButtonContainer = () => {
  const handleClick = (event) => {

    if (event.target.tagName === "BUTTON") {
      alert(event.target.textContent);
    }
  };

  return (
    <div onClick={handleClick}>
      <button>버튼 1</button>
      <button>버튼 2</button>
      <button>버튼 3</button>
    </div>
  );
};
```

## event.stopPropagation()

이벤트의 전파를 중지시키는 역할 / 이벤트의 전파를 제어할 수 있다.
