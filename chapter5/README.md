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
