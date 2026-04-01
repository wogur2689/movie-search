<template>
  <header class="hero">
    <p class="hero-tag">MOVIE SEARCH</p>
    <h1>무비 시어터</h1>
    <p class="hero-sub">보고 싶은 영화를 검색하고, 오늘의 영화를 찾아보세요.</p>
  </header>
</template>

<style scoped>
.hero {
  max-width: 900px;
  margin: 0 auto 28px;
  text-align: center;
}

.hero-tag {
  margin: 0;
  color: #ff8a80;
  letter-spacing: 4px;
  font-weight: 700;
  font-size: 0.78rem;
}

.hero h1 {
  margin: 8px 0 10px;
  font-size: clamp(2rem, 5vw, 3.4rem);
  text-shadow: 0 0 18px rgba(255, 98, 131, 0.35);
}

.hero-sub {
  margin: 0;
  color: #d6d8e4;
}
</style>
