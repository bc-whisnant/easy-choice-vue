<script setup>
import { ref, computed } from 'vue';
import Heading from './components/Heading.vue';
import ChoiceEntry from './components/ChoiceEntry.vue';
import ChoiceContainer from './components/ChoiceContainer.vue';
import NumberOfAttempts from './components/NumberOfAttempts.vue';
import Button from './components/Button.vue';
import Result from './components/Result.vue';
const choices = ref([]) // ['Pizza', 'Testing', '123']
const buttonIcon = '🎲'
const currentChoice = ref('')
const easyChoice = ref('')
const allChoicesRemoved = ref(false)
const numberOfAttemptsLabel = 'Number of Attempts'
const numberOfAttempts = ref(0)
const currentAttempt = ref(0)
const choiceCounts = ref({})
const finalChoiceRevealed = ref(false)

const isDuplicateChoice = computed(() => {
  const choice = currentChoice.value.trim().toLowerCase()
  return choices.value.some((existing) => existing.toLowerCase() === choice)
})

const addChoice = () => {
  const choice = currentChoice.value.trim()
  if (choice && !isDuplicateChoice.value) {
    choices.value.push(choice)
  }
  currentChoice.value = ''
  allChoicesRemoved.value = false
}
const removeChoice = (index) => {
  choices.value.splice(index, 1)
  choiceCounts.value = {}
  finalChoiceRevealed.value = false
  currentAttempt.value = 0
  numberOfAttempts.value = 0
  if (!choices.value.length) {
    allChoicesRemoved.value = true
    easyChoice.value = ''
  }
}

const mostFrequentChoice = () => {
  let winner = choices.value[0]
  choices.value.forEach((choice) => {
    if ((choiceCounts.value[choice] || 0) > (choiceCounts.value[winner] || 0)) {
      winner = choice
    }
  })
  return winner
}

const pickChoice = () => {
  const choice = choices.value[Math.floor(Math.random() * choices.value.length)]
  choiceCounts.value[choice] = (choiceCounts.value[choice] || 0) + 1
  currentAttempt.value++
  easyChoice.value = choice

  if (currentAttempt.value === numberOfAttempts.value) {
    setTimeout(() => {
      easyChoice.value = mostFrequentChoice()
      finalChoiceRevealed.value = true
    }, 900)
  }
}

const choiceReset = () => {
  choices.value = []
  choiceCounts.value = {}
  finalChoiceRevealed.value = false
  currentChoice.value = ''
  easyChoice.value = ''
  allChoicesRemoved.value = false
  numberOfAttempts.value = 0
  currentAttempt.value = 0
}

const decreaseNumberOfAttempts = () => {
  numberOfAttempts.value--
}

const increaseNumberOfAttempts = () => {
  numberOfAttempts.value++
}

const attemptsExhausted = computed(() => {
  return currentAttempt.value > 0 && currentAttempt.value === numberOfAttempts.value
})

const resultLabel = computed(() => {
  return finalChoiceRevealed.value ? 'Final choice:' : 'Current result:'
})

const buttonLabel = computed(() => {
  return finalChoiceRevealed.value ? 'Reset' : 'Pick A Choice'
})


</script>

<template>
  <header>
    <div class="wrapper">
      <Heading text="Easy Choice" subtext="Can't decide? Let us choose!" />
    </div>
  </header>

  <main>
    <ChoiceEntry @addChoice="addChoice" v-model="currentChoice" :disabled="currentChoice.trim() === '' || isDuplicateChoice"
      placeholder="Add a choice..." />
    <ChoiceContainer @removeChoice="removeChoice" :choices="choices" />
    <div class="actions">
      <NumberOfAttempts v-if="choices.length" :label="numberOfAttemptsLabel" :disabled="attemptsExhausted" :numberOfAttempts="numberOfAttempts" @decreaseNumberOfAttempts="decreaseNumberOfAttempts" @increaseNumberOfAttempts="increaseNumberOfAttempts" />
      <Button @pickChoice="pickChoice" @choiceReset="choiceReset" :resetState="finalChoiceRevealed" :buttonIcon="buttonIcon" :disabled="!choices.length || !numberOfAttempts || (attemptsExhausted && !finalChoiceRevealed)"
        :buttonText="buttonLabel" />
      <p class="attempts-progress" v-if="choices.length && currentAttempt > 0">Attempt {{ currentAttempt }} of {{ numberOfAttempts }}</p>
      <Result v-if="easyChoice && choices.length" :resultLabel="resultLabel" :result="easyChoice" />
    </div>
  </main>
</template>

<style scoped>
header .wrapper {
  display: flex;
  flex-direction: column;
  padding: 20% 0 10% 0;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
}

main {
  flex: 1;
  background: linear-gradient(180deg, #f3f0ff 0%, #ffffff 100%);
  padding: 24px;
  overflow-y: auto;
  display: flex;
  flex-direction: column;
  height: 75vh;
}

.actions {
  margin-top: auto;
}

.attempts-progress {
  font-size: 12px;
  color: #888;
  font-weight: 600;
  text-align: center;
  margin-bottom: 8px;
}
</style>
