<script setup>
  import Heading from './components/Heading.vue';
  import ChoiceEntry from './components/ChoiceEntry.vue';
  import ChoiceContainer from './components/ChoiceContainer.vue';
  import Button from './components/Button.vue';
  import Result from './components/Result.vue';
  const choices = ['Pizza', 'Testing', '123']
  const buttonIcon = '🎲'
  const easyChoice = 'Pizza'
</script>

<template>
  <header>

    <div class="wrapper">
      <Heading text="Easy Choice" subtext="Can't decide? Let us choose!" />
    </div>
  </header>

  <main>
    <ChoiceEntry placeholder="Add a choice..." />
    <ChoiceContainer :choices="choices" />
    <Button :buttonIcon="buttonIcon" buttonText="Pick A Choice"/>
    <Result :result="easyChoice" />
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
  }

</style>
