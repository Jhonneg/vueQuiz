<script>
import Questions from "./components/Questions.vue";
import Result from "./components/Result.vue";
import { questionsData } from "./data";
console.log(questionsData.questions);
export default {
  name: "App",
  components: {
    Questions,
    Result,
  },
  data() {
    const { questions, questionsAnswered, totalCorrect, results } =
      questionsData;
    return {
      questions,
      questionsAnswered,
      totalCorrect,
      results,
    };
  },
  methods: {
    questionAnswered(is_correct) {
      if (is_correct) {
        this.totalCorrect++;
      }
      this.questionsAnswered++;
    },
    reset() {
      this.questionAnswered = 0;
      this.totalCorrect = 0;
    },
  },
};
</script>

<template>
  <div class="ctr">
    <Questions
      v-if="questionsAnswered < questions.length"
      :questions="questions"
      :questionsAnswered="questionsAnswered"
      @question-answered="questionAnswered"
    />
    <Result v-else :results="results" :totalCorrect="totalCorrect" />
    <button
      @click.prevent="reset"
      type="button"
      class="reset-btn"
      v-if="this.questionAnswered === questions.length"
    >
      Reset
    </button>
  </div>
</template>
