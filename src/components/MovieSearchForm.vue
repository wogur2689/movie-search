<script setup>
const searchQuery = defineModel("searchQuery", { type: String, default: "" });

defineEmits(["search"]);
</script>

<template>
  <form class="search-box" @submit.prevent="$emit('search')">
    <input
      v-model="searchQuery"
      type="text"
      placeholder="영화 제목을 입력하세요..."
    />
    <button type="submit">검색</button>
  </form>
</template>

<style scoped>
.search-box {
  max-width: 760px;
  margin: 0 auto 34px;
  display: grid;
  grid-template-columns: 1fr auto;
  gap: 10px;
}

.search-box input {
  padding: 14px 16px;
  border: 1px solid #3b3f56;
  border-radius: 10px;
  background: rgba(20, 22, 34, 0.85);
  color: #fff;
  outline: none;
}

.search-box input:focus {
  border-color: #ff5f7a;
  box-shadow: 0 0 0 3px rgba(255, 95, 122, 0.2);
}

.search-box button {
  padding: 0 22px;
  border: none;
  border-radius: 10px;
  background: linear-gradient(135deg, #ff4d6d, #ff7b54);
  color: #fff;
  font-weight: 700;
  cursor: pointer;
}

@media (max-width: 640px) {
  .search-box {
    grid-template-columns: 1fr;
  }

  .search-box button {
    height: 44px;
  }
}
</style>
