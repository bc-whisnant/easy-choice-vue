<script setup>
  import Choice from './Choice.vue';

  defineProps({
    choices: {
      type: Array,
      required: true,
    }
  })

  const emit = defineEmits(['removeChoice'])

  const removeChoice = (index) => {
    emit('removeChoice', index)
  } 
</script>


<template>
  <div class="choices-list">
    <Choice v-for="(choice, index) in choices" :key="index" :choice="choice" @removeChoice="removeChoice(index)" />
  </div>
</template>

<style scoped>
  .choices-list {
    max-height: 40vh;
    margin-bottom: 24px;
    overflow-y: scroll;
  }

</style>  
