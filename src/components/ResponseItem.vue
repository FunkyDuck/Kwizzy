<script setup lang="ts">
  const props = defineProps({
    userAnswer: String || Number || Boolean || null,
    answer: String,
  })
</script>

<template>
  <section v-if="userAnswer === answer" class="has-background-success has-text-dark">
    Bravo, la bonne réponse était : <b>{{ answer }}</b>.
  </section>

  <section v-else class="has-background-danger has-text-dark">
    Faux, <b>{{ userAnswer }}</b> est une mauvaise réponse.<br>
    la bonne réponse était : <b>{{ answer }}</b>.
  </section>
</template>

<style scoped>
  section {
    margin: 1dvh 0;
    padding: 1dvh 1dvw;
    border-radius: 8px;
  }
</style>
