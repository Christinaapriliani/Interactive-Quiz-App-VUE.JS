<template>
  <div>
    <p>You got {{ correctCount }} out of {{ totalQuestions }} correct!</p>
  </div>
</template>

<script>
export default {
  props: {
    correctCount: Number,
    totalQuestions: Number
  }
};
</script>
