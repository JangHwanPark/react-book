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

```