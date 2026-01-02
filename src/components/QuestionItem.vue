<script setup lang="ts">
import { type Ref, ref, watch, type PropType } from 'vue'
import ResponseItem from '@/components/ResponseItem.vue'

const props = defineProps({
  question: String,
  answer: [String, Number, Boolean] as PropType<string | number | boolean>,
  choices: {
    type: Array as PropType<(string | number | boolean)[]>,
    default: () => [],
  },
})

const emits = defineEmits<{
  (e: 'answered', value: boolean): void
}>()

const userAnswer = ref<string | number | boolean | undefined>(undefined)
const hasAnswered: Ref<boolean> = ref(false)

watch(
  () => props.question,
  () => {
    userAnswer.value = undefined
    hasAnswered.value = false
  },
)

function setAnswer(c: string | number | boolean) {
  userAnswer.value = c
  hasAnswered.value = true
}

function nextQuestion() {
  emits('answered', userAnswer.value === props.answer)
}
</script>

<template>
  <section>
    <p>{{ question }}</p>
  </section>

  <section>
    <p>Réponses :</p>

    <div v-if="typeof answer === 'string'">
      <button
        class="button is-info"
        :disabled="hasAnswered"
        v-for="c of choices"
        :key="c as any"
        @click="setAnswer(c as any)"
      >
        {{ c }}
      </button>
    </div>

    <div v-else-if="typeof answer === 'number'">
      <input type="number" :disabled="hasAnswered" v-model.number="userAnswer" />
      <button class="button is-info" @click="setAnswer(userAnswer)" :disabled="hasAnswered">
        Valider
      </button>
    </div>

    <div v-else-if="typeof answer === 'boolean'">
      <button class="button is-info" @click="setAnswer(true)" :disabled="hasAnswered">Vrai</button>
      <button class="button is-info" @click="setAnswer(false)" :disabled="hasAnswered">Faux</button>
    </div>
  </section>

  <section v-if="hasAnswered">
    <ResponseItem :userAnswer="userAnswer" :answer="answer" />
    <button @click="nextQuestion()" class="button is-primary">Question suivante</button>
  </section>
</template>

<style scoped>
section:first-of-type {
  margin-bottom: 1.5rem;
  background: rgba(255, 255, 255, 0.04);
  padding: 1rem 1.25rem;
  border-radius: 12px;

  p {
    font-size: 1.4rem;
    font-weight: 600;
    line-height: 1.4;
  }
}

section {
  div {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
    gap: 1rem;

    button {
      width: 100%;
      white-space: normal;
      word-break: break-word;
      text-align: center;
      min-height: 3rem;
    }
  }
}
</style>
