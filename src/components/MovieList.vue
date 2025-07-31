<script setup>

import {ref} from 'vue';



defineProps({
    Movies: {
        type: Array,
        required: true
    }
}
)


</script>
<template>

      <div class="movie-list">
 
    <div v-for="movie in movies" :key="movie.imdbID" class="movie-card">
 
      <img :src="movie.Poster" :alt="movie.Title" />
      <h3>{{ movie.Title }}</h3>
      <p>{{ movie.Year }}</p>
    </div>
  </div>
</template>

<style scoped>
.movie-list {
  display: flex;
  flex-wrap: wrap; /* Allows items to wrap onto the next line */
  justify-content: center;
  gap: 20px;
  padding: 20px;
}
.movie-card {
  width: 200px;
  text-align: center;
  background-color: #f9f9f9;
  border-radius: 8px;
  box-shadow: 0 2px 8px rgba(0,0,0,0.1);
  overflow: hidden; /* Ensures the image respects the border-radius */
}
.movie-card img {
  width: 100%;
  height: 300px;
  object-fit: cover; /* Ensures the image covers the area without distortion */
}
.movie-card h3 {
  margin: 10px 0;
  padding: 0 5px;
  font-size: 16px;
}
.movie-card p {
  color: #666;
  margin-bottom: 10px;
}
</style>