<!-- Quiz.vue -->
<template>
  <p class="progress">Progress: {{ progress }} / {{ quizData.length }}</p>
  <div class="quiz-container">
    <h1 class="question-title">{{ quiz.question }}</h1>
    <ul class="options-list">
      <li
        v-for="(option, index) in quiz.options"
        :key="index"
        @click="checkAnswer(option)"
        :class="{
          selected: option === selectedAnswer,
          correct: option === quiz.correctAnswer && isCorrect,
          incorrect: option === selectedAnswer && !isCorrect,
        }"
      >
        {{ option }}
      </li>
    </ul>
    <button
      @click="nextQuestion"
      v-if="currentQuestionIndex < quizData.length - 1"
      class="next-btn"
    >
      Next Question
    </button>
    <button
      @click="resetQuestion"
      v-if="currentQuestionIndex <= quizData.length - 1"
      class="reset-btn"
    >
      Reset Quiz
    </button>
  </div>
</template>

<script>
export default {
  props: ["quizData"],
  data() {
    return {
      currentQuestionIndex: 0,
      selectedAnswer: null,
      showMessage: false,
      isCorrect: false,
      message: "",
      progress: 0,
    };
  },

  computed: {
    quiz() {
      return this.quizData[this.currentQuestionIndex];
    },
  },

  methods: {
    checkAnswer(answer) {
      if (this.selectedAnswer) return;
      this.selectedAnswer = answer;
      this.showMessage = true;
      if (answer === this.quiz.correctAnswer) {
        this.isCorrect = true;
        this.$swal.fire({
          title: "Jawaban anda benar",
          toast: true,
          timer: 2000,
          width: "20em",
          timerProgressBar: true,
          showConfirmButton: false,
          position: "top-end",
          icon: "success",
        });
        this.progress++;
        document
          .querySelector(".options-list li.selected")
          .classList.add("correct");
      } else {
        this.isCorrect = false;
        this.$swal.fire({
          title: "Jawaban anda salah",
          toast: true,
          timer: 2000,
          width: "20em",
          timerProgressBar: true,
          showConfirmButton: false,
          position: "top-end",
          icon: "error",
        });
        document
          .querySelector(".options-list li.selected")
          .classList.add("incorrect");
      }
    },

    nextQuestion() {
      this.selectedAnswer = null;
      this.showMessage = false;
      this.currentQuestionIndex++;
    },

    resetQuestion() {
      this.$swal.fire({
        title: "Mulai ulang quiz",
        timer: 2000,
        timerProgressBar: true,
        showConfirmButton: false,
        position: "center",
        icon: "info",
      });

      setTimeout(() => {
        this.currentQuestionIndex = 0;
        this.progress = 0;
        this.selectedAnswer = null;
        this.showMessage = false;
      }, 2000);
    },
  },
};
</script>
