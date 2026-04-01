<script setup>
import MovieCard from "./MovieCard.vue";

defineProps({
  movies: {
    type: Array,
    default: () => [],
  },
});
</script>

<template>
  <section class="movie-grid">
    <MovieCard v-for="movie in movies" :key="movie.id" :movie="movie" />
  </section>
</template>

<style scoped>
.movie-grid {
  max-width: 1100px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(170px, 1fr));
  gap: 16px;
}
</style>
