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
      this.questionsAnswered = 0;
      this.totalCorrect = 0;
    },
  },
};
</script>

<template>
  <div class="ctr">
    <Transition name="fade" mode="out-in">
      <Questions
        v-if="questionsAnswered < questions.length"
        :questions="questions"
        :questionsAnswered="questionsAnswered"
        @question-answered="questionAnswered"
      />
      <Result v-else :results="results" :totalCorrect="totalCorrect" />
    </Transition>
    <button
      @click.prevent="reset"
      type="button"
      class="reset-btn"
      v-if="questionsAnswered === questions.length"
    >
      Reset
    </button>
  </div>
</template>
