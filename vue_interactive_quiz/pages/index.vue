<template>
  <div>
    <h1>Interactive Quiz App</h1>
    <QuizQuestion
      :question="currentQuestion.question"
      :number="currentQuestionNumber"
    />
    <QuizOptions
      :options="currentQuestion.options"
      @selectOption="checkAnswer"
    />
    <QuizResult
      :correctCount="correctCount"
      :totalQuestions="totalQuestions"
      v-if="quizCompleted"
    />
  </div>
</template>

<script>
import QuizQuestion from '~/components/QuizQuestion.vue';
import QuizOptions from '~/components/QuizOptions.vue';
import QuizResult from '~/components/QuizResult.vue';

export default {
  components: {
    QuizQuestion,
    QuizOptions,
    QuizResult
  },
  data() {
    return {
      questions: [
        {
          question: 'What is the capital of France?',
          options: ['London', 'Berlin', 'Paris', 'Rome'],
          correctAnswer: 'Paris'
        },
        // Add more questions...
      ],
      currentQuestionNumber: 0,
      correctCount: 0,
      quizCompleted: false
    };
  },
  computed: {
    currentQuestion() {
      return this.questions[this.currentQuestionNumber];
    },
    totalQuestions() {
      return this.questions.length;
    }
  },
  methods: {
    checkAnswer(selectedOption) {
      if (selectedOption === this.currentQuestion.correctAnswer) {
        this.correctCount++;
      }
      if (this.currentQuestionNumber < this.questions.length - 1) {
        this.currentQuestionNumber++;
      } else {
        this.quizCompleted = true;
      }
    }
  }
};
</script>
