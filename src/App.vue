<script>
export default {
  name: "App",
  data() {
    return {
      questions: [
        {
          q: "In what year Vue came out?",
          answers: [
            { text: "2016", is_correct: false },
            { text: "2013", is_correct: false },
            { text: "2014", is_correct: true },
            { text: "2015", is_correct: false },
          ],
        },
        {
          q: "In what year Javascript came out?",
          answers: [
            { text: "1994", is_correct: false },
            { text: "1995", is_correct: true },
            { text: "1998", is_correct: false },
            { text: "1996", is_correct: false },
          ],
        },
        {
          q: "What is Nuxt?",
          answers: [
            {
              text: "A framework for vue for building fullstack applications.",
              is_correct: true,
            },
            {
              text: "A component library.",
              is_correct: false,
            },
            {
              text: "A database integration library for Vue3",
              is_correct: false,
            },
          ],
        },
      ],
      results: [
        {
          min: 0,
          max: 2,
          title: "Try again!",
          desc: "Do a little more studying and you may succeed!",
        },
        {
          min: 3,
          max: 3,
          title: "Wow, you're a genius!",
          desc: "Studying has definitely paid off for you!",
        },
      ],
    };
  },
};
</script>

<template>
  <div class="ctr">
    <button type="button" class="reset-btn">Reset</button>
  </div>
</template>

<style scoped></style>
