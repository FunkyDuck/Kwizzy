<script setup lang="ts">
import { ref } from 'vue'

const isActive = ref(false)

const toggleMenu = () => {
  isActive.value = !isActive.value;
}
</script>

<template>
  <header class="header">
    <nav class="navbar">
      <div class="navbar-brand">
        <a class="header-logo" href="/">
          <img src="/ico-Kwizzy_64.png" />
        </a>

        <a
          role="button"
          class="navbar-burger"
          :class="{ 'is-active': isActive }"
          aria-label="menu"
          aria-expanded="false"
          data-target="navbar"
          @click="toggleMenu"
        >
          <span aria-hidden="true"></span>
          <span aria-hidden="true"></span>
          <span aria-hidden="true"></span>
          <span aria-hidden="true"></span>
        </a>
      </div>

      <div id="navbarBasic" class="navbar-menu" :class="{ 'is-active': isActive }">
        <ul class="navbar-start">
          <li class="navbar-item"><RouterLink to="/quizz">Quizz</RouterLink></li>
          <li class="navbar-item"><RouterLink to="/new-quizz">Create Quizz</RouterLink></li>
          <li class="navbar-item"><RouterLink to="/login">Login</RouterLink></li>
          <li class="navbar-item"><RouterLink to="/Account">Account</RouterLink></li>
          <li class="navbar-item"><RouterLink to="/logout">Logout</RouterLink></li>
        </ul>
      </div>
    </nav>
  </header>
</template>

<style scoped>
  ul {
    li {
      text-align: right;
      font-size: 1.25rem;
      font-weight: bold;
    }
  }
</style>
