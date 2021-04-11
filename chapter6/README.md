## Chapter 6

react-router-dom : 네비게이션을 만들어주는 패키지

Router는 무슨 페이지에 있을 때 어디로 가라고 해주는 것
ex) '/about' -> About.js

url을 가져다가 라우터가 컴포넌트를 불러오는 것임

```javascript
function App() {
  return (
    <Hashrouter>
      <Route path='/about' component={About} />
    </Hashrouter>
  );
}
```

Route 에는 props 2 렌더링할 스크린이 들어가고 다른 프롭은 뭘할지 정해짐 what url is going to do

<br>

```javascript
<HashRouter>
  <Route path='/'>
    <h1>Home</h1>
  </Route>
  <Route path='/about'>Abput</Route>
</HashRouter>
```

이렇게 하면 /about에서 Home과 About 겹치는 문제 발생. exact 써줘야 할 듯 or <></>

```javascript
<HashRouter>
  <Route path='/home'>
    <h1>Home</h1>
  </Route>
  <Route path='/home/introduction'>
    <h1>introduction</h1>
  </Route>
  <Route path='/about' exact>
    Abput
  </Route>
</HashRouter>
```

또 겹치는 문제 발생. introduction이 두 개의 라우터와 겹침. 같이 렌더링 됨.

<br>

### exact={true}

```javascript
<HashRouter>
  <Route path='/' exact={true} component={Home} />
  <Route path='/about' component={About} />
</HashRouter>
```

이렇게 하면 안겹쳐짐

<br>

### #6.2

네비게이션: home과 about을 서로 이동하게 만들어주는 것. 버튼을 만든다고 한다

href 속성을 쓰면 그냥 새로고침만 시켜버리고 원하는 페이지로 고정이 안된다.

-> Link를 쓰는 이유

### Link

```jsx
<Link to='/'>Home</Link>
<Link to='/about'>About</Link>
```

HTML의 a 태그, href 를 Link, to로 대체한다

router 밖에서 Link를 쓸 수 없다

## fragment

<></>

- 두 개를 동시에 렌더링하기 위해서

### github gh-pages

- HashRouter가 Browser Router보다 gh-page에 업로드 하기 쉽다

<br>

### props

props를 통해 정보를 전달하고 about에 정보를 실제로 그려준다

### #6.3

Link에서 to는 string과 object, function를 받을 수 있음

```jsx
<Link
  to={{
    pathname: '/courses',
    search: '?sort=name',
    hash: '#the-hash',
    state: { fromDashboard: true },
  }}
/>
```

```jsx
<Link
  to={{
    pathname: '/about',
    state: {
      fromNavigation: true,
    },
  }}
>
```

about page에 object를 보내는 것

### #6.4 Redirecting

render() => componentDidMount() 실행

- movie-detail 말고 movie/:id 형식으로 할 수도 있다.
