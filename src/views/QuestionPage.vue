<script setup>
import { onMounted, ref } from 'vue'
import { useRoute } from 'vue-router'
import { shuffle } from 'lodash-es'

import useAPI from '@/composables/useAPI'
import useColor from '@/composables/useColors'
import TitleBar from '@/components/TitleBar.vue'
import NotificationAnswers from '@/components/NotificationAnswers.vue'
import useScore from '@/composables/useScore'
import DifficultyChip from '@/components/DifficultyChip.vue'
import router from '@/router'

const route = useRoute()
const colors = useColor()
const api = useAPI()
const question = ref(null)
const answers = ref([])
const isCorrect = ref(false)
const { changeScore } = useScore()
const handleAnswer = (points) => {
  isCorrect.value = points > 0
  showNotification.value = true
  setTimeout(() => {
    changeScore(points)
    router.push('/')
  }, 1000)
}
const showNotification = ref(false)

onMounted(async () => {
  question.value = await api.getQuestion(route.params.id)
  answers.value.push({
    id: answers.value.length,
    correct: true,
    answer: question.value.correct_answer,
    points: question.value.difficulty === 'easy' ? 10 : question.value.difficulty === 'medium' ? 20 : 30,
  })
  question.value.incorrect_answers.map((answer) => {
    answers.value.push({
      id: answers.value.length,
      correct: false,
      answer,
      points: -5,
    })
  })
  answers.value = shuffle(answers.value)
})
</script>
<template>
  <div v-if="question" class="question-container">
    <TitleBar> {{ question.category }}</TitleBar>

    <p class="question">{{ question.question }}</p>
    <div class="answers">
      <div
        v-for="answer in answers"
        :key="answer.id"
        :class="colors.getColor(answer.id)"
        class="answer"
        @click="handleAnswer(answer.points)"
      >
        {{ answer.answer }}
      </div>
    </div>
    <DifficultyChip :difficulty="question.difficulty" />
  </div>
  <div v-else class="loading">Loading...</div>
  <NotificationAnswers v-if="showNotification" :correct="isCorrect" />
</template>

<style lang="postcss" scoped>
.question-container {
  @apply flex h-full w-full flex-col items-center gap-8;

  & .question {
    @apply text-center text-4xl font-bold;
  }

  & .answers {
    @apply grid w-full flex-grow grid-cols-2 gap-8;

    & .answer {
      @apply flex items-center justify-center rounded-lg text-center text-3xl text-white;
      &:hover {
        @apply cursor-pointer;
      }
    }
  }
}

.loading {
  @apply flex h-full w-full items-center justify-center text-7xl;
}
</style>
