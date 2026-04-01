# movie-search

Vue 3 + Vite 기반 영화 검색 사이트입니다.

## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur).

## Customize configuration

See [Vite Configuration Reference](https://vite.dev/config/).

## Project Setup

```sh
npm install
```

### TMDB API Key Setup

1. [TMDB](https://www.themoviedb.org/settings/api)에서 API 키를 발급받습니다.
2. 프로젝트 루트에서 `.env.example`을 복사해 `.env` 파일을 만듭니다.
3. `.env`에 키를 입력합니다.

```sh
VITE_TMDB_API_KEY=your_tmdb_api_key_here
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Compile and Minify for Production

```sh
npm run build
```
