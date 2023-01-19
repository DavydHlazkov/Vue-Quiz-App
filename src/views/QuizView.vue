<template>
  <div>
    <QuizHeader
      :questionStatus="questionStatus"
      :barPercentage="barPercentage"
    />

    <div>
      <Question
        v-if="currentQuestionId < quiz.questions.length"
        :question="quiz.questions[currentQuestionId]"
        @selectOption="onOptionSelected"
      />
      <Results
        v-else
        :numberOfCorrect="numberOfCorrect"
        :numberOfQuestions="quiz.questions.length"
      />
    </div>
  </div>
</template>

<script setup>
import Question from "../components/Question.vue";
import QuizHeader from "../components/QuizHeader.vue";
import Results from "../components/Result.vue";
import { useRoute } from "vue-router";
import { ref, computed } from "vue";
import quizes from "../data/data.json";

const route = useRoute();
const quizId = parseInt(route.params.id);
const currentQuestionId = ref(0);
const quiz = quizes.find((q) => q.id === quizId);

const questionStatus = computed(
  () => `${currentQuestionId.value} / ${quiz.questions.length}`
);

const barPercentage = computed(
  () => `${(currentQuestionId.value / quiz.questions.length) * 100}%`
);
const numberOfCorrect = ref(0);

const onOptionSelected = (isCorrect) => {
  if (isCorrect) {
    numberOfCorrect.value++;
  }
  currentQuestionId.value++;
};
</script>

<style scoped></style>
