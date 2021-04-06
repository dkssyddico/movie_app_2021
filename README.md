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

1. VSC를 실행시킨 폴더의 Terminal에 git init
2. Github에서 new repository 생성(되도록 같은 이름 사용, package.json의 name에 쓴 이름)
3. VSC Terminal에 git remote add origin + URL [https://github.com/dkssyddico/movie_app_2021](https://github.com/dkssyddico/movie_app_2021)
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

<br>

## Chapter 3

### State

- State는 동적 데이터와 함께 작업할 때 만들어짐.
- 변하는 데이터, 존재하지 않는 데이터, 사라지고 다시 생성되는, 변경된 데이터 = dynamic data
- state는 **object**이고 component의 데이터를 넣을 공간이 있고 **데이터는 변한당.**
- 데이터가 변하기 때문에 state를 이용해야 함
- 내가 바꿀 데이터는 state 안에 넣는다.
- 직접 state를 변경하지 말라고 함: react는 render function을 refresh하지 않을 것.
- state의 상태를 변경할 때 react가 render function을 호출해서 바꿔주길 원함

```jsx
class App extends React.Component {
  state = {
    count: 0,
  };
  add = () => {
    console.log('add');
  };
  minus = () => {
    console.log('minus');
  };
  render() {
    return (
      <div>
        <h1>The number is: {this.state.count}</h1>
        <button onClick={this.add}>Add</button>
        <button onClick={this.minus}>Minus</button>
      </div>
    );
  }
}
```

<br>

### setState

- state는 object. **setState**는 새로운 state를 받아야 함.
- setState를 사용하지 않으면 새 state와 함께 render function이 호출되지 않는다.
- 매 순간 setState를 호출할 때마다 react는 새로운 state와 함께 render function을 호출할 것.
- 🔽 아래와 같은 코드는 좋은 코드가 아니지만 react가 허락은 해줌

```jsx
add = () => {
  this.setState({ count: this.state.count + 1 });
};
```

- **current**로 만드는 방법 🔽
- state를 set할 때, react에서 외부의 상태에 의존하지 않는 가장 좋은 방법

```jsx
add = () => {
  this.setState((current) => ({ count: current.count + 1 }));
};
```

<br>

### **function component** : 함수를 수행하는 component

```jsx
function App() {
  return (
    <div className='App'>
      {foodILike.map((dish) => (
        <Food key={dish.id} name={dish.name} picture={dish.image} rating={dish.rating} />
      ))}
    </div>
  );
}
```

<br>

### **class component**

- 아기는 사람에서 확장되고, 사람의 특징을 가져올 수 있고 그 특징에서 확장됨
- cell phone class 에서 확장한 samsung class
- return을 가지지 않음. function이 아니라서.
- **render** method를 가짐

```jsx
class App extends React.Component {
  render() {
    return <h1>I am class Component</h1>;
  }
}
```

- function component는 function이고 무언가를 return하고 screen에 표시된다.
- class component는 class. react component로 부터 확장되고 screen에 표시, render method 실행해줘야 함!
- **react는 자동적으로 모든 class component의 render method를 실행하고자 함**

<br>

### Component - Life cycle

- life cycle method는 기본적으로 react가 component를 생성하는, 그리고 없애는 방법이다.

- **Mounting**

  - 태어나는 것과 같다
  - constructor()
  - render()
  - componentDidMount(): 이 component는 처음 render 됐어!
    - render()가 먼저 호출되고 그 다음이 componentDidMount()

```jsx
 componentDidMount() {
    console.log('component rendered');
  }
  render() {
    console.log("I'm rendering");}
//I'm rendering
//component rendered 순으로 뜸 !
```

- **Updating**

  - render()
  - componentDidUpdate()

- **Unmounting**
  - component가 죽는 것을 의미: 페이지를 바꿀 때. state를 사용해서 component를 교체할 때
  - componentWillUnmount()

<br>

### 호출 순서

```jsx
class App extends React.Component {
  constructor(props) {
    super(props);
    console.log('hello');
  }
  state = {
    count: 0,
  };
  add = () => {
    this.setState((current) => ({ count: current.count + 1 }));
  };
  minus = () => {
    this.setState((current) => ({ count: current.count - 1 }));
  };
  componentDidMount() {
    console.log('component rendered');
  }
  componentDidUpdate() {
    console.log("I'm just updated");
  }
  componentWillUnmount() {
    console.log('goodbye');
  }
  render() {
    console.log("I'm rendering");
    return (
      <div>
        <h1>The number is: {this.state.count}</h1>
        <button onClick={this.add}>Add</button>
        <button onClick={this.minus}>Minus</button>
      </div>
    );
  }
}

export default App;
```

1. render function
2. componentDidMount

- Add button 클릭, setState 호출

3. render function
4. componentDidUpdate
5. componentWillUnmount는 component가 떠날 때 호출

<br>

## Chapter 4

### Fetching Movies from API

- Data fetch
  - YTS API에서 영화 정보를 받아옴
  - Axios 이용

```jsx
getMovies = async () => {
  const movies = await axios.get('https://yts-proxy.nomadcoders1.now.sh/list_movies.json');
};
```

<br>

### async, await 쓰는 이유

- axios.get으로 데이터를 받아오는 게 느릴 수 있음
- 완전히 데이터를 받아오고 처리하기 위해서

<br>

### Invaild Dom property 'class' 오류

- 그냥 class는 자바스크립트의 `class` 라고 인식.
- class를 className으로
- HTML, CSS와 JS에서 같은 이름으로 다른 기능을 하는 것이 있다
  - ex: class, for → className, htmlFor

<br>

### summary 글자수 동등하게 해주는 방법

- string은 Array와 같다
- string.length: 길이 반환
- string.slice(start, end)
  - start: 추출 시작점
  - end: 추출 종료점

```jsx
<p className='movie__summary'>{summary.slice(0, 180)}...</p>
```

<br>

## Chapter 5

### Deploying to Github Pages

```
npm i gh-pages
```

- package.json에 homepage 추가

```
"homepage": "https://dkssyddico.github.io/movie_app_2021/"
```

- npm run build: 나에게 build 폴더를 줌
- 이 build 폴더를 gh-pages에 업로드한다.

- package.json scripts 추가

```
"deploy": "gh-pages -d build",
"predeploy": "npm run build"
```

- deploy는 기본적으로 predeploy를 불러온다
- npm run deploy를 하면 gh-pages에 업로드 완료.

<br>

1. gh-pages 설치
2. homepage 넣기
3. 내 깃허브 io 주소 넣기
4. deploy, predeploy 명령어 넣어서 실행 !

<br>

## Chapter 6

react-router-dom : 네비게이션을 만들어주는 패키지

Router는 무슨 페이지에 있을 때 어디로 가라고 해주는 것
ex) '/about' -> About.js
