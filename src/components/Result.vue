<template>
  <div class="results">
    <p>Your results</p>
    <h1>{{ props.numberOfCorrect }}/{{ props.numberOfQuestions }}</h1>
  </div>
  <div class="link">
    <RouterLink to="/">Go Back</RouterLink>
  </div>
</template>

<script setup>
import { defineProps } from "vue";
import { RouterLink } from "vue-router";
const props = defineProps(["numberOfCorrect", "numberOfQuestions"]);
</script>

<style scoped>
.results {
  text-align: center;
  padding: 100px 0;
}

p {
  font-size: 25px;
}

h1 {
  font-size: 80px;
}

.link {
  text-align: center;
}
a {
  text-decoration: none;
  color: #000;
  font-size: 20px;
  font-weight: bold;
}
</style>
