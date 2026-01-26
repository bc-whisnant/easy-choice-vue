<script setup>
  import { ref } from 'vue';
  import Heading from './components/Heading.vue';
  import ChoiceEntry from './components/ChoiceEntry.vue';
  import ChoiceContainer from './components/ChoiceContainer.vue';
  import Button from './components/Button.vue';
  import Result from './components/Result.vue';
  const choices = ref([]) // ['Pizza', 'Testing', '123']
  const buttonIcon = '🎲'
  const currentChoice = ref('')
  const easyChoice = ref('')

  const addChoice = () => {
    choices.value.push(currentChoice.value)
    currentChoice.value = ''
  } 
  const removeChoice = (index) => {
    choices.value.splice(index, 1)
  }

  const pickChoice = () => {
    easyChoice.value = choices.value[Math.floor(Math.random() * choices.value.length)]
  } 

</script>

<template>
  <header>

    <div class="wrapper">
      <Heading text="Easy Choice" subtext="Can't decide? Let us choose!" />
    </div>
  </header>

  <main>
    <ChoiceEntry @addChoice="addChoice" v-model="currentChoice" :disabled="!currentChoice" placeholder="Add a choice..." />
    <ChoiceContainer @removeChoice="removeChoice" :choices="choices" />
    <div class="actions">
      <Button @pickChoice="pickChoice" :buttonIcon="buttonIcon" buttonText="Pick A Choice"/>
      <Result v-if="easyChoice && choices.length" :result="easyChoice" />
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

</style>
