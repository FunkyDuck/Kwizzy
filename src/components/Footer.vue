<script setup lang="ts">
const startYear = 2025
const endYear = new Date().getFullYear()

const strYears = endYear === startYear ? startYear : startYear + '-' + endYear
</script>

<template>
  <footer>
    <p>Kwizzy by <a href="https://funkyduck.be">FunkyDuck</a> © {{ strYears }}</p>

    <ul>
      <li><RouterLink to="/about">À Propos</RouterLink></li>
      <li><RouterLink to="/cgu">CGU</RouterLink></li>
      <li><RouterLink to="/legal">Mentions Légales</RouterLink></li>
      <li>Github</li>
    </ul>
  </footer>
</template>

<style scoped></style>
