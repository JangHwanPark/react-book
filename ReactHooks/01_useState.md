## useState 란?

리액트 컴포넌트에서 변경되는 값은 변수대신 `useState`라는 `Hooks`을 사용하여 선언한다.

예를들어 어떤 이벤트가 발생했을 때 텍스트가 변경되거나 이미지 전환, 카운트가 증가되는 데이터 등을 `useState` 로 선언하여 관리한다.

이를 사용해 구현한 실제 예시가 좋아요 및 구독버튼, 캐러셀 슬라이드, 필터 버튼등이 있다.

<br>

`useState` 는 아래와 같이 선언 한다.
```javascript
const [state, setState] = useState(initialState);
```

`useState`는 `두 개의 값`을 `배열 구조분해`를 사용해 선언하고, `한 개`의 `매개변수`를 받는다.<br>
배열의 첫 번째 값인 `state`는 상태값을 의미하며 두 번째 값인 `setState`는 상태를 업데이트 하는 함수를 의미한다.<br>

`useState`의 `매개변수`에 전달되는`initialState(초기값)`은 `상태값(state)`을 초기화 한다.

<br>

## useState 를 이용해 변경되는 상태 관리하기
```javascript
import React, {useState} from 'react';

export default function UseStateBasic(props) {
    const [count, setCount] = useState(0);
    const handleClickCntUp = () => setCount(count + 1);
    const handleClickCntDown = () => setCount(count - 1);

    return (
        <div>
            <div>Count : {count}</div>
            <button onClick={handleClickCntUp}>Up</button>
            <button onClick={handleClickCntDown}>Down</button>
        </div>
    );
}
```
위 코드는 버튼을 클릭하면 숫자가 1씩 증가 또는 감소하는 예제다.

처음 count 라는 상태변수에 0을 할당한 뒤 클릭이벤트가 발생하면 setCount 에 의해 카운트가 1씩 증가 또는 감소한다.

> 참고<br>
> 리액트에서 이벤트를 설정할때는 태그 내부에 `onClick`, `onChange`와 같은 방법으로 설정하며 함수의 참조를 전달해야한다.<br>
> `onClick={실행할함수()`처럼 실행하면 렌더링되는 시점에 함수가 호출되기 때문에 이벤트가 동작하지않는등 오류가 발생할 수 있다.
> ```javascript
> <button onClick={실행할함수}>클릭<button/>
> <input type='text' onChange={실행할함수}/>
> ```

<br>

## 이전 상태값 관리하기
```javascript
import React, {useState} from 'react';

export default function UseStatePrev(props) {
    const [count, setCount] = useState(0);
    const handleSum = () => {
        setCount(count + 1);
        setCount(count + 2);
        setCount(count + 3);
        setCount(count + 4);
        setCount(count + 5);
    }

    const handlePrevSum = () => {
        setCount((prev) => prev + 1);
        setCount((prev) => prev + 2);
        setCount((prev) => prev + 3);
        setCount((prev) => prev + 4);
        setCount((prev) => prev + 5);
    }

    return (
        <div>
            <div>Count : {count}</div>
            <button onClick={handleSum}>handleSum</button>
            <button onClick={handlePrevSum}>handlePrevSum</button>
        </div>
    );
}
```