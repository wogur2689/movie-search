<script setup>
const props = defineProps({
  movie: {
    type: Object,
    required: true,
  },
});

const TMDB_IMAGE_BASE_URL = "https://image.tmdb.org/t/p/w500";

function getPosterUrl(path) {
  return path ? `${TMDB_IMAGE_BASE_URL}${path}` : "";
}

function formatMeta(movie) {
  const score = typeof movie.vote_average === "number" ? movie.vote_average.toFixed(1) : "-";
  const year = movie.release_date ? movie.release_date.slice(0, 4) : "미정";
  return `평점 ${score} · ${year}`;
}
</script>

<template>
  <article class="movie-card">
    <img
      v-if="getPosterUrl(props.movie.poster_path)"
      class="poster-image"
      :src="getPosterUrl(props.movie.poster_path)"
      :alt="props.movie.title"
      loading="lazy"
    />
    <div v-else class="poster">NO POSTER</div>
    <div class="info">
      <h3>{{ props.movie.title }}</h3>
      <p>{{ formatMeta(props.movie) }}</p>
    </div>
  </article>
</template>

<style scoped>
.movie-card {
  border: 1px solid #2e3348;
  border-radius: 14px;
  overflow: hidden;
  background: rgba(19, 22, 33, 0.9);
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}

.movie-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 10px 24px rgba(0, 0, 0, 0.35);
}

.poster {
  aspect-ratio: 2 / 3;
  display: grid;
  place-items: center;
  background:
    linear-gradient(160deg, rgba(255, 98, 131, 0.22), rgba(84, 82, 206, 0.12)),
    #202438;
  color: #aeb4d0;
  font-weight: 700;
  letter-spacing: 1px;
}

.poster-image {
  width: 100%;
  aspect-ratio: 2 / 3;
  object-fit: cover;
  display: block;
}

.info {
  padding: 12px;
}

.info h3 {
  margin: 0 0 4px;
  font-size: 1rem;
}

.info p {
  margin: 0;
  color: #9ea3bc;
  font-size: 0.9rem;
}
</style>
