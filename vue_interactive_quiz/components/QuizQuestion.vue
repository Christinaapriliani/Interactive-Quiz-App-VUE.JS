<template>
  <div>
    <p>Question {{ number + 1 }}: {{ question }}</p>
  </div>
</template>

<script>
export default {
  props: {
    question: String,
    number: Number
  }
};
</script>
