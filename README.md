# Movie App 2021 🍎

> Make movie app with React

## 노마드코더 강의: ReactJS로 영화 웹 서비스 만들기

- Go to the course ! 👉 [Click Here](https://nomadcoders.co/react-fundamentals/lobby)

<br>

## Requirements

- node.js, npm, npx, git
- Theory part: HTML, CSS, Vanilla JS

<br>

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
