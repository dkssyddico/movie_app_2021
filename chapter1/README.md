## Chapter 1

- React: 페이스북이 만듦. 요즘 회사들은 default로 리액트를 사용
- [create-react-app](https://github.com/facebook/create-react-app)

<br>

### Setting(# 1.1)

```sh
cd Documents
npx create-react-app 원하는 폴더명(movie_app_2021)
code .
```

- package.json: scripts에서 start, build 만 남기기
- 터미널에 npm start

<br>

### git 연결하기(# 1.2)

1. VSC를 실행시킨 폴더의 Terminal에 git init
2. Github에서 new repository 생성(되도록 같은 이름 사용, package.json의 name에 쓴 이름)
3. VSC Terminal에 git remote add origin + URL [https://github.com/dkssyddico/movie_app_2021](https://github.com/dkssyddico/movie_app_2021)
4. git add .
5. git commit -m "first commit"
6. git push origin master

<br>

### 리액트 동작(# 1.3)

- elements를 JS와 생성하고 HTML에 삽입
- div root 안에 elements를 밀어넣는다
- 모든 react applications을 div 사이에 밀어넣는다

```js
ReactDOM.render(<App />, document.getElementById('root'));

function App() {
  return <div className='App'>Hello</div>;
}
```

- react는 소스코드에 처음부터 HTML을 넣지 않고, HTML에서 HTML을 추가하거나 제거하는 법을 알고 있음
- **Virtual DOM**: 소스코드에는 보이지 않는 것.
