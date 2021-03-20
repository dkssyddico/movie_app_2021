# Movie App 2021 🍎

> Make movie app with React

## 노마드코더 강의: ReactJS로 영화 웹 서비스 만들기

- Go to the course ! 👉 [Click Here](https://nomadcoders.co/react-fundamentals/lobby)

<br>

## Requirements

- node.js, npm, npx, git
- Theory part: HTML, CSS, Vanilla JS

<br>

## React 공식 문서

👉 [https://ko.reactjs.org/](https://ko.reactjs.org/)

## Chapter 1

- React: 페이스북이 만듦. 요즘 회사들은 default로 리액트를 사용
- [create-react-app](https://github.com/facebook/create-react-app)

<br>

### Setting

```sh
cd Documents
npx create-react-app 원하는 폴더명(movie_app_2021)
code .
```

- package.json: scripts에서 start, build 만 남기기
- 터미널에 npm start

<br>

### git 연결하기

1. VSC Terminal에 git init
2. Github에서 new repository 생성
3. VSC Terminal에 git remote add origin [https://github.com/dkssyddico/movie_app_2021](https://github.com/dkssyddico/movie_app_2021)
4. git add .
5. git commit -m "first commit"
6. git push origin master

<br>

### 리액트 동작

- elements를 JS와 생성하고 HTML에 삽입
- div root 안에 elements를 밀어넣는다
- 모든 react applications을 div 사이에 밀어넣는다

```js
ReactDOM.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>,
  document.getElementById('root')
);

function App() {
  return <div className='App'>Hello</div>;
}
```

- react는 소스코드에 처음부터 HTML을 넣지 않고, HTML에서 HTML을 추가하거나 제거하는 법을 알고 있음
- **Virtual DOM**

<br>

## Chapter 2

### Component

- **Component**: HTML을 반환하는 함수
- React는 component를 사용해서 HTML처럼 작성하는 경우에 필요
- **JSX**: HTML + JS. JS안의 HTML.
  - React에서만 있는 unique한 개념 !

<br>

- component 만드는 방법
- HTML을 반환하는 함수를 만들 때 함수명은 **대문자**로 만든다.

```jsx
import React from 'react'; // 꼭 써줘야 함

function Potato() {
  return <h3>I like potato</h3>;
}

export default Potato;
```

- react application이 하나의 component만을 rendering 할 수 있다.
- application 안에서 많은 component를 넣을 수 있다.
- component 안에 더 많은 component를 import 할 수 있다.
- JSX: component에 정보를 보낼 수 있다.
- 재사용 가능한 component를 만들 수 있다.

<br>

```jsx
import React from 'react';

function Food({ fav }) {
  return <h1>I like {fav} </h1>;
}

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

- props: 뭐든지 component에 넣게 되는 것
- props은 function의 argument로 감

<br>

### 웹사이트에 동적 데이터를 추가하는 방법

- [Array.prototype.map()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/map)

<br>

### [PropTypes](https://ko.reactjs.org/docs/typechecking-with-proptypes.html)

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
