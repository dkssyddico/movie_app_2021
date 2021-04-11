## Chapter 2

### Component

```jsx
ReactDOM.render(<App />, document.getElementById('root'));
//<App /> 가 Component!
```

- react는 모든 게 Component

- **Component**: HTML을 반환하는 함수 🔽

```jsx
import React from 'react';

function App() {
  return (
    <div>
      <h1>Hello</h1>
    </div>
  );
}
```

- HTML을 반환한 것

- React는 component를 사용해서 HTML처럼 작성하려는 경우에 필요
- **JSX**: HTML + JS. JS안의 HTML.
  - React에서만 있는 unique한 개념 !

<br>

### Component 만드는 방법

- HTML을 반환하는 함수를 만들 때 함수명은 **대문자**로 만든다.

```jsx
//potato.js

import React from 'react'; // 꼭 써줘야 함

function Potato() {
  return <h3>I like potato</h3>;
}

export default Potato;
// Potato를 export해야 다른 곳에서도 쓸 수 있다
```

**- react application이 하나의 component만을 rendering 할 수 있다.**

- 그래서 index.js에서는 App 만 쓰고, App.js 안에 Potato를 넣어준다.

```jsx
App.js;

import React from 'react';
import Potato from './Potato';

function App() {
  return (
    <div>
      <h1>Helllo</h1>
      <Potato />
    </div>
  );
}

export default App;
```

- App.js 안에서 많은 component를 넣을 수 있다.
- component 안에 더 많은 component를 import 할 수 있다.

<br>

### # 2.1

- JSX: component에 정보를 보낼 수 있다.
- 재사용 가능한 component를 만들 수 있다. component를 계속해서 반복해서 사용할 수 있음
- component에서 component로, children component로 정보 보내는 법을 배울 것임!

```jsx
import React from 'react';

function Food({ fav }) {
  return <h1>I like {fav} </h1>;
}
// props object 안에는 fav가 있다.
// { fav } 는 object(props)를 열어서 fav를 가져온다는 뜻

function App() {
  return (
    <div className='App'>
      <h1>Hello</h1> // Hello
      <Food fav='kimchi' /> // I like kimchi
      <Food fav='pizza' /> // I like pizza
      <Food fav='sushi' /> // I like sushi
      <Food fav='cake' /> // I like cake
      <Food fav='macaroon' /> // I like macaroon
    </div>
  );
}

export default App;
```

🔼 Food component에 kimchi, pizza라는 value로 prop(property) fav를 줬음

- App이 father, Food가 children
- props: 뭐든지 component에 넣게 되는 것
- props은 function의 argument로 감

<br>

### 웹사이트에 동적 데이터를 추가하는 방법(# 2.2)

- [Array.prototype.map()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/map)
  - array로부터 array를 줌
  - array의 각 item에서 function을 실행하는 array를 가지는 자스 함수. function의 결과를 갖는 array를 반환한다.

```jsx
import React from 'react';

function Food({ name }) {
  return <h1>I like { name } </h1>;
}

const foodILike = [{ name: 'kimchi' },{ name: 'sushi' },{ name: 'pasta' }]];

function App() {
  return (
    <div>
    {foodILike.map(dish => <Food name={dish.name} />)}
    </div>
  );
}


// dish는 object

export default App;
```

<br>

### # 2.3 map Recap

- 함수로 나눠주는 방법

```jsx
import React from 'react';

function Food({ name }) {
  return <h1>I like { name } </h1>;
}

const foodILike = [{ name: 'kimchi' },{ name: 'sushi' },{ name: 'pasta' }]];

function renderFood(dish){
  return <Food name={dish.name} />
}

function App() {
  return (
    <div>
    {foodILike.map(renderFood)}
    </div>
  );
}

export default App;
```

- 이렇게 하면 unique key prop 이 필요하다는 에러가 뜸
- 그래서 각각의 item이 다를 수 있도록 id를 꼭 넣어준다. id: 1 이렇게

<br>

- 오류가 해결되는 코드

```jsx
import React from 'react';

function Food({ name }) {
  return <h1>I like { name } </h1>;
}

const foodILike = [{ id:1, name: 'kimchi' },{ id:2, name: 'sushi' },{ id:3, name: 'pasta' }]];

function renderFood(dish){
  return <Food key={dish.id} name={dish.name} />
}

function App() {
  return (
    <div>
    {foodILike.map(renderFood)}
    </div>
  );
}

export default App;
```

- Tip : 시각장애인들을 위해서 img에는 alt를 넣어준다

<br>

### 2.3 Protection With Proptypes

#### [PropTypes](https://ko.reactjs.org/docs/typechecking-with-proptypes.html)

- 내가 전달받은 props가 내가 원하는 props인지를 확인해주는 것

- 제대로 된 prop을 보냈는지 확인시켜주는 것.

- 설치 방법

```sh
npm i prop-types
```

- 사용 사례

```jsx
Food.propTypes = {
  name: PropTypes.string.isRequired,
  picture: PropTypes.string.isRequired,
  rating: PropTypes.number,
};
```

- 실제로는 PropTypes라고 써야한다.

<br>
