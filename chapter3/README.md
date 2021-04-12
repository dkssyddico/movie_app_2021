## Chapter 3

### 3.0 Class Components and State

1. function component

```jsx
function App () {
  return ()
}
```

2. class component

<br>

#### Class component 만들기

- 매번 component를 만들 때마다 모든 것을 다 구현하고 싶지 안하서 extends from React.Component를 한다.

  - baby는 사람에서 확장되고 사람의 특징을 모두 가져올 수 있다.
  - samsung 이 cell phone에서 가져오는 것처럼

- class react component는 return을 가지고 있지 않다. function이 아니기 때문
- render 이런건 React.Component가 가지는 Method
- function component는 function이고 return을 함 class componet는 class로써 react component로 확장되고 스크린에 표시됨
  **- react는 자동적으로 모든 class component의 render method를 실행하고자 함**

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

#### State

- **class component가 가지는 state !**
- State는 동적 데이터와 함께 작업할 때 만들어짐.
- 변하는 데이터, 존재하지 않는 데이터, 사라지고 다시 생성되는, 변경된 데이터 = dynamic data
- state는 **object**이고 component의 데이터를 넣을 공간이 있고 **데이터는 변한당.**
- 데이터가 변하기 때문에 state를 이용해야 함
- state에 바꾸고 싶은 data를 넣는다

```jsx
class App extends React.Component {
  state = {
    count: 0,
  };
  render() {
    return <h1>The number is {this.state.counter}</h1>;
  }
}
```

<br>
- App에서 데이터를 어떻게 바꿀까?
  - 
  - 직접 state를 변경하지 말라고 함: react는 render function을 refresh하지 않을 것.
  - state의 상태를 변경할 때 react가 render function을 호출해서 바꿔주길 원함

```jsx
class App extends React.Component {
  state = {
    count: 0
  };
  add = () => {
    console.log("add");
  };
  minus = () => {
    console.log("minus");
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
```

- 그 외: function에 ()를 붙이면 바로 실행. 안붙이면 click 시 실행

<br>

### 3.1 All you need to know about State

state를 직접 변경하지 않는다!!

```jsx
add = () => {
  this.state.count = 1;
};
```

위와 같이 할 시, react는 render function을 refresh하지 않기 때문

- 매번 state의 상태를 변경할 때, react가 render function을 호출해서 바꿔주길 원함!

<br>

### setState가 왜 필요한가?

- setState function을 호출하면, react는 언제 우리가 setState를 호출할 지를 알고, 내가 view를 refresh하길 원하는 것을 알고 render function을 refresh하길 원한다.
- state는 object.
- **setState를 호출하면 react는 state를 refresh하고 render function을 호출함**
  - **setState를 사용하지 않으면 새 state와 함께 render function이 호출되지 않는다.**
  - 매 순간 setState를 호출할 때마다 react는 새로운 state와 함께 render function을 호출할 것.
- 🔽 아래와 같은 코드는 좋은 코드가 아니지만 react가 허락은 해줌

```jsx
add = () => {
  this.setState({ count: this.state.count + 1 });
};
```

- **current**로 만드는 방법 🔽
- react는 넘나 똑똑해서 현재 state를 가져오는 것을 허락해줌: **current**
- state를 set할 때, react에서 외부의 상태에 의존하지 않는 가장 좋은 방법

```jsx
add = () => {
  this.setState((current) => ({ count: current.count + 1 }));
};
// current가 현재 state인 것임.
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

### # 3.2 Component - Life cycle

- life cycle method는 기본적으로 **react가 component를 생성하고 없애는 방법이다.**

- **Mounting**

  - 태어나는 것과 같다
  - constructor() : JS에서 class를 만들 때 호출되는 것 - super()
  - render()
  - **componentDidMount()**: 이 component는 처음 render 됐어!
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

<br>

- **Updating**
  - update의 원인은 사용자: 버튼을 누르거나 그런거
  - render()
  - **componentDidUpdate()**

<br>

- **Unmounting**
  - component가 죽는 것을 의미: 페이지를 바꿀 때. state를 사용해서 component를 교체할 때
  - **componentWillUnmount()**

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

- Add button 클릭, setState 호출, render function 다시 호출ㄷ함

3. render function
4. componentDidUpdate
5. componentWillUnmount는 component가 떠날 때 호출

<br>
