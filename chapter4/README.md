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
