<template>
  <header>
    <h4>Question {{ props.questionStatus }}</h4>
    <div class="bar">
      <div :style="{ width: props.barPercentage }" class="completion"></div>
    </div>
  </header>
</template>

<script setup>
import { defineProps } from "vue";
const props = defineProps(["questionStatus", "barPercentage"]);
</script>

<style scoped>
header {
  margin-top: 20px;
}

header h4 {
  font-size: 30px;
}

.bar {
  width: 300px;
  height: 50px;
  border: 3px solid bisque;
}

.completion {
  height: 100%;
  width: 0%;
  background-color: bisque;
}
</style>
