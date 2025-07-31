<script setup>
import { ref } from 'vue';

import SearchBar from './components/SearchBar.vue';
import MovieList from './components/MovieList.vue';

const activeSearchTerm = ref('');
const isLoading = ref(false);
const error  = ref(null);
const movies = ref([]);


const apiKey = '2e3c68f2';

async function handleSearch(term) {
  // console.log('App.vue, received ', term);
  activeSearchTerm.value = term;

  isLoading.value = true;

  try {
     const apiUrl = `https://www.omdbapi.com/?apikey=${apiKey}&s=${term}`;
    const Response = await fetch(apiUrl);
    const data =  await Response.json();

    if(data.Response === "True") {
      movies.value = data.Search
    } else {
      error.value = data.Error;
    }

  }catch(err) {
     console.error("An error occurred during fetch:", err);
    error.value = 'An unexpected error occurred. Please try again.';
  } finally{
    isLoading.value = false;
  }


}
</script>

<template>
  <header>
    <h1>Vue Movie Finder</h1>
  </header>
  <main>

    <SearchBar @perform-search="handleSearch" />

    <div v-if="isLoading" class="feedBack">Loading...</div>
    <div v-else-if="error" class="feed error">{{ error }}</div>

    <MovieList v-else-if="movies.length > 0" :movies="movies" />

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