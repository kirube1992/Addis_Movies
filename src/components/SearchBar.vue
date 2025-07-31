<script setup>
import {ref} from 'vue';

const searchTerm = ref('');

const emit = defineEmits(['perform-search']);



function serach() {
  if(searchTerm.value.trim() !== ''){
     emit('perform-search', searchTerm.value);
  }
}

</script>
<template>
  <div class="search-bar">
<form @submit.prevent="serach">
  <input type="text" v-model="searchTerm" placeholder="write movie title ...."/>
  <button>Save</button>
</form>
</div>
</template>
<style scoped>

.search-bar {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 20px;
  gap: 10px;
}
.search-bar input {
  width: 300px;
  padding: 10px;
  font-size: 16px;
  border: 2px solid #ccc;
  border-radius: 8px;
}
.search-bar button {
  padding: 10px 20px;
  font-size: 16px;
  background-color: #42b883; /* Vue Green */
  color: white;
  border: none;
  border-radius: 8px;
  cursor: pointer;
}
.search-bar button:hover {
  background-color: #33a06f;
}

.search-btn{
    display: flex;
    margin: 5px;
}

.Move-input {
    padding:5px;
    margin: 5px;
}

.save-btn {
    padding:5px;
}

</style>