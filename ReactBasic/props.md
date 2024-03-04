## 프롭스(props)란?

`프롭스(props)`는 properties(속성)의 줄임말로 `어떤 데이터`를 `상위 컴포넌트`에서 `하위 컴포넌트`로 `전달`할 때 사용하는 리액트 문법이다. 

리액트는 `프롭스(props)`객체를 사용하여 부모 컴포넌트에서 자식 컴포넌트로 데이터 전달이 가능하지만, 자식 컴포넌트에서 부모 컴포넌트로 데이터를 전달할 수 없다.

`프롭스(props)`는 서버에서 전달받은 데이터뿐만 아니라, `기본 데이터(string, bool, number)`, `JSX(component)`, `객체`, `배열`, `함수` 등 모든 자바스크립트 값을 하위 컴포넌트로 전달할 수 있다.

<br>

## 프롭스를 이용해 하위 컴포넌트에 데이터 전달하기

아래는 부모 컴포넌트인 `App` 컴포넌트에서 하위컴포넌트인 `PropsPractice` 컴포넌트로 `name`, `developed`, `type`, `language`, `license` 데이터를 전달하여 렌더링하는 예제다.

### App.jsx
```javascript
import PropsPractice from "./components/PropsPractice/PropsPractice";

export default function App() {
    return (
        <div>
            <PropsPractice
                name={'리액트'}
                developed={'메타'}
                type={'라이브러리'}
                language={'자바스크립트'}
                license={'오픈소스'}
            />
        </div>
    );
}
```

### PropsPractice.jsx
```javascript
import React from 'react';

export default function PropsPractice({name, developed, type, language, license}) {
    return (
        <div>
            <h1>PropsPractice</h1>
            <p>이름 : {name}</p>
            <p>개발사 : {developed}</p>
            <p>유형 : {type}</p>
            <p>언어 : {language}</p>
            <p>라이선스 : {license}</p>
        </div>
    );
}
```

전달한 데이터는 자식 컴포넌트의 파라미터를 통해 전달받아 바인딩할 수 있다.

위 예제에서는 `데이터(props)`를 객체로 감싸서 함수의 파라미터로 전달받는다. 이 문법을 `비구조화 할당` 또는 `구조 분해`라고 부른다.

<br>

## defaultProps로 Props에 기본값 전달하기

부모 컴포넌트가 자식 컴포넌트에 props를 지정하지 않았을 때 `기본값을 설정`하여 사용할 수 있다. 이를 통해 필수 props를 지정하지 않아도 되는 편리함이 있다.

`defaultProps`를 설정하려면 `컴포넌트 명.defaultProps = { ... }`으로 객체 형식으로 설정하면 된다.

### App.jsx
```javascript
import DefaultPropsPractice from "./components/PropsPractice/DefaultPropsPractice";

export default function App() {
    return (
        <div>
            <DefaultPropsPractice name={'리액트'} developed={'메타'}/>
            <DefaultPropsPractice name={'리액트'}/>
            <DefaultPropsPractice/>
        </div>
    );
}
```

### DefaultPropsPractice.jsx
```javascript
import React from 'react';

export default function DefaultPropsPractice({ name, developed }) {
    return (
        <div>
            <h1>DefaultPropsPractice</h1>
            <p>이름 : {name}</p>
            <p>개발사 : {developed}</p>
        </div>
    );
}

DefaultPropsPractice.defaultProps = {
    name : 'Next.js',
    developed : 'Vercel'
}
```

첫 번째 `DefaultPropsPractice` 컴포넌트는 `name`과 `developed` props를 전달했기에 리액트, 메타가 출력되고,
두 번째 컴포넌트는 `name` props만 전달했기에 리액트와 `developed` 값은 `defaultProps`인 Vercel이 출력된다.
마지막 컴포넌트는 아무 컴포넌트도 전달되지 않았기 때문에 `defaultProps`인 Next.js와 Vercel이 출력된다.

<br>

## 스프레드 연산자를 이용해 프롭스 전달하기

반복되는 데이터를 여러 컴포넌트에 전달하고 싶을 때 `스프레드 연산자(...)`를 사용해 props를 전달할 수 있다.
이는 코드가 간결해지고 유지보수가 편해진다.

### App.jsx
```javascript
import PropsSpreadPractice from "./components/PropsPractice/PropsSpreadPractice";

export default function App() {
    const props = {
        name: 'Next.js',
        developed: 'Vercel',
        type: '프레임워크',
        language: '자바스크립트, TypeScript',
        license: '오픈소스',
    };

    return (
        <div>
            <PropsSpreadPractice {...props}/>
        </div>
    );
}
```

### PropsSpreadPractice.jsx
```javascript
import React from 'react';

export default function PropsSpreadPractice({name, developed, type, language, license}) {
    return (
        <div>
            <h1>PropsSpreadPractice</h1>
            <p>이름 : {name}</p>
            <p>개발사 : {developed}</p>
            <p>유형 : {type}</p>
            <p>언어 : {language}</p>
            <p>라이선스 : {license}</p>
        </div>
    );
}
```