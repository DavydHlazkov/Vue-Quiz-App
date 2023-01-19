<template>
  <div>
    <header>
      <h1>Quizes</h1>
      <input type="text" placeholder="search..." v-model.trim="search" />
    </header>
    <div class="options-container">
      <Card v-for="quiz in allQuizes" :key="quiz.id" :quiz="quiz" />
    </div>
  </div>
</template>

<script setup>
import Card from "../components/Card.vue";
import quizes from "../data/data.json";

import { ref, watch } from "vue";
const allQuizes = ref(quizes);
const search = ref("");

watch(search, () => {
  allQuizes.value = quizes.filter((quiz) =>
    quiz.name.toLowerCase().includes(search.value.toLowerCase())
  );
});
</script>

<style scoped>
header {
  margin-bottom: 10px;
  margin-top: 30px;
  display: flex;
  align-items: center;
}

header h1 {
  font-weight: bold;
  margin-right: 30px;
}

header input {
  border: none;
  background-color: rgba(128, 128, 128, 0.1);
  padding: 10px;
  border-radius: 5px;
}

.options-container {
  display: flex;
  flex-wrap: wrap;
  margin-top: 40px;
}
</style>
