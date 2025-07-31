<script setup>


defineProps({
    movie:{
        type:Array,
        required:true
    }
})
</script>

<template>
    <div class="movie-card">
    <!-- OMDb sometimes returns 'N/A' for the poster. We should handle that.
         We can show a placeholder image if the poster is 'N/A'. -->
    <img 
      v-if="movie.Poster !== 'N/A'"
      :src="movie.Poster" 
      :alt="movie.Title" 
    />
    <div v-else class="placeholder-poster">
      No Image
    </div>
    
    <h3>{{ movie.Title }}</h3>
    <p>{{ movie.Year }}</p>
  </div>
</template>

<style scoped>
/* We are moving the styles for a single card here.
   This component is now fully self-contained. */
.movie-card {
  width: 200px;
  text-align: center;
  background-color: #f9f9f9;
  border-radius: 8px;
  box-shadow: 0 2px 8px rgba(0,0,0,0.1);
  overflow: hidden;
  transition: transform 0.2s ease;
}

.movie-card:hover {
  transform: translateY(-5px);
}

.movie-card img {
  width: 100%;
  height: 300px;
  object-fit: cover;
}

.placeholder-poster {
  width: 100%;
  height: 300px;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #e0e0e0;
  color: #888;
}

.movie-card h3 {
  margin: 10px 0;
  padding: 0 5px;
  font-size: 16px;
  height: 40px; /* Give a fixed height to prevent layout shifts */
}

.movie-card p {
  color: #666;
  margin-bottom: 10px;
}
</style>