<script setup>
import { computed, onMounted, ref } from "vue";
import HeroHeader from "./components/HeroHeader.vue";
import MovieGrid from "./components/MovieGrid.vue";
import MovieSearchForm from "./components/MovieSearchForm.vue";

const TMDB_BASE_URL = "https://api.themoviedb.org/3";
const TMDB_API_KEY = import.meta.env.VITE_TMDB_API_KEY;

const searchQuery = ref("");
const movies = ref([]);
const isLoading = ref(false);
const errorMessage = ref("");
const hasSearched = ref(false);

const pageTitle = computed(() =>
  hasSearched.value ? "검색 결과" : "현재 인기 영화"
);

async function requestMovies(endpoint, params = {}) {
  if (!TMDB_API_KEY) {
    errorMessage.value =
      "API 키가 없습니다. .env 파일에 VITE_TMDB_API_KEY를 설정해주세요.";
    movies.value = [];
    return;
  }

  const query = new URLSearchParams({
    api_key: TMDB_API_KEY,
    language: "ko-KR",
    ...params,
  });

  isLoading.value = true;
  errorMessage.value = "";

  try {
    const response = await fetch(`${TMDB_BASE_URL}${endpoint}?${query.toString()}`);
    if (!response.ok) {
      throw new Error("영화 정보를 불러오지 못했습니다.");
    }

    const data = await response.json();
    movies.value = Array.isArray(data.results) ? data.results : [];
  } catch (error) {
    errorMessage.value = error instanceof Error ? error.message : "알 수 없는 오류가 발생했습니다.";
    movies.value = [];
  } finally {
    isLoading.value = false;
  }
}

async function loadPopularMovies() {
  hasSearched.value = false;
  await requestMovies("/movie/popular");
}

async function searchMovies() {
  const keyword = searchQuery.value.trim();
  if (!keyword) {
    await loadPopularMovies();
    return;
  }

  hasSearched.value = true;
  await requestMovies("/search/movie", { query: keyword });
}

onMounted(loadPopularMovies);
</script>

<template>
  <div class="cinema-bg">
    <HeroHeader />

    <MovieSearchForm v-model:search-query="searchQuery" @search="searchMovies" />

    <p class="list-title">{{ pageTitle }}</p>

    <p v-if="isLoading" class="status-message">영화 목록을 불러오는 중...</p>
    <p v-else-if="errorMessage" class="status-message error">{{ errorMessage }}</p>
    <p v-else-if="movies.length === 0" class="status-message">표시할 영화가 없습니다.</p>

    <MovieGrid v-else :movies="movies" />
  </div>
</template>

<style scoped> 
.cinema-bg {
  min-height: 100vh;
  padding: 40px 24px 60px;
  color: #f6f6f6;
  background:
    radial-gradient(circle at top, rgba(180, 20, 40, 0.25), transparent 35%),
    linear-gradient(180deg, #0f0f16 0%, #161926 45%, #101218 100%);
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}

.list-title {
  max-width: 1100px;
  margin: 0 auto 14px;
  font-size: 1.1rem;
  font-weight: 700;
}

.status-message {
  max-width: 1100px;
  margin: 0 auto 20px;
  color: #c2c7df;
}

.status-message.error {
  color: #ff8e8e;
}

@media (max-width: 640px) {
  .cinema-bg {
    padding: 30px 14px 44px;
  }
}
</style>
