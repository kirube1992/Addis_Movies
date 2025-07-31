<script setup>
import { ref } from 'vue';

import SearchBar from './components/SearchBar.vue';

const activeSearchTerm = ref('');

function handleSearch(term) {
  console.log('App.vue, recived ', term);
  activeSearchTerm.value = term;
}
</script>

<template>
  <header>
    <h1>Vue Movie Finder</h1>
  </header>
  <main>

    <SearchBar @perform-search="handleSearch" />

    <div v-if="activeSearchTerm" class="search-result-info">
      <p>Searching for: {{ activeSearchTerm }}</p>
    </div>
  </main>
</template>

<style scoped>
header {
  text-align: center;
  padding: 20px;
  background-color: #2c3e50;
  color: white;
}
.search-result-info {
  text-align: center;
  margin-top: 20px;
  font-size: 18px;
}
</style>